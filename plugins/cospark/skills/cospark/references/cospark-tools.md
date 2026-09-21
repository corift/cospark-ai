# Cospark tools

Read when executing Cospark tools. Use the connected tool schema for current inputs, supported values, and returned fields.

## Choose the tool

- Use `generate_image` to create an image or edit supplied images. For an edit, pass the original frame in `references` as a public URL or Cospark file ID. `nano-banana-pro` selects Nano Banana Pro; `nano-banana-2` selects Nano Banana 2 / Flash. Honor the requested model and check the live schema for supported quality and aspect ratio. Keep every casting attempt anchored to the original frame.
- Use `generate_video` for text-to-video.
- Use `generate_video_from_frames` to turn a strong starting image into a video. Prefer creating or refining the image first so its style, character, composition, lighting, and props are established before adding motion. This image-to-video workflow gives concrete visual direction to preserve and is the preferred approach for controlled, consistent shots, including UGC, B-roll, and product shots. The starting image can be supplied by the user or created for the task; a single frame is enough. Add an ending frame when a specific final composition matters.
- Use `generate_video_with_references` primarily for Seedance workflows for now, when images, videos, or audio should guide the result without serving as exact boundary frames. For an individual Gemini Omni shot, prefer preparing a strong starting image and animating it with `generate_video_from_frames`. This is a workflow preference, not a claim that other models cannot accept references.
- For reference-led creator ads, use individual `generate_video_from_frames` calls for the dialogue and B-roll, then assemble in the chosen editor. Follow [the UGC flow](ugc-video-structure.md) and pass `model: "gemini-omni"` explicitly for its Gemini route unless another model is requested.
- Use `generate_ugc_video` when the user explicitly requests automatic full-script planning and assembly. Pass the full approved script and concise direction in `prompt`, starting images according to the connected schema, and explicit `model: "gemini-omni"` unless another supported model is chosen. Omitting the model invokes the service's MiniMax default. Save the returned run ID; do not use this tool for a request to generate clips manually.
- Poll `get_ugc_video_status` with that run ID until it completes or fails. A pending response is normal; wait for its suggested interval and never start a replacement run because of a timeout or pending status.
- A UGC response with `status: "completed"` can still be incomplete. Check `partial` and `failedScenes` before calling the ad complete. Preserve the playable output and report each missing scene, exact dialogue, and returned error. Distinguish provider generation timeouts from source-URL fetch failures; the error alone does not establish their underlying cause. Apply the charged-retry rule below before generating replacements.
- If the user requests several independent hook variants, start one standard video run per requested variant, keep the returned IDs associated with their prompts, and poll each original run. Do not turn the batch into one long UGC workflow.
- If a completed UGC ad needs one shot fixed, generate only the replacement clip with the appropriate standard video tool. Do not rerun the full UGC workflow unless the whole video needs to be regenerated.
- Use `list_voices` when a voiceover needs a specific voice, then pass its ID to `generate_voiceover`.
- Use `generate_voiceover` for narration or standalone spoken audio.
- Use `inspect_media` before making content-based cuts or claiming what happens inside video or audio. For video, visually review the returned contact-sheet image; do not rely only on the text analysis. The first sheet is returned as native MCP image content, while resource links and structured data preserve access to the complete inspection result.
- When exact dialogue matters, inspect the finished video and compare its timestamped transcript with the user's script before calling it approved. Even a non-partial run can omit words. Check scene joins and the final CTA; cross-check a suspected omission against audio or an independent transcript. If a line is wrong, identify the smallest replacement passage or shot. Do not attribute missing words to the model or automatic trimming without evidence.
- Use `upload_media` only when a local file or public URL must become a Cospark media source.
- Use Cospark's Instagram and TikTok search and detail tools for organic creator and B-roll discovery; follow [reference discovery](reference-discovery-and-inspection.md) for the search-to-inspection flow. A separate ScrapeCreators MCP is not required. Keep compact responses and bound shortlists with `maxResults` where supported.
- Use `search_ads` for public creative references. Set `format: "image"` for static ads or `format: "video"` when the user wants video examples. Image queries rank by visual similarity; video queries search indexed transcripts, scene descriptions, on-screen text, and creative metadata.
- For video search results, return the supplied `videoUrl` and visually review the native contact-sheet image before selecting a reference. `contactSheetUrls` preserve access to every sheet in chronological order. Call `get_ad` for the selected video when the task needs its compact evidence document with persisted summary, hook, CTA, audio treatment, transcript, semantic scenes, and visible text. Its resource links supply the playable video and contact-sheet previews. These scene boundaries are approximate and must not be reported as verified cuts.
- Use `list_ad_brands` to discover the library's advertiser names before a brand-filtered search.
- Use `get_ad` for the compact evidence document of any selected image or indexed video ad. It returns the ad ID as structured output and supplies the analysis as readable text. Use `inspect_media` for generated, uploaded, or external media, or when the persisted ad record leaves a material question unanswered; do not re-inspect a library video just to recreate analysis already stored for it.

Use `list_workspaces` to find an existing workspace and its session ID. Use `create_workspace` when a new editable workspace is needed; optionally call `list_projects` first to attach it to an existing project. Project creation is not available through these tools.

For simple editing, pass the workspace session ID to `read_timeline`, `compose_timeline`, and `edit_timeline` to inspect a timeline, arrange media on tracks, trim clips, and make cuts. Read the current timeline before editing an existing composition.

For Gemini talking-head UGC, use the explicit model selection above for both individual clips and requested automatic orchestration. For `generate_video_with_references`, prefer Seedance unless the user chooses another supported model. For other video workflows, let Cospark select the model unless the user requests one or the references require a capability documented in [video models](video-models.md). Honor a user-selected model across related shots; do not silently switch to automatic selection. Read that reference before selecting a model explicitly or correcting an unsupported configuration.

## Track runs without losing results

Record the prompt, settings, source and returned run ID for every shot as soon as the response arrives. Read both structured output and text/error content; an absent `structuredContent` field is not an empty successful response. Poll the original ID at the suggested interval until completion or failure. A `processing` response is not proof that the provider is making progress, and an unchanged status does not justify another generation. If a submission times out without an ID, its outcome is unknown; retain the original response and report that uncertainty. Another potentially charged attempt requires authorization.

Keep generation, inspection, rendering and upload statuses separate. A completed generation with a failed inspection still has usable source media; do not describe it as a failed render or submit a replacement just to obtain a transcript.

## When inspection is unavailable

Try `inspect_media` first. If it times out or fails, preserve the generated file and review the same media using available local tools: probe its technical properties, view representative frames and cut boundaries, and obtain word timings through Resolve transcription or another available transcription tool. Reuse existing transcripts; do not repeatedly submit the same analysis without a reason. If using another service, stay within the task's permissions and disclose any unavailable review.

Compare the actual dialogue with the script, including the final word and disposable phrases. Use silence analysis only to refine boundaries, not to identify speech. Cross-check ambiguous brand names or suspected omissions against audio or an independent transcript before calling them spoken errors. If the necessary evidence is still missing, leave the relevant cut or approval unverified rather than guessing. Report technical checks, sampled visuals and audible review accurately.

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
