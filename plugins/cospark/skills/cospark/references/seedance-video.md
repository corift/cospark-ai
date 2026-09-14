# Seedance Video

Write the prompt like clear direction for someone filming the scene. Establish the subject, setting, and camera style, then describe what happens in order. Use concrete actions and ordinary language. Add detail where it helps the model make a specific choice.

For a useful starting point, read the relevant pattern in [references/examples.md](seedance-examples.md): a product reaction, a beach interaction, separate identity and motion references, or a Seedance 2.5 documentary sequence. Adapt the pattern to the request.

For B-roll framing, physical action, and review, read the shared [B-roll production guide](broll-production.md). For B-roll montages, use [Timed B-roll shot prompts](broll-shot-prompts.md): overall filming style, then timed shots with concrete composition, movement, continuity and explicit hard cuts. This structure is shared with Gemini; execution settings remain model-specific.

## Choose the generation

With Cospark, use `generate_video` for text, `generate_video_from_frames` for an exact starting frame, and `generate_video_with_references` for guiding media. Use `upload_media` for local inputs and `inspect_media` to review outputs. A complete talking-head script needing automatic planning and assembly belongs in [Cospark’s `generate_ugc_video` workflow](cospark-tools.md); preserve an explicitly requested Seedance model rather than silently switching workflows or models.

Honor the user's Seedance version. Otherwise, choose the newest Seedance version exposed by the tool that supports the requested inputs and duration, and state the choice. Check the tool schema for model IDs, reference syntax, durations, resolution, and audio support. A capability described in an example may not be available through the selected tool.

For a prompt-only request, return the prompt. When generation is requested, send the finished prompt directly. Add separate planning, replacement images, or edited assembly only when the task calls for them.

## Write the scene

Use a few paragraphs or simple headings when they help. A useful order is:

- **Subject and setting:** who is there, where they are, and the important appearance or objects. Include duration, aspect ratio, and whether the clip is one take or a sequence of shots.
- **Camera:** who is filming, where the camera starts, what it follows, and how the footage should feel.
- **Action:** what happens in order, how people react, and how the scene ends. Use timestamps when timing or shot changes matter.
- **Sound:** background sound, sounds caused by the action, exact dialogue, and whether music is wanted.

For a simple reaction, a short paragraph may be enough. For several shots, describe each shot and its camera behavior. Distinguish cuts that skip time from actions that must happen continuously. Leave enough time for the action and dialogue in each beat.

Describe small observable behavior: he notices the camera, gives a brief nod, and looks away; she takes a sip, pauses, and raises an eyebrow. Broad words such as "natural" or "realistic" can set the tone, but the actions should show what they mean.

When dialogue matters, quote each line once, name the speaker, and keep acting directions outside the quotation. Describe voice and delivery briefly if needed.

## Keep the scene coherent

When preparing realistic UGC character or shot references, follow [Creating realistic characters and shots](creating-a-realistic-character.md). Start from a real photo or exact video frame; change the face, clothing, and colors as requested while preserving the shot. For reference-based B-roll and product demos, existing media can be useful even when its product differs; adapt the product and necessary action through the prompt. Text-only montage requests can proceed without preparing reference images when invented scenes fit the brief.

Inspect supplied references before using them. Explain what each contributes when there could be ambiguity. One image can supply the person, setting, and opening composition together. If a video supplies only movement, say which subject should perform it and which parts of the video to leave out. Use reference labels such as `@Image 1` only when the tool supports them.

State what stays consistent: the person's appearance, clothing, important objects, and where people and objects start. Distinguish multiple people by clear visual traits and roles. Specify an object's holder or final location when it matters to the action.

Carry changes forward. Hair and clothing stay wet after rain; a dropped object stays where it lands until someone moves it. Describe physical consequences where useful: a planted foot grips before a turn, a hand presses into sand, or loose fabric follows a gust.

Match camera imperfections to the requested style and what is happening. A friend following someone may frame late or briefly lose focus. Moving from shade into sunlight may change exposure. Choose a few relevant details; polished footage may need none of these effects.

State what should stay true in plain language, such as "George stays seated throughout." Keep additional restrictions focused on likely problems in this scene.

## Review and generate

Read the prompt once for conflicting directions, overcrowded timing, and unexplained changes between shots. Check it against the user's references and exact dialogue.

Use the supplied media and preserve the user's chosen identity, clothing, setting, and composition, including any appearance changes already requested. Ask only before materially changing them beyond that scope. Start only the requested generations; do not retry a failed job if another attempt may incur cost without approval. Inspect completed media before claiming it followed the prompt when an inspection tool is available.
