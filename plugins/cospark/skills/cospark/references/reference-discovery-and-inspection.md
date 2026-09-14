# Reference discovery and inspection

Use when a brief needs visual references for A-roll, B-roll, product shots, or an edited sequence. This workflow coordinates available search, inspection, image-editing, generation, and editing tools; it does not provide new API endpoints or assume every search provider is connected. Scale the work to the request: a quick test may need only a few inspected shots.

## Search for the shot

Translate the brief into visible actions and compositions before searching. For meal planning, useful queries include “overhead dinner ingredients,” “woman checking phone beside groceries,” and “close-up fork lifting spaghetti.” A similar product category can help, but a different category may supply the right grip, camera angle, light, or movement.

Choose sources for the evidence needed:

| Source | Useful evidence |
| --- | --- |
| Ads | Shot sequence, relationship to narration, product demonstration, cut rhythm and camera moves. |
| TikTok / Reels | Everyday activities, candid environments, physical movement and creator filming setups. |
| Pinterest / photographs | Specific compositions, poses, rooms, food presentation and lighting. A still cannot establish motion or edit rhythm. |

Start with supplied media or a suitable saved reference. For ad discovery, use Cospark `search_ads`; use `list_ad_brands` before filtering by advertiser. For social or Pinterest search, use an available connector, documented ScrapeCreators integration, or browser search. Verify supported endpoints and returned media fields before calling them. A provider offering a capability does not mean the current Cospark MCP exposes it. If one source is unavailable, use another suitable source and disclose the gap rather than building an integration as part of a reference-only request.

## Inspect before selecting

Use search thumbnails or contact sheets to shortlist candidates, then inspect the actual selected media. For video, use `inspect_media` and visually review its returned sheets alongside the scene timings. Reuse an adequate existing inspection. Watch the relevant passage when motion, object handling, a reveal, or exact cuts determine suitability. A transcript alone is insufficient for selecting visual B-roll.

Prefer candidates with useful framing, visible hands and props, plausible action, suitable light, and enough detail for the intended output. Check for obstructing text, motion blur, awkward transitional poses, and backgrounds that would be difficult to adapt. Rank by the target shot's needs; views, likes, or ad longevity do not establish visual suitability or conversion performance.

When a montage should feel recorded by one person, assess the set together: camera distance, viewpoint, light, surfaces, framing and food/product styling should plausibly belong to the same filming context. One creator's video or related sequence may provide stronger continuity than individually attractive photos from unrelated sources. For casual food recordings, search for someone showing their meal; a styled recipe photograph or an eating action may serve a different brief. Prefer sources that already contain the intended wide view instead of relying on later digital zoom-out to reveal missing surroundings.

For a montage, record shot order, approximate duration, action, shot scale, camera movement and crop changes separately. Contact sheets and scene detection suggest boundaries; confirm before/after frames or playback before calling cut timings exact. Distinguish a hard cut, static punch-in and continuous camera move.

Show a compact shortlist with a preview, source link, what each reference contributes, and any material limitation. For video, retain timestamps and a playable source. Stop at this deliverable when the user requested research or frame review only; do not make preview approval a new mandatory step when generation is already authorized.

## Extract and adapt the selected frames

Obtain the actual individual frame at the selected timestamp and best available quality. Use a contact sheet to choose the moment, not as the image-edit input. Record which source and timestamp produced each frame.

Follow [Creating realistic characters and shots](creating-a-realistic-character.md) for adaptation. Assign separate roles to composition, character identity and product references. Preserve the source's useful photographic texture, lighting and physical staging while making the requested changes. Cleanup should not automatically beautify the scene or remove relevant product detail. Compare the source and edit for drift in hands, grip, face, props and framing.

## Choose the generation and editing route

- **Controlled opening or recurring identity:** prepare suitable frames and references. Check the tool's actual input combinations; an image described as the opening in a reference prompt is not a technically enforced starting frame.
- **Timed actions, camera moves or an invented montage:** use the chosen model's prompting skill. Seedance can be directed with successive shot descriptions and timestamps; inspect what it actually produces. When the user requests text-only generation, write the shot plan without attaching images or video. Keep this as the requested test rather than silently adding reference inputs.
- **Precise cuts, trims or crop changes:** use FFmpeg or an available video editor to select and assemble useful moments. Several short inserts can come from a longer source clip. Choose screen time by the brief: fast UGC often uses roughly one- to two-second inserts, while a readable demonstration or continuous reveal may need longer.
- **A close-to-wide reveal or changing viewpoint:** generate the needed camera motion when it reveals surroundings absent from the source or changes perspective. A digital zoom-out can be edited if an already-wide source contains the scene. For example, prompt a camera pulling back from a swimmer to reveal the pool when that wider view needs to be created.

Choose per shot. One successful manual montage does not establish a universal model or editing preference. For a reference adaptation, continue with [Using a reference video](using-a-reference-video.md); for a complete narrated ad, use [UGC video planning and structure](ugc-video-structure.md).

## Review and retain useful evidence

Inspect generated media against the requested action, continuity, realism, camera move and cut rhythm. Verify actual duration and dimensions before describing a result as meeting a duration or resolution request. A numeric value written in a prompt is not an output setting. Keep model-generated edits distinguishable from subsequent manual cuts or timing repairs, and state when review was limited to sampled frames.

Save source links or IDs, selected timestamps, frames, adaptations, prompts and output IDs with the job. Tag useful references by action, framing, setting, camera move and visual style so they can be found for another category. Add them to an existing shared reference store when available; do not imply that a reference-library service exists or treat temporary media URLs as durable originals. Record reusable lessons in the maintained skills, keeping job-specific artifacts and untested hypotheses clearly identified.
