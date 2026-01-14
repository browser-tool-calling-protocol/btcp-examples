# Basic Setup Test

This example helps you verify that your BTCP setup (MCP server + Chrome extension) is working correctly.

## Prerequisites

Before running this test, ensure you have:

1. Installed the [BTCP Chrome extension](https://github.com/browser-tool-calling-protocol/btcp-chrome)
2. Built and configured the [BTCP MCP server](https://github.com/browser-tool-calling-protocol/btcp-mcp)
3. Chrome browser open with the extension active

## Setup

### Step 1: Configure MCP Server

Copy the `.mcp.json` file to this directory or your home directory, then update the path to point to your btcp-mcp installation:

```json
{
  "mcpServers": {
    "btcp": {
      "command": "node",
      "args": ["/absolute/path/to/btcp-mcp/dist/index.js"]
    }
  }
}
```

### Step 2: Verify Chrome Extension

1. Open Chrome browser
2. Click on the BTCP extension icon in the toolbar
3. Ensure the extension shows "Connected" or ready status
4. Keep at least one Chrome tab open

### Step 3: Test the Connection

Open your MCP-compatible AI agent (Claude Desktop or Claude Code) in this directory and ask it to:

```
List all available BTCP tools
```

or

```
Check if the BTCP browser extension is connected
```

## Expected Results

If everything is working correctly, you should see:

1. **MCP Server Connected**: The agent should be able to communicate with the BTCP MCP server
2. **Browser Extension Connected**: The MCP server should be connected to your Chrome extension
3. **Tools Available**: You should see a list of available browser tools (varies based on active tab/page)

## Troubleshooting

### "No tools available" or empty response

- Ensure Chrome is open with the BTCP extension installed
- Check that the extension is enabled (not disabled)
- Try refreshing the Chrome page or restarting Chrome

### "MCP server not found" or connection errors

- Verify the path in `.mcp.json` is correct and absolute
- Ensure you ran `npm run build` in the btcp-mcp directory
- Check that Node.js is installed and accessible

### Extension not connecting

- Open Chrome DevTools (F12) and check the console for errors
- Try removing and re-adding the extension
- Ensure no firewall is blocking local connections

## What's Next?

Once you've verified the basic setup works, explore other examples:
- Page interaction tools
- Form filling automation
- Data extraction from web pages
