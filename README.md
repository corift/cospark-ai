# Cospark

Research ad references and generate or edit images, videos, UGC, and voiceovers from AI agents through Cospark's authenticated remote MCP server.

MCP server: `https://api.cospark.so/api/mcp/cospark`

## Tools

- `generate_image` — generate an image from a prompt.
- `generate_video` — generate a video from text.
- `generate_video_from_frames` — animate a starting image with an optional ending image.
- `generate_video_with_references` — guide a video with reference images, videos, or audio.
- `generate_ugc_video` — start a complete 9:16 talking-head video from a script, direction, and character image.
- `get_ugc_video_status` — poll a talking-head run until its reviewed final video is ready.
- `list_voices` — list available voice IDs and their characteristics.
- `generate_voiceover` — create narrated audio with duration and timestamped segments.
- `inspect_media` — inspect video or audio and return timing, transcript, scene analysis, and a viewable contact-sheet image.
- `upload_media` — import a public URL or prepare a signed upload for a local media file.
- `search_ads` — search public image or indexed video ads; video results include playable URLs and contact-sheet previews.
- `get_ad` — retrieve the full record for an image ad returned by `search_ads`.
- `list_ad_brands` — discover advertiser names before filtering ad search by brand.
- `list_projects` — list existing projects that can contain a workspace.
- `create_workspace` — create an editable workspace and return its session ID and chat URL.
- `list_workspaces` — list recent workspaces in cursor-paginated pages of up to 10.
- `read_timeline` — read the current tracks and items in a timeline.
- `compose_timeline` — create a simple multi-track timeline.
- `edit_timeline` — add, remove, move, or trim timeline items.

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

## Install the plugin from GitHub

The plugin includes three skills: `cospark` for generation, inspection, uploads, voice selection, and timeline editing; `gemini-omni-ugc` for individual talking-head clips and product handling; and `seedance-video` for reference-driven shots and choreography.

```sh
codex plugin marketplace add corift/cospark-ai --ref main
codex plugin add cospark@cospark
```

Codex checks configured Git marketplaces during startup and refreshes installed plugins when their repository changes. Start a new Codex thread after installation or an update so the latest skill and MCP tools are loaded.

For plugin bundle changes, update `plugins/cospark`, bump the version in `plugins/cospark/.codex-plugin/plugin.json`, and push the commit to `main`. Changes made only to the hosted MCP implementation become available when the server is deployed and do not require a plugin version bump unless the bundled skill, manifest, or MCP configuration also changes.

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

## Media inspection

`inspect_media` returns its first contact sheet as native MCP image content at the generated resolution, so multimodal MCP clients such as Codex can view the frames directly. It also preserves contact-sheet resource links and structured inspection data for clients that need URLs or access to additional sheets. If the image cannot be embedded, the resource links remain available.

## Ad reference search

Use `search_ads` with `format: "image"` for static creative references or `format: "video"` for indexed video ads. Image queries use visual similarity; video queries search indexed transcripts, scene descriptions, on-screen text, and creative metadata. Video results include short-lived playable `videoUrl` values, chronological `contactSheetUrls`, resource links, and the first contact sheet as native high-detail MCP image content. The links are signed without exposing the private video-library credential.

Review the inline contact sheet before choosing a video reference. Call `inspect_media` with its `videoUrl` when a decision needs fuller scene, dialogue, or timing analysis.

## License

The distribution package in this repository is licensed under the MIT License. The Cospark service and API remain subject to the [Cospark Terms of Service](https://cospark.so/terms).

## Maintaining skills

Maintain all three skills under `plugins/cospark/skills/`, including their reference files. This repository is the source of truth. Do not edit installed copies under `~/.codex/plugins/cache/` or keep standalone duplicates under `~/.codex/skills/`.

The installed plugin is a distribution copy of these sources. If an installed copy contains useful changes, reconcile them into this repository before refreshing the plugin so they are not lost. Keep complementary personal skills such as ad research, copywriting, and cataloging in their own source locations; they are separate capabilities, not additional copies of the three plugin skills.

After editing, validate the skills and plugin, update the plugin version, commit, and push to `main`. Refresh the Git marketplace with `codex plugin marketplace upgrade cospark`, reinstall with `codex plugin add cospark@cospark`, and start a new task to load the updated skills.

The OpenAI submission is a separate release. Upload a fresh skill bundle in the portal for each skill update; pushing to GitHub does not update its published snapshot. Include each skill's `SKILL.md`, `references/`, and `agents/` files in the bundle.
