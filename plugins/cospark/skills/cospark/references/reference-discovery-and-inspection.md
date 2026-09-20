# Finding and choosing reference videos

For realistic UGC, start with a real creator video. Look for someone filmed in an ordinary setting, with believable light, a useful camera angle, and an action that fits the script. Use a supplied or saved reference when it already works.

## 1. Search for the situation

Turn the idea into something a person would actually say or do. Search Instagram Reels and TikTok for that situation and the filming format. A creator does not need to mention the target product to provide a good reference.

For a cooking app without app-demo footage, useful search directions include:

| Search phrase | What to look for |
| --- | --- |
| “let's cook dinner” | Someone speaking to the phone before cooking |
| “dinner in 20 minutes” | A real reason for urgency and a casual home setting |
| “what I'm making for dinner” | A visible creator followed by cooking coverage |
| “don't know what to cook” | A spoken problem the app could help solve |

These are example queries, not a record of the exact searches used in an earlier job. Vary the wording when results are mostly recipes, music montages, or screen recordings. Once a creator has the right filming style, inspect nearby reels on their profile.

Choose each reference for its job. Talking-head footage supplies the presenter setup; cooking footage supplies supporting shots; a real app recording supplies product behavior. A popular food montage may be useful B-roll but cannot supply a speaking creator frame. When no app recording is available, plan a spoken benefit with relevant everyday activity rather than inventing a working app demo.

## 2. Use ScrapeCreators for organic discovery

Use the connected ScrapeCreators MCP when available. Check its current schema before calling it; tool versions and fields can change.

| Task | Tool |
| --- | --- |
| Find Instagram reels by phrase | `v2_instagram_reels_search` with `query` |
| Look through a promising creator's reels | `v1_instagram_user_reels` with `handle` or `user_id` |
| Fetch a selected reel's caption and video URL | `v1_instagram_post` with its original `url` |
| Find TikTok videos by phrase | `v1_tiktok_search_keyword` with `query` |
| Fetch a selected TikTok and optional transcript | `v2_tiktok_video` with its original `url` |

Instagram reel search uses Google-indexed results, so it is incomplete and may miss recent posts. Follow up on promising profiles. The user-reels endpoint does not return captions; fetch individual posts when their wording matters. On TikTok, relevance is a useful starting sort for finding a particular shot; popularity is optional context. Remove unnecessarily narrow date filters when looking for an evergreen filming setup.

If ScrapeCreators is unavailable, use another connected social-search tool or browser search, such as `site:instagram.com/reel/ "let's cook dinner"`. Open and verify candidates before recommending them. Do not invent search endpoints or describe Cospark's ad library as a general Instagram search.

Use Cospark `search_ads` for ad references and `list_ad_brands` before filtering by advertiser. Organic videos are especially useful for natural creator setups; ads are useful for scripts, product demonstrations, and edit structure.

## 3. Watch before choosing

Shortlist from previews, then inspect the strongest videos. For an external reel, pass its playable media URL to Cospark `inspect_media` and view the returned contact sheets. For an indexed Cospark ad, use `get_ad` and its existing analysis first. Watch the relevant passage when speech, gestures, object handling, or cuts affect the decision. A caption or transcript cannot establish what the shot looks like.

For a creator frame, check:

- **Face and posture:** a visible face, a natural speaking expression, and hands that can support the intended gesture.
- **Light:** skin detail remains visible in the brightest parts of the face. Avoid large blown-out white patches.
- **Setting:** an ordinary room with some depth and believable background detail.
- **Camera:** useful distance and framing, with the texture of real phone footage.
- **Obstructions:** little motion blur and preferably no captions over the face, hands, or important objects.
- **Script fit:** a believable reason for the person to be speaking in that setting.

Rank visual suitability separately from topic relevance. Views and likes can help narrow a search, but they do not prove a frame will work or an ad will convert.

For B-roll, choose a useful shot rather than searching only for an exact match to the entire ad. A different product or topic can still supply the right angle, light, hand placement, surroundings or activity. Start with the selected creator's video and nearby reels, then broaden the search when they lack the shot you need. When several shots should feel recorded by one person, compare their rooms, light, surfaces, and filming distance together. Related footage often fits better than unrelated attractive images, but using one source is not a requirement.

Extract those frames and follow [B-roll production](broll-production.md) to change only what the new ad needs, animate the shots, and cut their best moments together.

## 4. Save the useful moment

Keep the original post link, creator handle, useful time range, and a short reason for choosing it in the project's research document. A compact shortlist is enough; build a gallery only when requested. Keep previews or playable links where supported, and label anything you could not inspect.

Extract the actual individual frame from the selected passage at the best available resolution, preferably as PNG. A lossless export avoids another compression step; it cannot restore missing source detail. Record the timestamp. Use contact sheets to choose moments, never as image-edit inputs. A reel cover can differ from the video: label it as a cover if that is all you have, and do not invent a frame timestamp.

Retain the original post URL even when a temporary CDN video URL works. Refresh expired media through the source provider. Upload the selected frame to Cospark when a reusable file ID is needed.

## 5. Make the new creator, then test the performance

Follow [Creating a realistic character](creating-a-realistic-character.md). Make all intended changes in one edit from the original frame. Review the new image beside its source before animating it.

For a new presenter setup, use an authorized short first-line test to check the face, voice, gestures, pace, and lighting in motion. Once it works, reuse that frame and direction for the remaining script. See [UGC video planning](ugc-video-structure.md). Research or image-only requests end with those deliverables; an end-to-end request can continue without another approval stage.

For an edited sequence, record shot order, action, approximate duration, and camera or crop changes. Confirm cuts with playback or adjacent frames before calling their timing exact. Generate camera moves when they reveal a new view; use an editor for precise trims, cuts, and crops of footage that already exists.

## Example: a cooking-app creator

In the September 2026 trial, [Cierra Neal's dinner reel](https://www.instagram.com/reel/DTQcDHMEXOk/) worked as a reference because its opening six seconds showed someone speaking to the phone in an ordinary home hallway, with natural household activity and a reason to hurry dinner. The product did not need an on-screen app demo for that setup to make sense.

The useful pattern is the immediate situation, natural light, and speaking frame. The creator's identity and incidental family members are not requirements for the new ad. This was an approved creative reference, not evidence of conversion performance.
