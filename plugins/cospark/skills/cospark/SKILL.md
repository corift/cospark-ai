---
name: cospark
description: Create end-to-end AI video ads with Cospark, including UGC hooks and bodies, product shots, voiceovers, media review, and editable timelines. Use when a user asks ChatGPT or Codex to generate, inspect, refine, or assemble ad media with Cospark; do not use for copy or ad strategy alone when no media action is requested.
---

# Cospark

Use the Cospark MCP tools to turn scripts and product media into finished, editable video ads. Preserve the user's exact script and creative direction, and avoid adding unnecessary generation parameters.

## Choose the tool

- Use `generate_image` for a new image from text.
- Use `generate_video` for text-to-video.
- Use `generate_video_from_frames` for one-off clips or ad shots when the user provides a starting image or exact start and end images. It is a good fit for short UGC hooks that must preserve the starting character and scene.
- Use `generate_video_with_references` when images, videos, or audio should guide the result without serving as exact boundary frames.
- Use `generate_ugc_video` once for a complete talking-head ad built around a longer exact spoken script. It handles planning, multiple shots, review, and final composition. It defaults to `minimax-h3-max`; pass `gemini-omni` only when the user requests Gemini. Save the returned run ID.
- Poll `get_ugc_video_status` with that run ID until it completes or fails. A pending response is normal; wait for its suggested interval and never start a replacement run because of a timeout or pending status.
- If the user requests several independent hook variants, start one standard video run per requested variant, keep the returned IDs associated with their prompts, and poll each original run. Do not turn the batch into one long UGC workflow.
- If a completed UGC ad needs one shot fixed, generate only the replacement clip with the appropriate standard video tool. Do not rerun the full UGC workflow unless the whole video needs to be regenerated.
- Use `list_voices` when a voiceover needs a specific voice, then pass its ID to `generate_voiceover`.
- Use `generate_voiceover` for narration or standalone spoken audio.
- Use `inspect_media` before making content-based cuts or claiming what happens inside video or audio.
- When exact dialogue matters, inspect the finished video and compare its timestamped transcript with the user's script before calling it approved. If a line is wrong, identify the smallest replacement passage or shot.
- Use `upload_media` only when a local file or public URL must become a Cospark media source.

Use `list_workspaces` to find an existing workspace and its session ID. Use `create_workspace` when a new editable workspace is needed; optionally call `list_projects` first to attach it to an existing project. Project creation is not available through these tools.

For simple editing, pass the workspace session ID to `read_timeline`, `compose_timeline`, and `edit_timeline` to inspect a timeline, arrange media on tracks, trim clips, and make cuts. Read the current timeline before editing an existing composition.

Let Cospark select the video model unless the user requests one or the references require a capability documented in [references/video-models.md](references/video-models.md). Read that reference before selecting a model explicitly or correcting an unsupported configuration.

## Handle media inputs

Public media URLs can be passed directly to generation tools. Import them with `upload_media` when a stable Cospark file ID is useful across multiple calls.

For a local image, video, or audio file:

1. Inspect only the file the user selected and determine its filename, media type, and byte size.
2. Call `upload_media` with a `file` source to receive a file ID and signed PUT request.
3. Upload the exact bytes to the signed URL with the returned method and headers using an available HTTPS-capable file-transfer tool.
4. After a successful upload, pass the file ID to the requested generation tool.

Do not expose the signed upload URL as the final result. It is temporary. If the environment cannot PUT local bytes over HTTPS, explain that limitation and ask for a public media URL instead of pretending the upload succeeded.

## Generate and return results

- Use only `16:9` or `9:16`; default to `16:9` unless the request or source composition clearly indicates portrait.
- Treat model validation errors as actionable guidance. Adjust automatically only when doing so preserves the user's intent; otherwise explain the supported choices.
- Generation uses the authenticated user's Cospark account and credits. Do not retry a failed or timed-out generation if doing so could create another charged job without the user's approval.
- Talking-head UGC generation takes several minutes. Start it once, then poll its status for the reviewed final result.
- For independent variants, parallel generation is appropriate when the user requested the batch and each run has distinct creative direction. Track every run ID and report failures separately instead of silently replacing them.
- Return the final durable Cospark media URL and, when useful, its file ID. Do not present temporary upload URLs as generated assets.
