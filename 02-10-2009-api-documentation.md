# 🌐 Eliza Market Scanner API Documentation

## 📚 Table of Contents
1. [Overview](#overview)
2. [Authentication](#authentication)
3. [Core APIs](#core-apis)
4. [Plugin APIs](#plugin-apis)
5. [Integration APIs](#integration-apis)
6. [WebSocket APIs](#websocket-apis)
7. [Error Handling](#error-handling)
8. [Rate Limiting](#rate-limiting)
9. [Examples](#examples)

## 🌟 Overview

The Eliza Market Scanner provides a comprehensive set of APIs for market data analysis, trading automation, and system integration. This documentation covers all available endpoints, authentication methods, and usage patterns.

### 🎯 API Versions
- Current Version: v1
- Beta Version: v2-beta
- Legacy Support: v0 (deprecated)

### 📡 Base URLs
```typescript
const API_ENDPOINTS = {
  production: 'https://api.eliza-scanner.com/v1',
  staging: 'https://staging-api.eliza-scanner.com/v1',
  development: 'https://dev-api.eliza-scanner.com/v1'
};
```

## 🔒 Authentication

### 1. API Key Authentication
```typescript
interface APIKeyAuth {
  type: 'apiKey';
  key: string;
  permissions: string[];
}

// Example Request
const headers = {
  'Authorization': 'Bearer YOUR_API_KEY',
  'Content-Type': 'application/json'
};
```

### 2. OAuth2 Authentication
```typescript
interface OAuth2Config {
  clientId: string;
  clientSecret: string;
  scopes: string[];
  redirectUri: string;
}

// OAuth2 Flow
async function getAccessToken(config: OAuth2Config): Promise<string> {
  const tokenResponse = await oauth2.getToken({
    code: authorizationCode,
    clientId: config.clientId,
    clientSecret: config.clientSecret,
    redirectUri: config.redirectUri
  });
  return tokenResponse.access_token;
}
```

## 🔄 Core APIs

### 1. Market Data API
```typescript
interface MarketDataAPI {
  endpoints: {
    // Get current market data
    '/market/current': {
      method: 'GET';
      params: {
        symbol: string;
        interval?: string;
      };
      response: MarketData;
    };
    
    // Get historical data
    '/market/history': {
      method: 'GET';
      params: {
        symbol: string;
        startTime: number;
        endTime: number;
        interval: string;
      };
      response: MarketDataHistory;
    };
    
    // Get market indicators
    '/market/indicators': {
      method: 'GET';
      params: {
        symbol: string;
        indicators: string[];
        interval?: string;
      };
      response: IndicatorData;
    };
  };
}

// Example Response
interface MarketData {
  symbol: string;
  price: number;
  volume: number;
  timestamp: number;
  indicators?: {
    rsi?: number;
    macd?: {
      value: number;
      signal: number;
      histogram: number;
    };
  };
}
```

### 2. Trading API
```typescript
interface TradingAPI {
  endpoints: {
    // Place new order
    '/trading/order': {
      method: 'POST';
      body: {
        symbol: string;
        side: 'buy' | 'sell';
        type: 'market' | 'limit';
        quantity: number;
        price?: number;
      };
      response: OrderResponse;
    };
    
    // Get order status
    '/trading/order/:orderId': {
      method: 'GET';
      params: {
        orderId: string;
      };
      response: OrderStatus;
    };
    
    // Cancel order
    '/trading/order/:orderId': {
      method: 'DELETE';
      params: {
        orderId: string;
      };
      response: CancellationResponse;
    };
  };
}

// Example Usage
async function placeOrder(order: Order): Promise<OrderResponse> {
  return await api.post('/trading/order', order);
}
```

## 🔌 Plugin APIs

### 1. Plugin Management API
```typescript
interface PluginAPI {
  endpoints: {
    // Register plugin
    '/plugins/register': {
      method: 'POST';
      body: {
        name: string;
        version: string;
        capabilities: string[];
        config: PluginConfig;
      };
      response: RegistrationResponse;
    };
    
    // Get plugin status
    '/plugins/:pluginId/status': {
      method: 'GET';
      params: {
        pluginId: string;
      };
      response: PluginStatus;
    };
    
    // Update plugin configuration
    '/plugins/:pluginId/config': {
      method: 'PUT';
      params: {
        pluginId: string;
      };
      body: PluginConfig;
      response: UpdateResponse;
    };
  };
}
```

### 2. Plugin Development API
```typescript
interface PluginDevelopmentAPI {
  // Plugin lifecycle hooks
  hooks: {
    onInitialize(): Promise<void>;
    onActivate(): Promise<void>;
    onDeactivate(): Promise<void>;
    onUpdate(config: PluginConfig): Promise<void>;
  };
  
  // Plugin capabilities
  capabilities: {
    registerCapability(name: string, handler: CapabilityHandler): void;
    unregisterCapability(name: string): void;
    invokeCapability(name: string, params: any): Promise<any>;
  };
}
```

## 🔗 Integration APIs

### 1. Exchange Integration API
```typescript
interface ExchangeAPI {
  endpoints: {
    // Connect exchange
    '/integrations/exchange/connect': {
      method: 'POST';
      body: {
        exchange: string;
        credentials: ExchangeCredentials;
        config: ExchangeConfig;
      };
      response: ConnectionResponse;
    };
    
    // Get exchange status
    '/integrations/exchange/:exchangeId/status': {
      method: 'GET';
      params: {
        exchangeId: string;
      };
      response: ExchangeStatus;
    };
  };
}

// Example Implementation
class BinanceIntegration implements ExchangeIntegration {
  async connect(credentials: ExchangeCredentials): Promise<void> {
    // Implementation
  }
  
  async getMarketData(symbol: string): Promise<MarketData> {
    // Implementation
  }
}
```

### 2. Data Provider Integration API
```typescript
interface DataProviderAPI {
  endpoints: {
    // Register data provider
    '/integrations/data-provider/register': {
      method: 'POST';
      body: {
        provider: string;
        credentials: ProviderCredentials;
        config: ProviderConfig;
      };
      response: RegistrationResponse;
    };
    
    // Get data feed
    '/integrations/data-provider/:providerId/feed': {
      method: 'GET';
      params: {
        providerId: string;
        symbol: string;
      };
      response: DataFeed;
    };
  };
}
```

## 📡 WebSocket APIs

### 1. Market Data Stream
```typescript
interface MarketDataStream {
  // Subscribe to market data
  subscribe(symbol: string, callback: (data: MarketData) => void): Subscription;
  
  // Subscribe to multiple symbols
  subscribeMulti(symbols: string[], callback: (data: MarketData[]) => void): Subscription;
  
  // Unsubscribe from updates
  unsubscribe(subscriptionId: string): void;
}

// Example Usage
const ws = new WebSocket('wss://stream.eliza-scanner.com/v1/market');

ws.onmessage = (event) => {
  const marketData: MarketData = JSON.parse(event.data);
  // Handle market data update
};
```

### 2. Trading Updates Stream
```typescript
interface TradingStream {
  // Subscribe to order updates
  subscribeOrders(callback: (update: OrderUpdate) => void): Subscription;
  
  // Subscribe to trade updates
  subscribeTrades(callback: (trade: Trade) => void): Subscription;
  
  // Subscribe to position updates
  subscribePositions(callback: (position: Position) => void): Subscription;
}
```

## ❌ Error Handling

### 1. Error Codes
```typescript
enum APIErrorCode {
  AUTHENTICATION_ERROR = 'auth_error',
  VALIDATION_ERROR = 'validation_error',
  RATE_LIMIT_ERROR = 'rate_limit_error',
  INTERNAL_ERROR = 'internal_error',
  INTEGRATION_ERROR = 'integration_error'
}

interface APIError {
  code: APIErrorCode;
  message: string;
  details?: any;
  timestamp: number;
}
```

### 2. Error Responses
```typescript
// Example error response
{
  "error": {
    "code": "validation_error",
    "message": "Invalid order parameters",
    "details": {
      "field": "quantity",
      "reason": "must be greater than 0"
    },
    "timestamp": 1645564800000
  }
}
```

## ⚡ Rate Limiting

### 1. Rate Limit Configuration
```typescript
interface RateLimitConfig {
  // Requests per minute
  rpm: {
    market: number;
    trading: number;
    account: number;
  };
  
  // Burst limits
  burst: {
    market: number;
    trading: number;
    account: number;
  };
}

// Default limits
const DEFAULT_RATE_LIMITS: RateLimitConfig = {
  rpm: {
    market: 600,
    trading: 100,
    account: 30
  },
  burst: {
    market: 10,
    trading: 5,
    account: 3
  }
};
```

### 2. Rate Limit Headers
```typescript
interface RateLimitHeaders {
  'X-RateLimit-Limit': number;
  'X-RateLimit-Remaining': number;
  'X-RateLimit-Reset': number;
}
```

## 💡 Examples

### 1. Market Analysis Example
```typescript
async function analyzeMarket(symbol: string): Promise<Analysis> {
  // Get market data
  const marketData = await api.get('/market/current', {
    params: { symbol }
  });
  
  // Get indicators
  const indicators = await api.get('/market/indicators', {
    params: {
      symbol,
      indicators: ['rsi', 'macd']
    }
  });
  
  // Analyze data
  return {
    symbol,
    price: marketData.price,
    indicators: indicators,
    analysis: calculateAnalysis(marketData, indicators)
  };
}
```

### 2. Trading Bot Example
```typescript
class TradingBot {
  private api: TradingAPI;
  private stream: MarketDataStream;
  
  async start(): Promise<void> {
    // Subscribe to market data
    this.stream.subscribe('BTCUSDT', async (data) => {
      // Analyze market conditions
      const analysis = await this.analyzeMarket(data);
      
      // Execute trading strategy
      if (analysis.shouldTrade) {
        await this.executeTrade(analysis);
      }
    });
  }
  
  private async executeTrade(analysis: Analysis): Promise<void> {
    // Place order
    const order = {
      symbol: analysis.symbol,
      side: analysis.action,
      type: 'market',
      quantity: analysis.quantity
    };
    
    const response = await this.api.post('/trading/order', order);
    
    // Monitor order status
    this.monitorOrder(response.orderId);
  }
}
```

## 📚 Additional Resources

### 1. API Tools
- [API Reference](https://api-docs.eliza-scanner.com)
- [OpenAPI Specification](https://api-docs.eliza-scanner.com/openapi.json)
- [Postman Collection](https://api-docs.eliza-scanner.com/postman)

### 2. Development Resources
- [SDK Documentation](https://github.com/eliza-scanner/sdk)
- [Example Projects](https://github.com/eliza-scanner/examples)
- [API Changelog](https://api-docs.eliza-scanner.com/changelog)

---

*This API documentation is continuously updated with new endpoints and features.* 