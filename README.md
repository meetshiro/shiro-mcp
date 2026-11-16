# Shiro MCP connector

Connect your AI assistant to [Shiro](https://meetshiro.com/?utm_source=github&utm_medium=directory&utm_campaign=2026-11-distribution), a book-writing app for novels and long non-fiction, in English and French.

Your agent can read your whole book: the outline, every scene, your characters and places, your style sheet and your notes. Ask it to find where a character was last seen, check a timeline, count how often a phrase comes back, or tighten a scene.

This repository holds the public connection configuration, a Shiro skill and setup notes for the hosted Shiro MCP server. It does not contain Shiro's app or server code.

## Connect

- Endpoint: `https://api.meetshiro.com/mcp`
- Transport: Streamable HTTP
- Authentication: OAuth 2.1 with PKCE and dynamic client registration
- Account: sign in with your Shiro account, or create a free one from the sign-in page

### Claude Code

```sh
claude mcp add --transport http shiro https://api.meetshiro.com/mcp
```

Then open `/mcp` and sign in to Shiro in the browser. Or install the plugin, which adds the connection and the Shiro skill:

```sh
/plugin marketplace add meetshiro/shiro-mcp
/plugin install shiro@shiro
```

### Claude and Claude Desktop

Settings, Connectors, Add custom connector, then paste `https://api.meetshiro.com/mcp`.

### Gemini CLI

```sh
gemini extensions install https://github.com/meetshiro/shiro-mcp
```

Then run `/mcp auth shiro` to sign in.

### Cursor

[Add Shiro to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=shiro&config=eyJ1cmwiOiJodHRwczovL2FwaS5tZWV0c2hpcm8uY29tL21jcCJ9), or add to `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "shiro": { "url": "https://api.meetshiro.com/mcp" } } }
```

### Kiro

[Add Shiro to Kiro](https://kiro.dev/launch/mcp/add?name=shiro&config=%7B%22url%22%3A%22https%3A%2F%2Fapi.meetshiro.com%2Fmcp%22%7D)

### Cline

In the Cline CLI or the extension's MCP servers, add a server: type **Remote (HTTP)**, URL `https://api.meetshiro.com/mcp`, authentication **OAuth**, and leave the OAuth client ID empty (Shiro registers the client itself). Cline opens the browser to sign in.

### VS Code

```sh
code --add-mcp '{"name":"shiro","type":"http","url":"https://api.meetshiro.com/mcp"}'
```

### Codex

```sh
codex mcp add shiro --url https://api.meetshiro.com/mcp
codex mcp login shiro
```

### ChatGPT and other clients

Add `https://api.meetshiro.com/mcp` as a remote MCP server (in ChatGPT, through developer mode connectors) and complete the OAuth sign-in. `.mcp.json` in this repository holds the same declaration. No key and no local process are needed.

## What your agent can do

About 85 tools cover what a writer does in Shiro:

- **Read**: the project card, the outline (scene by scene or one line per chapter), scenes, whole chapters a page at a time, World entries, notes, research, comments, history and stats.
- **Write**: edit and insert prose, create chapters and scenes, try another take of a scene as an alternative, fill World entries, file notes and Inbox captures.
- **Shape**: structure, story beats, revision passes, labels, goals and the style sheet.
- **Check and publish**: continuity checks, counts, compile, EPUB and print export.

## How changes are kept

Your agent works on the book as you would, and nothing is lost. Every call is one entry in the project's History, named for the agent, and each scene it changes keeps a version from before and after, so you can restore any of them. Scenes and notes you hide from Shiro stay out of its reach. The agent can also choose to suggest a change instead of making it: the suggestion waits in Shiro until you apply or reject it. An agent connected by someone who may only suggest on a shared book always suggests.

## Example prompts

- Where does Mara last appear before chapter 12, and what is she carrying?
- List every scene set at night in part two, with its word count.
- Tighten the opening scene of chapter 3 and keep my voice.
- Check that the ages in my World entries match the timeline.
- Export the book as an EPUB.

## Documentation and support

- [Connection guide](https://meetshiro.com/agents/)
- [llms.txt](https://meetshiro.com/llms.txt)
- [Support](https://meetshiro.com/support/)
- [Privacy](https://meetshiro.com/privacy/)
- [Terms](https://meetshiro.com/terms/)
- Email: hello@meetshiro.com

## License

The connection configuration, the skill and the documentation in this repository are MIT licensed. The hosted Shiro service is governed by its own [terms](https://meetshiro.com/terms/). See `NOTICE` for the name and logo.
