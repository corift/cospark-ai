# Ad analysis

Use when the user wants an existing ad explained, taken apart, compared with other ads, or converted into reusable creative direction. This workflow analyzes evidence already stored by Cospark when possible; it does not require a new generation or another video-inspection pass.

## Retrieve the evidence

- When the user wants examples discovered and analyzed, call `search_ads` with the relevant query and filters, shortlist suitable results, then call `get_ad` for each ad being analyzed.
- When the user already supplied an ad ID returned by `search_ads`, begin with `get_ad`.
- For an indexed video, use the persisted `get_ad` evidence document: summary, hook, CTA, audio, transcript, semantic scenes, visible text, source metadata, and contact-sheet previews.
- For an image ad, use its `get_ad` evidence document and visually inspect the returned creative.
- Use `inspect_media` instead when the asset is generated, uploaded, external to the ad library, or the persisted record does not answer a material visual or timing question. Do not re-inspect an indexed video merely to restate analysis that `get_ad` already returned.

Search results are discovery summaries, not sufficient evidence for a detailed teardown. Fetch the selected ads before making content claims.

## Analyze what the ad does

Scale the response to the user's question. For an ordinary teardown, cover the useful parts below without forcing empty sections or turning every observation into a score.

### Hook

Name the opening mechanism and the channels that deliver it: picture, speech, visible text, or sound. Explain what question, conflict, result, demonstration, or curiosity gap the opening creates. Quote only words present in the transcript or visible text.

### Beat sheet

Group the evidence into functional beats such as hook, problem, turn or product introduction, demonstration, proof, offer, and CTA. Include timestamps when present. Not every ad uses every beat, and several stored semantic scenes may belong to one beat.

The video record labels semantic scene timing as approximate. Treat those timestamps as useful narrative boundaries, not verified edit points. Never convert scene count or selected-frame count into cut count, cuts per second, or shot length.

### Persuasion and offer

Identify:

- the audience and problem being framed;
- explicit product claims and benefits;
- how the product is demonstrated;
- proof mechanisms such as testimonials, app screens, before-and-after evidence, numbers, authority, or social proof;
- an actual offer, if present, such as a discount, bundle, gift, or trial;
- the CTA wording, timing, channel, and relationship to the concept.

Keep claims, proof, and offer separate. A website or instruction to click is a CTA, not an offer. Describe unsupported social-proof statements as claims rather than verified facts.

### Audio and muted viewing

Describe speaker arrangement, delivery mode, music, sound effects, and meaningful silence from the stored audio analysis. Assess muted viability by comparing what speech carries with the visible text and visual demonstration. State uncertainty when visible text may be selective rather than complete captions.

### What transfers

Separate two layers:

- **Reusable:** structure, hook mechanism, pacing at the semantic-beat level, promise shape, proof placement, demonstration pattern, and CTA construction.
- **Specific:** this product, person, price, claim, setting, season, brand treatment, or visual identity.

This distinction should help create the next ad without recommending a near-copy of the reference.

## Compare several ads

Apply the same questions to every ad before comparing them. Highlight shared structure and meaningful differences such as product-introduction timing, hook mechanism, proof, offer, CTA, audience, and audio dependence. When the user supplies performance labels, report patterns associated with those labels without claiming causation. Without performance data, describe composition and creative strategy only.

## Measurement boundaries

Safe derived measurements include total duration, approximate beat duration, transcript word count, and approximate speaking rate. Product, brand, face, or text appearance times may be reported as approximate only when the stored scenes support them.

Do not invent or estimate:

- hard-cut timestamps, cuts per second, or shortest, median, and longest shots;
- transition types;
- frame-accurate first appearances;
- spend, ROAS, retention, conversion rate, hook rate, or reasons an ad won.

Name missing measurements plainly. Recommend a fresh media inspection only when it can actually resolve the user's question; ordinary strategic analysis should use the persisted ad record.
