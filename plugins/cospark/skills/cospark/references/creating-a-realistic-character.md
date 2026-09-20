# Creating a realistic character

Start with a good frame from a real video. Keep the light, camera angle, background, and small imperfections that make it look like someone recorded it on their phone. Replace the person and the details the brief asks to change.

## 1. Choose a useful source frame

Use a suitable image the user supplied, or follow [Finding reference videos](reference-discovery-and-inspection.md) to find a creator on Instagram or TikTok. Pick the frame for the intended scene: a visible speaking face for talking-head footage, or clear hands and objects for an action shot.

Look for natural skin texture, facial highlights with detail, a relaxed pose, and a real room with some depth. Avoid blurred hands, awkward expressions, and captions covering important features. Use the individual frame at its original quality, not a contact-sheet crop or a written recreation of the scene. Honor an explicit request for text-only generation without adding a reference.

## 2. Say what should change

Start with a short prompt. The image already shows the room, light, pose, and framing; you do not need to describe all of them again.

> Keep everything about this image the same, including the lighting, framing, background, pose, and expression. Replace the foreground woman with a clearly different fictional woman in her early 30s, with a similar skin-tone lightness to the source. She must not resemble the source woman. Remove all overlaid text, captions, emojis, watermarks, and interface elements.

Adjust the person description to the brief. Change clothing, accessories, props, or the background only when wanted. If the user asks for a completely text-free image, add that requirement; otherwise preserve writing that belongs on the actual product or app screen. Removing a social caption does not mean erasing the product UI.

When several details need changing, put them in the same prompt:

> Also change her top to a forest-green T-shirt, add an oatmeal kitchen apron and small asymmetric earrings, and replace the mug with the supplied product.

Use only the details that help this scene. A plant, necklace, earbud, or microphone is optional. Keep sound capture believable for the shot: close phone framing can work without a visible microphone, while an interview may need one.

## 3. Make each attempt from the original

Include all intended changes in one generation. If the result needs another attempt, revise the prompt and use the original source again. Do not edit a generated face, then edit that result to add earrings, then edit it again to change the background. Repeated edits can soften detail and move the image further from the source.

For an authorized batch, send the original frame into every independent variant. Keep the prompts and results together so the user can compare them.

Use the user's chosen image model and tool. For Nano Banana through Cospark, call `generate_image` with the source in `references`: `nano-banana-pro` selects Pro, and `nano-banana-2` selects Nano Banana 2 / Flash. Check the connected schema for supported settings. Read [Cospark tools](cospark-tools.md) for uploads, returned assets, and run handling.

## 4. Preserve the source lighting

Keep exposure, shadow direction, and the ordinary phone-camera finish. A brighter face or smoother skin can make the edit look less believable even when the new identity is good.

When casting is flexible, prefer a new person with roughly the same skin-tone lightness as the source. Large complexion changes have been less reliable in our reference edits. Skin tone and ethnicity are separate attributes; a different identity or ethnicity does not require a large change in lightness. If the brief calls for a substantially different complexion, find a closer source rather than changing the requested casting.

Check for added light from the front. If the edit has brightened the face, a focused correction is:

> Do not add frontal fill light or brighten the face. Preserve the source image's facial exposure, lighting direction, and natural shadows.

Both Pro and Flash added some frontal brightness in the September 2026 cooking-frame comparison; Pro was more restrained in that pair. This is a reason to inspect the result, not a general ranking of the models. The cause of the complexion-related drift has not been isolated.

## 5. Compare the source and edit

Show both images when the user is choosing a creator. Check:

- The new person is clearly different from the source person.
- The expression, gaze, body pose, and hand positions still fit the shot.
- The face has not gained unwanted brightness, smoothing, or studio lighting.
- The room, crop, props, and product details remain correct.
- Requested text cleanup is complete and hands or objects have no obvious distortions.

If one detail drifts, name that detail in the next prompt. A longer prompt is useful when it fixes a specific miss; it is not automatically better. A good-looking still also needs a short motion test before relying on it for a new video setup.

## Keep one character across several shots

First establish the new person in one clear frame. For each additional shot, attach its own original frame as Image 1 and the selected creator image as Image 2:

> Edit Image 1. Use Image 2 for the person's facial identity only. Preserve Image 1's expression, gaze, hairstyle, pose, lighting, camera angle, and setting. [Add the changes needed for this shot.]

The generated identity image is a second reference, not a replacement for the original shot. Do not use the previous edited shot as the next shot's source. Keep an exercise grimace, a downward glance, or a tied-back hairstyle when the action calls for it. Describe outfit changes separately.

## Adapt product shots and B-roll

A reference from another category can supply the camera angle, light, hand placement, or action. Attach the target product separately for its shape, packaging, branding, or screen content, and the selected creator image when identity matters. State what each reference supplies.

For example, a bottle presentation can guide a different bottle shot, but the grip may need to change to fit the new object. An app reference can supply the phone angle; use real target-app captures for accurate UI. Keep changes in one edit from the original frame.

For animation, pass the selected image as the actual starting frame when supported. When using several reference images, describe their roles and follow the model's supported inputs. Continue with [UGC video planning](ugc-video-structure.md) for the first-line test and remaining script.
