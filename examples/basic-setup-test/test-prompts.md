# Test Prompts for BTCP Setup Verification

Use these prompts with your MCP-compatible AI agent to verify your BTCP setup.

## Basic Connectivity Tests

### 1. List Available Tools

```
List all available BTCP tools from the browser extension.
```

**Expected**: A list of tool names/descriptions, or confirmation that the connection is active.

### 2. Check Connection Status

```
Check if the BTCP browser extension is connected and responding.
```

**Expected**: Status indicating the browser extension is connected.

### 3. Get Current Page Info

```
Using BTCP, get information about the current browser tab (URL, title).
```

**Expected**: Returns the URL and title of the active Chrome tab.

## Verification Checklist

After running the tests above, verify:

- [ ] MCP server starts without errors
- [ ] Browser extension shows as connected
- [ ] At least one tool is available
- [ ] Tool calls return results (not errors)

## If Tests Fail

1. **Restart sequence**: Close Claude/agent -> Close Chrome -> Open Chrome -> Open agent
2. **Check logs**: Look for errors in Chrome DevTools console (F12)
3. **Verify paths**: Ensure `.mcp.json` has correct absolute paths
4. **Extension permissions**: Make sure the extension has necessary permissions
