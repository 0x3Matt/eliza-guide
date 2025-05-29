# 🧠 ARIA Knowledge Implementation & Eliza Knowledge System Guide

## 📚 Table of Contents
1. [Current ARIA Implementation](#current-aria-implementation)
2. [Overview of Eliza Knowledge Management](#overview)
3. [Knowledge System Architecture](#architecture)
4. [Adding Knowledge to Agents](#adding-knowledge)
5. [Knowledge Directory Structure](#directory-structure)
6. [Supported File Types](#supported-files)
7. [Knowledge Modes](#knowledge-modes)
8. [How Knowledge Processing Works](#processing)
9. [Best Practices & Potential Improvements for ARIA](#best-practices)
10. [Relevant Links](#links)

## ✨ Current ARIA Implementation

The ARIA agent (`eliza/characters/aria-info/aria.character.json`) is currently configured to utilize Eliza's Retrieval-Augmented Generation (RAG) knowledge system.

### Configuration Snippet (`aria.character.json`)

```json
{
    "name": "ARIA",
    // ... other character properties ...
    "settings": {
        // ... other settings ...
        "ragKnowledge": true // RAG system is enabled
    },
    "topics": [
       // ... other topics ...
        "MetaMetaClub" // Topic related to the knowledge file added
    ],
    // ... other character properties ...
    "knowledge": [
        // Defines the knowledge sources for RAG
        { "path": "test-knowledge.md", "shared": false } 
    ]
}
```

### Explanation

1.  **RAG Enabled**: The `"ragKnowledge": true` setting activates the advanced knowledge processing system.
2.  **Knowledge Source**: The agent uses a single knowledge file defined by `"path": "test-knowledge.md"`.
3.  **File Location**: This file (`test-knowledge.md`) is located in the standard knowledge directory: `eliza/characters/knowledge/`. Paths are relative to this root.
4.  **Content**: The `test-knowledge.md` file currently contains information about **MetaMetaClub**, allowing ARIA to answer questions on this topic based on the provided text.
5.  **Shared Status**: `"shared": false` indicates this knowledge is specific to the ARIA agent and not shared with other agents using the same knowledge base (if applicable in the deployment).
6.  **Topic**: The "MetaMetaClub" topic was added to reflect the agent's new knowledge domain.

This setup allows ARIA to leverage the content within `test-knowledge.md` to answer user queries accurately about MetaMetaClub, as demonstrated in the successful test interactions.

## 🌟 Overview of Eliza Knowledge Management

Eliza's Knowledge Management system is a powerful Retrieval-Augmented Generation (RAG) feature that enables agents to process, store, and retrieve information from various sources. This allows agents to provide contextually relevant responses by leveraging stored knowledge during conversations, going beyond their base training data.

### 🎯 Key Features
- Multiple knowledge source types (files, directories, strings)
- Advanced semantic search via embeddings
- Context-aware retrieval based on conversation
- Efficient storage and indexing of knowledge chunks
- Support for `.md`, `.txt`, and `.pdf` file types
- Configurable knowledge modes (Classic vs. RAG)

## 🏗️ Knowledge System Architecture

The RAG system integrates external knowledge sources into the agent's response generation process.

```mermaid
graph LR
    A[User Query] --> B{Agent Runtime};
    B --> C[Embedding Generation];
    C --> D{Vector Database};
    E[Knowledge Sources
(.md, .txt, .pdf)] --> F[Preprocessing & Chunking];
    F --> G[Embedding Generation];
    G --> D;
    D -- Semantic Search --> H[Relevant Knowledge Chunks];
    B --> I{LLM};
    H --> I;
    A --> I;
    I --> J[Generated Response];
```

### 📂 Knowledge Item Structure (Internal)
```typescript
interface RAGKnowledgeItem {
  id: UUID; // Unique ID for the chunk/document
  content: {
    text: string; // The actual text chunk
    metadata?: any; // Source file, chunk index, etc.
  };
  embedding?: number[]; // Vector representation
  timestamp: Date;
  agentId: UUID; // Agent associated with this knowledge
  isShared: boolean; // If the knowledge is shared
}
```

## 🧩 Adding Knowledge to Agents

ElizaOS provides multiple ways to add knowledge to agents:

### 1. Via Character Definition (Current ARIA Method)

The simplest approach is defining knowledge directly in the character's `.json` configuration file. This is how ARIA is currently set up.

```json
{
  "name": "My Agent",
  // ... other properties ...
  "settings": {
    "ragKnowledge": true // MUST be true to use file/directory knowledge
  },
  "knowledge": [
    // Direct string knowledge (added to context if ragKnowledge: false, processed by RAG if true)
    "Important Fact: ElizaOS supports multiple knowledge formats.",

    // Single file reference (processed by RAG)
    { "path": "specific-topic.md", "shared": false },

    // Directory reference (all supported files within processed by RAG)
    { "directory": "product-manuals/", "shared": true }
  ]
}
```

### 2. Programmatically Before Runtime Initialization

You can dynamically load knowledge content using custom scripts before creating the agent runtime.

```typescript
// Example: Load all markdown files from a docs folder
import fs from 'fs';
import path from 'path';

function loadDocumentation(directoryPath: string): string[] {
  // Function to recursively get files (implementation not shown)
  const files = getFilesRecursively(directoryPath, ['.md']); 
  return files.map((filePath) => {
    const relativePath = path.relative(process.cwd(), filePath); // Or your base path
    const content = fs.readFileSync(filePath, 'utf-8');
    // You might structure this differently, perhaps returning objects
    return `Path: ${relativePath}

${content}`; 
  });
}

const docKnowledge = loadDocumentation('./docs');

// Then, in your runtime creation code:
const characterConfig = { /* ... load your character config ... */ };
characterConfig.knowledge = [
    ...(characterConfig.knowledge || []), // Keep existing knowledge
    ...docKowledge // Add dynamically loaded strings
]; 

// const runtime = await createRuntime({ character: characterConfig, ... });
```

### 3. Adding Knowledge After Runtime Creation

Knowledge can be added programmatically *after* the runtime is initialized, often used in plugins or dynamic systems.

```typescript
// Import needed utilities from @elizaos/core
import { createUniqueUuid } from '@elizaos/core'; 

async function addKnowledgeItem(runtime: IAgentRuntime, textContent: string, identifier: string) {
  const knowledgeItem = {
    // Generate a deterministic ID based on an identifier
    id: createUniqueUuid(runtime, identifier), 
    content: {
      text: textContent,
    },
    // You might add isShared, agentId etc. depending on implementation needs
  };

  // Add to runtime with default chunking/embedding settings
  await runtime.ragKnowledgeManager.addKnowledge(knowledgeItem); 

  // Or add with custom processing settings (if supported by method)
  // await runtime.addKnowledge(knowledgeItem, {
  //   targetTokens: 1500, 
  //   overlap: 100,      
  //   modelContextSize: 8192, 
  // });
}

// Example usage:
// await addKnowledgeItem(runtime, "New important fact...", "fact-001"); 
```

## 📁 Knowledge Directory Structure

Eliza expects knowledge files referenced by `path` or `directory` in the character configuration to reside within a specific root directory.

- **Default Root**: `eliza/characters/knowledge/`
- **Structure Inside Root**:
    ```
    characters/
    └── knowledge/          # Root knowledge directory established in runtime.ts
        ├── test-knowledge.md # File referenced by ARIA { "path": "test-knowledge.md" }
        ├── shared/         # Optional: For logically grouping shared items
        │   └── common-procedures.txt 
        └── agent-specific/ # Optional: For agent-specific organization
            └── product-specs.pdf 
    ```
- **References**: Paths in `knowledge` array (`"path": "..."`, `"directory": "..."`) are relative to this `knowledge/` root.

## 📄 Supported File Types

When using the RAG system (`"ragKnowledge": true`), Eliza can process the following file types referenced via `path` or `directory`:

- PDF files (`.pdf`)
- Markdown files (`.md`)
- Text files (`.txt`)

## ⚙️ Knowledge Modes

Eliza supports two primary modes for handling the `knowledge` array in the character file:

### 1. Classic Mode (Default)
- **Setting**: `"ragKnowledge": false` (or omitted)
- **Behavior**:
    - Only processes **direct string** entries in the `knowledge` array.
    - These strings are typically added directly to the agent's context/prompt.
    - File (`path`) and directory (`directory`) entries are **ignored**.
    - No chunking, embedding, or semantic search is performed on this knowledge.
- **Use Case**: Simple, static facts or instructions for the agent.

### 2. RAG Mode (Used by ARIA)
- **Setting**: `"ragKnowledge": true`
- **Behavior**:
    - Enables advanced knowledge processing.
    - Processes **all** knowledge types: strings, files (`path`), and directories (`directory`).
    - Content is read, preprocessed, chunked, and embedded.
    - Stored in a vector database for semantic retrieval.
    - Retrieved chunks are added to the agent's context dynamically based on the user query.
- **Use Case**: Integrating large documents, external knowledge bases, enabling semantic search over content.

## 🔄 How Knowledge Processing Works (RAG Mode)

### 1. Document Processing Flow
The RAG system processes documents referenced in the `knowledge` array (when `ragKnowledge: true`) during agent initialization:

1.  **Discovery**: Scans `knowledge` array for `path` and `directory` entries. Resolves paths relative to the `knowledgeRoot` (`characters/knowledge/`).
2.  **File Reading**: Reads content from supported file types (`.md`, `.txt`, `.pdf`). PDF requires specific service/library integration.
3.  **Preprocessing**: Cleans and normalizes the text content (e.g., removing markdown syntax, extra whitespace).
4.  **Chunking**: Splits the preprocessed text into smaller, manageable chunks (default size ~512 tokens). Overlap between chunks is maintained to preserve context.
5.  **Embedding**: Generates vector embeddings for each chunk using the configured embedding model.
6.  **Storage**: Stores the chunks and their embeddings in the vector database associated with the agent (or shared space if `shared: true`).

### 2. Retrieval Process
When the agent receives a user message:

1.  **Query Embedding**: The user's message (and potentially recent conversation history) is embedded.
2.  **Semantic Search**: The query embedding is compared against the embeddings of the stored knowledge chunks in the vector database.
3.  **Chunk Retrieval**: The most semantically similar chunks (based on a similarity threshold, e.g., 0.85) are retrieved.
4.  **Context Injection**: The text content of these retrieved chunks is added to the context provided to the Large Language Model (LLM) along with the user query and prompt.
5.  **Response Generation**: The LLM generates a response using the original query and the augmented context containing the retrieved knowledge.

### 3. Processing Parameters (Defaults)
- **Chunk Size**: ~512 tokens
- **Chunk Overlap**: ~20 tokens
- **Similarity Threshold**: 0.85
- **Match Count**: 5-8 results typically retrieved

## 💡 Best Practices & Potential Improvements for ARIA

Based on the Eliza documentation and general RAG best practices, here's how ARIA's knowledge usage could be improved:

### 1. Content Organization (Inside `test-knowledge.md`)
- **Use Clear Headings**: Continue using markdown headings (`##`, `###`) to structure the content logically. This aids readability and can potentially help retrieval focus.
- **Atomic Information**: Break down complex ideas into smaller paragraphs or sections. Each chunk ideally focuses on a specific sub-topic.
- **General to Specific**: Structure the document from general overview (`## About MetaMetaClub`) to specific details (`## Key Features`, `## Membership Benefits`).

### 2. File Management
- **Descriptive Filenames**: `test-knowledge.md` is okay for testing, but for production, use more descriptive names like `metametaclub-platform-info.md`.
- **Multiple Files**: If knowledge grows significantly, split it into multiple, focused files (e.g., `metametaclub-features.md`, `metametaclub-membership.md`). Update the `knowledge` array in `aria.character.json` accordingly:
    ```json
    "knowledge": [
        { "path": "metametaclub-platform-info.md", "shared": false },
        { "path": "metametaclub-features.md", "shared": false },
        { "path": "metametaclub-membership.md", "shared": false }
    ]
    ```
- **Use Directories**: For larger collections of related documents, use the `directory` reference:
    ```json
    "knowledge": [
        { "directory": "metametaclub/", "shared": false } 
        // This would process all .md, .txt, .pdf in characters/knowledge/metametaclub/
    ]
    ```

### 3. Knowledge Optimization
- **Focused Content**: Ensure each knowledge file/section is focused. Avoid mixing unrelated topics heavily within a single document if possible.
- **Review Chunking**: While default chunking works well, if retrieval misses obvious information, it *might* be due to how content is split. Rephrasing or restructuring the source document can help. (Advanced: Custom chunking settings via programmatic `addKnowledge`).
- **Regular Updates**: Keep the knowledge files (`.md` content) up-to-date with the latest information about MetaMetaClub. The agent only knows what's in the files.

### 4. Expand Knowledge Sources
- Add more `.md` files covering other topics relevant to ARIA (e.g., details about Arttention Media services, specific AI concepts).
- Consider converting existing documentation (if available in `.txt` or `.pdf`) and adding them via `path` or `directory` references.

## 🔗 Relevant Links

-   **Eliza Knowledge Management Docs**: [https://eliza.how/docs/core/knowledge](https://eliza.how/docs/core/knowledge)
-   **Eliza Memory Management Docs** (Related Concepts): [https://eliza.how/docs/guides/memory-management](https://eliza.how/docs/guides/memory-management) (Link from original prompt context)

---
*This guide documents the knowledge implementation for the ARIA agent as of [Current Date] and provides general guidance based on the Eliza framework.* 