# Cospark

Generate images and videos from AI agents through Cospark's authenticated remote MCP server.

MCP server: `https://api.cospark.so/api/mcp/cospark`

## Tools

- `generate_image` — generate an image from a prompt.
- `generate_video` — generate a video from text.
- `generate_video_from_frames` — animate a starting image with an optional ending image.
- `generate_video_with_references` — guide a video with reference images, videos, or audio.
- `upload_media` — import a public URL or prepare a signed upload for a local media file.

## Connect with Codex

Add the server to `~/.codex/config.toml`:

```toml
[mcp_servers.cospark]
url = "https://api.cospark.so/api/mcp/cospark"
auth = "oauth"
tool_timeout_sec = 900
```

Then authenticate:

```sh
codex mcp login cospark
```

Codex opens the Cospark sign-in flow and stores the resulting OAuth credentials locally.

## Install the plugin from this repository

The plugin adds workflow guidance for model selection, local media uploads, frame animation, and reference-driven video.

```sh
git clone https://github.com/corift/cospark-ai.git
codex plugin marketplace add ./cospark-ai
codex plugin add cospark@cospark
```

Start a new Codex thread after installation so the skill and MCP tools are loaded.

## Other MCP clients

Configure a Streamable HTTP server named `cospark` with this URL:

```text
https://api.cospark.so/api/mcp/cospark
```

The client must support browser-based OAuth. If it supports configurable tool timeouts, allow at least 10 minutes for video generation.

## Media uploads

Public media URLs can be used directly. Local files use a two-step signed upload:

1. Call `upload_media` with the filename, media type, and byte size.
2. PUT the local file bytes to the returned signed URL using the returned headers.
3. Use the returned Cospark file ID in a generation tool.

Local files can be images, videos, or audio up to 100 MB.

## License

The distribution package in this repository is licensed under the MIT License. The Cospark service and API remain subject to the [Cospark Terms of Service](https://cospark.so/terms).
