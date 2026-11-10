# Papex for Cursor

This plugin connects Cursor to [Papex](https://papex.org), the record layer for AI-era science.
It runs the Papex MCP server (`@papexlabs/mcp`) on your computer.

**What the agent can do:** prepare private Hypothesis, Discovery and Publication drafts for your
review, read public Papex profiles and records, propose changes to a draft you select, and stage
supporting files you choose.

**What the agent cannot do:** sign a research record as you, accept its own proposals, make rights
statements or publish. You review, edit, sign and choose what to share in Papex.

## Install

In Cursor, open **Customize**, find **Papex** and select **Install**.

Requires Node.js 22.12 or newer. Cursor starts the server with `npx`, which downloads the pinned
version of `@papexlabs/mcp` on first start.

To add only the server by hand, put this in `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "papex": {
      "command": "npx",
      "args": ["-y", "@papexlabs/mcp@0.19.1"]
    }
  }
}
```

## Connect your Papex account

Without a connection, the plugin reads public Papex records only. To let the agent prepare drafts,
ask it to **connect to Papex**:

1. The agent gives you a link and a pairing code.
2. You open the link in a browser signed in to Papex. If you are not signed in, Papex asks you to
   sign in first and then shows the request. Check the code and the permissions, and sign them.
3. Back in Cursor, the agent asks whether the account Papex names is yours. Answer, and the new
   tools load.

The plugin has no settings to fill in. The connection's key is made on your computer, kept in
`~/.papex/delegate-private-key.json`, and signs requests there. Revoke the connection in Papex
under **Workspace → Connections** at any time to disable it.

**Cloud agents.** A Cursor cloud agent runs the server on its own machine, so the key is made and
kept there, not on your computer, and it goes when that machine does. Connect again in a new cloud
agent, and revoke the old connection in Papex.

## Start without an account

The agent can also start on Papex before you have an account: ask it to start on Papex without an
account (`papex_connect` with `withoutAccount`). It keeps up to 3 private drafts for 30 days, with no
files, until you claim them with the link and code it gives you. Nothing is public until you sign.
How agents do this: https://papex.org/auth.md.

## Data

Drafts, selected files and their hashes go to Papex; seals and checkpoints send commitments, not
file contents or paths. The app name Papex shows for a connection is the one Cursor reports about
itself. See the [privacy policy](https://papex.org/privacy) and the [terms](https://papex.org/terms).

A Papex record shows who signed which version and when. It is not peer review and does not
establish that a result is correct.

## Support

hello@papex.org · security reports: security@papex.org

## License

Apache-2.0
