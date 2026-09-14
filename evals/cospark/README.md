# Cospark skill checks

These fixtures test the skill's reference selection and response behavior without generating paid media. They are maintainer tests, not files loaded by the skill.

## Repeat the checks

1. Validate the plugin and skill metadata. Check that exactly one `SKILL.md` exists and that every linked Markdown file resolves inside the skill folder and is reachable from its entrypoint.
2. For each case in `cases.json`, start a fresh agent context with only the candidate name, description, entrypoint path, request, and any case context. Keep the `criteria` and previous results hidden from the agent. Restrict it to reading the candidate files; do not supply the README, prior conversation, or installed release.
3. Ask it to decide whether the skill applies, read only necessary references, and produce the actual response. For tool-dependent cases, request a clearly labeled simulated execution sequence. Disable external actions and media generation. Record files read, the response, missing inputs, and concerns.
4. Review the response against the held-out criteria. Check reference selection as well as output, particularly whether B-roll picks up talking-head instructions or unrelated requests activate Cospark.
5. Save the results and a content hash for each candidate file. Re-run affected cases after meaningful changes.

The initial run used fresh independent agents for the dialogue, montage, research, and full-ad cases. One additional agent evaluated the four boundary cases together from metadata, before loading applicable files. That boundary batch is weaker isolation than one fresh context per case; use separate contexts when checking subtle activation regressions.

These are constrained behavioral dry runs, not automatic production discovery tests or live MCP integration tests. No external tool execution is available to the test agents, so absence of paid calls alone is not evidence of a skill safeguard. Assess the written decisions and proposed actions. The tests do not establish generation quality, model timing accuracy, or compatibility with the current server. No before/after quality comparison was performed.
