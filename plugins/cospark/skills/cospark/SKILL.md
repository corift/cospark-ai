---
name: cospark
description: Research ad references and create end-to-end AI video ads with Cospark, including UGC hooks and bodies, product shots, voiceovers, media review, and editable timelines. Use when a user asks ChatGPT or Codex to find reference ads or generate, inspect, refine, or assemble ad media with Cospark; do not use for copy or ad strategy alone when no reference or media action is requested.
---

# Cospark

This skill owns Cospark tool execution and shared production guidance. Use the Cospark MCP tools to turn scripts and product media into finished, editable video ads. Preserve the user's exact script and creative direction, and avoid adding unnecessary generation parameters.

## Choose the production guidance

For a new product's broader research-to-production workflow, use [Product to ads](../product-to-ads/SKILL.md). It covers the product brief, reference-ad gallery, concepts, production planning and iteration; a focused media request does not require that full workflow.

For a complete creator-led ad with supporting shots, read [UGC video planning and structure](references/ugc-video-structure.md). It covers the spoken story, B-roll selection, coverage to generate, and pacing against the finished narration, with or without a reference video. Use it when planning or assembling the full ad; a request for one clip does not require a full-ad workflow.

## Creating realistic characters and shots

For finding and evaluating references across ads, TikTok/Reels, and Pinterest, read [Reference discovery and inspection](references/reference-discovery-and-inspection.md). It connects shot-based search, visual review, frame selection, adaptation, and the choice of generation or editing. For an already selected video, use [Using a reference video](references/using-a-reference-video.md).

For B-roll framing, action, timing, and review, read [B-roll production](references/broll-production.md). For generated montages, use [timed shot prompts](references/broll-shot-prompts.md). Both are shared production guidance. For model-specific prompting, use [Gemini Video](../gemini-video/SKILL.md) or [Seedance Video](../seedance-video/SKILL.md) after choosing the model.

For realistic UGC starting frames, begin with a real photograph or an exact frame from a video. When creating a new character, change the face, clothing, and colors while preserving the source's pose, expression, framing, lighting, background, and objects. Use a supplied source first; otherwise find a suitable real photo, for example on Pinterest. Avoid inventing a polished character portrait from text as the default.

Apply the same reference-first approach to B-roll, product demos, inserts, and other realistic ad shots. The reference can show a different product: preserve its useful camera work and physical staging, then adapt the product, branding, and action through the prompt.

Honor explicit text-only or no-reference generation tests. In that mode, references may inform an analysis or written shot plan, but do not create or attach media inputs the user excluded.

Read [Creating realistic characters and shots](references/creating-a-realistic-character.md) before sourcing or remaking A-roll, B-roll, or product-shot references.

## Choose the tool

- Use `generate_image` for a new image from text.
- Use `generate_video` for text-to-video.
- Use `generate_video_from_frames` to turn a strong starting image into a video. Prefer creating or refining the image first so its style, character, composition, lighting, and props are established before adding motion. This image-to-video workflow gives concrete visual direction to preserve and is the preferred approach for controlled, consistent shots, including UGC, B-roll, and product shots. The starting image can be supplied by the user or created for the task; a single frame is enough. Add an ending frame when a specific final composition matters.
- Use `generate_video_with_references` primarily for Seedance workflows for now, when images, videos, or audio should guide the result without serving as exact boundary frames. For an individual Gemini Omni shot, prefer preparing a strong starting image and animating it with `generate_video_from_frames`. This is a workflow preference, not a claim that other models cannot accept references.
- Use `generate_ugc_video` once for a complete talking-head ad built around a longer exact spoken script. Pass `model: "gemini-omni"` explicitly by default (Gemini Omni Flash), the full approved script and concise direction in `prompt`, and the supplied starting images using the connected tool's schema. It handles planning, multiple shots, review, and final composition; do not manually split the full script into standalone generations. Omitting `model` invokes the service's MiniMax default, so do not omit it. Use another model only when the user explicitly chooses it. Save the returned run ID.
- Poll `get_ugc_video_status` with that run ID until it completes or fails. A pending response is normal; wait for its suggested interval and never start a replacement run because of a timeout or pending status.
- A UGC response with `status: "completed"` can still be incomplete. Check `partial` and `failedScenes` before calling the ad complete. Preserve the playable output and report each missing scene, exact dialogue, and returned error. Distinguish provider generation timeouts from source-URL fetch failures; the error alone does not establish their underlying cause. Apply the charged-retry rule below before generating replacements.
- If the user requests several independent hook variants, start one standard video run per requested variant, keep the returned IDs associated with their prompts, and poll each original run. Do not turn the batch into one long UGC workflow.
- If a completed UGC ad needs one shot fixed, generate only the replacement clip with the appropriate standard video tool. Do not rerun the full UGC workflow unless the whole video needs to be regenerated.
- Use `list_voices` when a voiceover needs a specific voice, then pass its ID to `generate_voiceover`.
- Use `generate_voiceover` for narration or standalone spoken audio.
- Use `inspect_media` before making content-based cuts or claiming what happens inside video or audio. For video, visually review the returned contact-sheet image; do not rely only on the text analysis. The first sheet is returned as native MCP image content, while resource links and structured data preserve access to the complete inspection result.
- When exact dialogue matters, inspect the finished video and compare its timestamped transcript with the user's script before calling it approved. Even a non-partial run can omit words. Check scene joins and the final CTA; cross-check a suspected omission against audio or an independent transcript. If a line is wrong, identify the smallest replacement passage or shot. Do not attribute missing words to the model or automatic trimming without evidence.
- Use `upload_media` only when a local file or public URL must become a Cospark media source.
- Use `search_ads` for public creative references. Set `format: "image"` for static ads or `format: "video"` when the user wants video examples. Image queries rank by visual similarity; video queries search indexed transcripts, scene descriptions, on-screen text, and creative metadata.
- For video search results, return the supplied `videoUrl` and visually review the native contact-sheet image before selecting or describing a reference. `contactSheetUrls` preserve access to every sheet in chronological order. Call `inspect_media` with the video URL when the task needs fuller scene, dialogue, or timing analysis.
- Use `list_ad_brands` to discover the library's advertiser names before a brand-filtered search. Use `get_ad` for the full record of an image ad returned by `search_ads`.

Use `list_workspaces` to find an existing workspace and its session ID. Use `create_workspace` when a new editable workspace is needed; optionally call `list_projects` first to attach it to an existing project. Project creation is not available through these tools.

For simple editing, pass the workspace session ID to `read_timeline`, `compose_timeline`, and `edit_timeline` to inspect a timeline, arrange media on tracks, trim clips, and make cuts. Read the current timeline before editing an existing composition.

For full-script talking-head UGC, use the explicit Gemini Omni default above. For `generate_video_with_references`, prefer Seedance unless the user chooses another supported model. For other video workflows, let Cospark select the model unless the user requests one or the references require a capability documented in [references/video-models.md](references/video-models.md). Honor a user-selected model across related shots; do not silently switch to automatic selection. Read that reference before selecting a model explicitly or correcting an unsupported configuration.

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
- Before importing into an editor, inspect the actual output frame rate and dimensions and set the requested timeline frame rate before assembly. A requested 60 fps timeline does not make a 24 fps generated source native 60 fps; disclose any interpolation.
- Return the final durable Cospark media URL and, when useful, its file ID. Do not present temporary upload URLs as generated assets.
- Ad-library video URLs are short-lived reference links, not generated assets. Use them promptly for review or `inspect_media`; do not describe them as durable user-owned output.
