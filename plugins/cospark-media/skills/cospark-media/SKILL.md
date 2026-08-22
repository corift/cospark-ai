---
name: cospark-media
description: Generate CoSpark images and videos, including text-to-video, frame-guided animation, reference-driven video, and media uploads. Use when a user asks to create visual media with CoSpark.
---

# CoSpark Media

Use the CoSpark MCP tools to produce the requested media. Preserve the user's creative direction and avoid adding unnecessary generation parameters.

## Choose the tool

- Use `generate_image` for a new image from text.
- Use `generate_video` for text-to-video.
- Use `generate_video_from_frames` when the user provides a starting image or exact start and end images.
- Use `generate_video_with_references` when images, videos, or audio should guide the result without serving as exact boundary frames.
- Use `upload_media` only when a local file or public URL must become a CoSpark media source.

Let CoSpark select the video model unless the user requests one or the references require a capability documented in [references/video-models.md](references/video-models.md). Read that reference before selecting a model explicitly or correcting an unsupported configuration.

## Handle media inputs

Public media URLs can be passed directly to generation tools. Import them with `upload_media` when a stable CoSpark file ID is useful across multiple calls.

For a local image, video, or audio file:

1. Inspect only the file the user selected and determine its filename, media type, and byte size.
2. Call `upload_media` with a `file` source to receive a file ID and signed PUT request.
3. Upload the exact bytes to the signed URL with the returned method and headers using an available HTTPS-capable file-transfer tool.
4. After a successful upload, pass the file ID to the requested generation tool.

Do not expose the signed upload URL as the final result. It is temporary. If the environment cannot PUT local bytes over HTTPS, explain that limitation and ask for a public media URL instead of pretending the upload succeeded.

## Generate and return results

- Use only `16:9` or `9:16`; default to `16:9` unless the request or source composition clearly indicates portrait.
- Treat model validation errors as actionable guidance. Adjust automatically only when doing so preserves the user's intent; otherwise explain the supported choices.
- Generation uses the authenticated user's CoSpark account and credits. Do not retry a failed or timed-out generation if doing so could create another charged job without the user's approval.
- Return the final durable CoSpark media URL and, when useful, its file ID. Do not present temporary upload URLs as generated assets.
