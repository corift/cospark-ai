# Creating realistic characters and shots

For realistic UGC, preserve the photographic evidence of a real shot. The starting frame should feel like a moment from someone's video, including its ordinary lighting, framing, and imperfections.

## Choose the source

For searching and shortlisting new material, use [Reference discovery and inspection](reference-discovery-and-inspection.md). The frame-based approach here applies to reference-led production; honor an explicit text-only or no-image generation test without adding media inputs.

- Use the user's supplied photo or exact video frame when suitable. For a video, inspect it to choose the moment, then obtain that actual single frame at the best available quality.
- If no suitable source is supplied, find an existing photograph or video with useful framing, action, and lighting, for example on Pinterest or in an ad library. The product or category does not have to match. Inspect the selected image and retain its source link.
- A contact sheet helps select a shot. Pass the actual selected photo or individual video frame into image editing, rather than recreating it from a written description or using the entire grid as the editing target.
- Choose a frame that can support the intended action. Talking-only A-roll needs a visible face and a plausible speaking pose; B-roll needs the hands, objects, and action framed appropriately. Preserve a specifically requested opening even when it differs from this preference.

## Change the character, preserve the shot

When the user asks for a new character, the default changes are **face, clothing, and colors**. Make the facial identity distinctly different while retaining the source expression and gaze. Keep the original body pose, hand positions, object grip, proportions, camera angle, camera distance, crop, room, objects, lighting direction, shadows, depth of field, and photographic texture.

Change outfit and requested colors without rebuilding the scene or replacing its natural lighting with a new color grade. Preserve hairstyle and other details unless included in the requested changes. If the user asks only to remove UI, preserve the original person and clothing too.

Use an image-editing tool with the source image attached; in Codex, use the built-in ImageGen tool. Remove browser chrome and captions when a clean starting frame is needed. Preserve natural softness, uneven light, and incidental background detail. Avoid beauty retouching, idealized symmetry, studio lighting, or a generic polished AI portrait.

For a character-only edit, preserve the scene. When adapting an ad to a different product, change the product, branding, props, and action as needed for that brief while retaining the source shot's useful visual structure. For multiple shots, use each original shot's exact frame as its composition reference and the chosen new character image as the identity reference.

## Recreate a video with one new person

This sequence worked well for a source-led character recreation:

1. Map the source shots and select individual frames that cover useful views of the person. Retain source timestamps where available.
2. Edit one clear face frame to establish the new identity. Keep its original scene and photographic texture; change the face, clothing, and requested colors.
3. For every additional shot, attach **its own original frame as Image 1** and **the new character frame as Image 2**. Reuse that character reference across the set instead of deriving each identity from the previous edited shot.
4. State the reference roles explicitly: “Edit Image 1. Image 2 supplies facial identity only. Preserve Image 1's expression, gaze, hairstyle, pose, camera, lighting, and setting.” Describe clothing changes separately for that shot.
5. Compare each original and edit side by side. Save the selected frames, source mapping, and prompts together so the approach can be repeated.

The source action takes priority over the identity reference's expression: keep an exercise grimace, a downward watch-check gaze, or a face hidden behind a phone. Do not borrow the character reference's loose hairstyle for a source shot with a ponytail. Preserve phone interfaces and other in-scene product details unless the brief asks to change them; removing platform overlays does not mean removing the product UI.

For a request limited to a plan or reference images, deliver those assets and stop before video generation.

## B-roll and product shots

Use existing media as the default reference for B-roll, demonstrations, close-ups, inserts, and additional coverage too. Do not start these shots from text alone merely because the target product differs from the reference. Choose the reference for its shot design and physical action, then attach its exact frame to the image edit.

Separate the reference roles: the existing shot supplies composition, camera angle, distance, lighting, hand placement, and action; the target product image supplies its shape, packaging, branding, or interface; the selected character image supplies identity when a person appears. Preserve what transfers naturally and adjust the prompt for what must change. Adapt the grip and movement when the new object requires it, rather than forcing an implausible exact pose.

For example, a handheld skincare-bottle shot can guide a drink-bottle shot: keep the camera position, light, background, and presentation gesture, but replace the bottle and label with the target product and adjust the grip to fit. A different app demo can supply phone angle and hand placement while the screen is replaced with the target app.

When video generation is requested, create clean adapted frames first and use them to generate the new footage. This does not require passing the original video into the video model. Keep the source product, branding, and dialogue out of the result unless the brief calls for them.

## Example edit direction

> Edit this exact frame to depict a distinctly different adult person. Change the facial identity to [new face description], the clothing to [outfit], and the colors to [requested colors]. Preserve the original expression, gaze, head angle, body pose, hands, object positions and grip, camera angle, framing, background, lighting, shadows, and photographic texture. Keep the candid source-video appearance. Remove the overlaid UI and captions. Do not redesign the scene or turn it into a polished portrait.

Fill in only the changes needed for the request; do not add appearance changes to a cleanup-only task.

## Check before animation

Compare the edit with the source: the intended appearance changes should be clear, and the rest should still read as the same shot. Check the face, hands, grip, objects, and background for drift. A prettier image is not a better starting frame if it loses the source's realism or cannot support the action.

Pass the edited image as the actual start frame when the video workflow supports exact starting frames. For a sequence guided by multiple images, label the identity and shot roles explicitly.
