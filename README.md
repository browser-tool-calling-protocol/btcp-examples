# BTCP Examples

Example projects demonstrating the [Browser Tool Calling Protocol (BTCP)](https://github.com/browser-tool-calling-protocol/.github) - an open standard enabling AI agents to invoke browser-based tools.

## What is BTCP?

BTCP allows AI agents to call browser-side tools with direct access to browser context. Unlike server-side tools, BTCP tools are **client-defined**, meaning they originate from the browser and have access to DOM, browser state, and web application context.

### Key Benefits

- **Client-defined tools**: Tool interfaces originate on the client, enabling context-aware functionality
- **Browser-native access**: Direct access to browser state, DOM, and web apps
- **No round-trip overhead**: Multi-step workflows execute in a single request
- **Privacy-first**: End-to-end encryption keeps browser data private

## Prerequisites

Before running these examples, you need:

1. **Chrome Browser** with the BTCP extension installed
2. **BTCP MCP Server** running locally
3. An **MCP-compatible AI agent** (Claude Desktop, Claude Code, etc.)

## Quick Setup

### 1. Install the Chrome Extension

Install the BTCP Chrome extension from the [btcp-chrome repository](https://github.com/browser-tool-calling-protocol/btcp-chrome):

1. Clone or download the extension
2. Open Chrome and navigate to `chrome://extensions/`
3. Enable "Developer mode" (toggle in top right)
4. Click "Load unpacked" and select the extension directory
5. The BTCP extension icon should appear in your toolbar

### 2. Install the MCP Server

```bash
# Clone the MCP server
git clone https://github.com/browser-tool-calling-protocol/btcp-mcp.git
cd btcp-mcp

# Install dependencies
npm install

# Build the server
npm run build
```

### 3. Configure Your AI Agent

Add the BTCP MCP server to your agent's configuration.

**For Claude Desktop** (`~/Library/Application Support/Claude/claude_desktop_config.json` on macOS):

```json
{
  "mcpServers": {
    "btcp": {
      "command": "node",
      "args": ["/path/to/btcp-mcp/dist/index.js"]
    }
  }
}
```

**For Claude Code** (`.mcp.json` in your project or home directory):

```json
{
  "mcpServers": {
    "btcp": {
      "command": "node",
      "args": ["/path/to/btcp-mcp/dist/index.js"]
    }
  }
}
```

## Examples

### [Basic Setup Test](./examples/basic-setup-test/)

A minimal example to verify your BTCP setup is working correctly. Tests:
- MCP server connectivity
- Browser extension connection
- Tool discovery

## How It Works

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   AI Agent      │────▶│   BTCP MCP      │────▶│ Chrome Extension│
│ (Claude, etc.)  │     │   Server        │     │   (Browser)     │
└─────────────────┘     └─────────────────┘     └─────────────────┘
        │                       │                       │
        │  1. Tool Request      │  2. Forward to       │
        │─────────────────────▶│     Browser          │
        │                       │─────────────────────▶│
        │                       │                       │
        │                       │  3. Execute in       │
        │                       │     Browser Context  │
        │                       │◀─────────────────────│
        │  4. Return Result     │                       │
        │◀─────────────────────│                       │
```

1. AI agent sends a tool call request via MCP
2. BTCP MCP server forwards the request to the browser extension
3. Extension executes the tool with full browser context access
4. Results are returned through the same path

## Resources

- [BTCP Specification](https://github.com/browser-tool-calling-protocol/btcp-specification)
- [Chrome Extension](https://github.com/browser-tool-calling-protocol/btcp-chrome)
- [MCP Server Bridge](https://github.com/browser-tool-calling-protocol/btcp-mcp)
- [JavaScript Client](https://github.com/browser-tool-calling-protocol/btcp-client)

## License

MPL-2.0
