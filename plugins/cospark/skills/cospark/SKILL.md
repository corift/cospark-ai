---
name: cospark
description: Read this skill anytime you need to research, analyze, plan, create, inspect, or edit AI video ads with Cospark, including ad references, Gemini or Seedance prompts, UGC, B-roll, media generation, and timelines; not for unrelated coding or general copy edits.
---

> Retired: this guidance now lives in the Cospark MCP. Call the `read_docs` tool with no path and follow the docs it returns; they supersede this skill and its references.

# Cospark

Turn a product brief, script, or source media into the requested research, prompt, clip, or finished ad. Use this entrypoint to choose the relevant references. Supporting documents are parts of this skill, not separately installed skills.

## Select the workflow

| Request | Read |
| --- | --- |
| Research a product and develop ad concepts or a production plan | [Product to ads](references/product-to-ads.md) |
| Find and evaluate ad, social, or photographic references | [Reference discovery](references/reference-discovery-and-inspection.md) |
| Analyze one ad or compare several ads | [Ad analysis](references/ad-analysis.md) |
| Recreate or adapt an existing video | [Using a reference video](references/using-a-reference-video.md) |
| Create or adapt a realistic character, starting frame, or product shot | [Characters and shots](references/creating-a-realistic-character.md) |
| Write or generate a Gemini clip | [Gemini video](references/gemini-video.md); for spoken clips, [talking-head prompting](references/gemini-talking-head.md) |
| Write or generate a Seedance clip | [Seedance video](references/seedance-video.md) |
| Plan or generate B-roll and product inserts | [B-roll production](references/broll-production.md); for native montages, [timed shot prompts](references/broll-shot-prompts.md) |
| Produce or assemble a complete creator-led ad with supporting footage | [UGC video structure](references/ugc-video-structure.md) |
| Execute Cospark generation, search, uploads, voiceover, inspection, or timeline tools | [Cospark tools](references/cospark-tools.md) |

Combine only the rows needed for the request. A Gemini B-roll prompt needs Gemini and B-roll guidance, not the talking-head template or full product-research workflow. Read tool instructions when calling tools; a prompt-only request does not require an API call. Open examples only when they help compose the selected shot.

## Preserve the brief

The user's explicit instructions take precedence over these workflow defaults. Preserve requested models, exact dialogue, selected assets, and already approved decisions. Reuse available context; ask only for missing information that materially changes the work and continue independent steps where possible.

Keep the deliverable within the request: research returns sources and concepts; prompt writing returns the prompt; authorized production proceeds through generation and review. Planning or prompt writing alone does not authorize paid generations. Do not add a new approval gate to work already authorized.

For a new realistic UGC creator, follow [reference discovery](references/reference-discovery-and-inspection.md): find a real Instagram or TikTok video, choose a useful moment, and extract its frame. Then [make the new character](references/creating-a-realistic-character.md) in one edit from that original. Test the first spoken line before producing the remaining script when the setup is new and video production is authorized. Reuse suitable supplied assets or an already tested setup. Honor explicit text-only or no-reference requests.

Before generation, use the tool guide's run-tracking and retry rules. Preserve original run IDs and poll pending jobs; another charged retry requires authorization. Verify finished media before claiming its dialogue, action, or timing matches, and disclose missing output or inspection limits.
