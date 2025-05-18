# Linear Issues MCP Server

[![smithery badge](https://smithery.ai/badge/@keegancsmith/linear-issues-mcp-server)](https://smithery.ai/server/@keegancsmith/linear-issues-mcp-server)

This is a simple MCP (Model Context Protocol) server that provides read-only access to Linear issues. It allows language models to fetch Linear issues and their associated data using a Linear API token.

## Features

The server provides two tools:

- `linear_get_issue`: Fetches basic details about a Linear issue by URL or identifier
- `linear_get_issue_with_comments`: Fetches complete information about a Linear issue including all comments

## Requirements

- Node.js
- A Linear API token or OAuth access token

### Installing via Smithery

To install Linear Issues Server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@keegancsmith/linear-issues-mcp-server):

```bash
npx -y @smithery/cli install @keegancsmith/linear-issues-mcp-server --client claude
```

## Installation

No installation is needed if you use npx. Just make sure you have Node.js and npm installed.

## Getting a Linear API Token

You can obtain a Linear API token in two ways:

1. **API Key (simplest):** Generate an API key in your [Linear API settings](https://linear.app/settings/api)

2. **OAuth Token:** For more advanced use cases or user-specific access
   - [Create an OAuth2 application in Linear](https://linear.app/settings/api/applications/new)
   - Follow the OAuth flow to get a user access token

## Usage with Claude for Desktop

To use this MCP server with Claude for Desktop:

1. Make sure you have your Linear API token ready
2. Add the server to your Claude for Desktop configuration at:

   - MacOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Linux: `~/.config/Claude/claude_desktop_config.json`
   - Windows: `%AppData%\Claude\claude_desktop_config.json`

Example configuration:

```json
{
  "mcpServers": {
    "linear-issues": {
      "command": "npx",
      "args": ["-y", "@keegancsmith/linear-issues-mcp-server"],
      "env": {
        "LINEAR_API_TOKEN": "your_linear_api_token_here"
      }
    }
  }
}
```

3. Restart Claude for Desktop

## Example Usage

Once the server is set up, you can use it in Claude to interact with Linear issues:

```
Can you get me the details for issue ENG-123?
```

Claude will use the `linear_get_issue` tool with your issue ID, accessing the token from environment variables.

```
What are all the comments on the issue at https://linear.app/company/issue/ENG-123/issue-title?
```

Claude can use `linear_get_issue_with_comments` to fetch the full issue details including comments.

## License

MIT
