# Cospark for AI agents

[Cospark](https://www.cospark.so) helps you research ad references and create images, video clips, UGC ads and voiceovers from your AI assistant. This repository provides a small workflow skill and setup instructions for connecting your own Cospark account. The maintained production guides come from the server's `read_docs` tool.

## Install the skill

```sh
pnpm dlx skills add corift/cospark-ai --skill cospark
```

The skill can be installed in clients supported by the skills CLI. A skill-only install does **not** add the MCP server. Add `https://api.cospark.so/mcp` as a remote Streamable HTTP server and sign in through browser OAuth. See [Cospark MCP setup](https://www.cospark.so/mcp).

For Claude Code:

```sh
claude mcp add --transport http cospark https://api.cospark.so/mcp
```

Then run `/mcp` and sign in to Cospark. Reuse an existing connection instead of adding a duplicate.

## Install in Hermes Agent

Requires Hermes **0.23.0 or later**. Install the Agent Plugins v1 skill package directly while the catalog submission is under review:

```sh
hermes plugins install corift/cospark-ai#plugins/cospark
```

The portable package installs the skill. Add the hosted MCP connection separately using Hermes' native OAuth support:

```sh
hermes mcp add cospark --url https://api.cospark.so/mcp --auth oauth
```

Complete browser sign-in with your own Cospark account and save the connection. If you already have it configured, reuse it; `hermes mcp login cospark` reconnects an existing server. Start a new interactive session so the skill and tools load, then ask:

> Use Cospark to read its documentation and explain how to turn my product photos into a video ad. Don't generate anything yet.

The first tool call should be `read_docs` with no path. If sign-in is unavailable, stop and report the setup requirement. Connecting or reading docs does not prove a paid production workflow has been tested.

Once Nous maintainers merge the catalog entry, the short install command will be `hermes plugins install cospark`. A submitted PR is not a published marketplace listing.

## What you can ask for

- Research references and plan an ad for a product.
- Turn supplied product images into an authorized video clip.
- Create a voiceover from approved dialogue.
- Inspect a finished video for product and dialogue errors.

The exact tools and supported models are provided by the live server. Ask the agent to read the relevant guides before research, generation or editing. References and view counts are not proof of campaign performance.

## Data, cost and permissions

Every MCP request goes to **api.cospark.so** and acts on your signed-in Cospark account. Prompts, selected media and project content supplied to tools are processed by Cospark and the providers required for those operations. Read the [privacy policy](https://www.cospark.so/privacy) and [terms](https://www.cospark.so/terms).

Generation, media inspection and social research can spend your Cospark credits. Project writes change your account's files. Paid retries need authorization; retain job IDs and poll existing work to avoid duplicate charges. This package does not authorize posting ads or spending campaign budgets.

The portable package contains a workflow skill and metadata: no executable plugin code, installation script, OAuth bridge, background process, self-updater or package telemetry. Installing it does not register tools, modify MCP configuration, or access credentials. The separate skills CLI has its own installation telemetry policy.

After you explicitly connect the hosted MCP, Hermes handles OAuth discovery, browser sign-in, token storage and refresh. The skill does not read credential stores or change host approval settings. The hosted tools and returned documentation can change independently of the pinned package commit; the catalog SHA pins the skill and metadata, not Cospark's service implementation.

## Maintenance

Version 0.5.0 replaces the retired bundled manuals with a connection-and-routing skill. Production guidance still has one maintained source: the hosted `read_docs` documentation. Historical references and evaluation records in git history are not current model instructions.

The existing Codex plugin manifest uses `.mcp.json` with native HTTP OAuth. Hermes reads `plugin.json` and the shared skill; its MCP connection is configured separately as shown above. Both use the supported `/mcp` URL. This repository is separate from the OpenAI developer-portal submission package (version 2.1.1); this release does not modify that submission.

The package is [MIT licensed](https://github.com/corift/cospark-ai/blob/main/LICENSE); the hosted service remains subject to Cospark's terms.
