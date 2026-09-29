---
name: comp-analysis
description: Run the ig-competitive-analyst agent on a named company. It researches the target and shortlists competitors, asks the user which competitors to use, then produces the full Word thesis and Excel audit workbook, the same output as /ig-comp-analysis. Use when the user runs /comp-analysis or asks for a competitive analysis done "by the agent".
---

# /comp-analysis: orchestrate the ig-competitive-analyst agent

The user's request (arguments or pasted brief) is: $ARGUMENTS

Follow these steps in order. Don't skip the competitor question: the user wants to choose the competitors before the report is finished.

1. **Get the brief.** If the request doesn't at least name a target company, ask for it and point the user to `prompts/competitive-analysis-request.md` for the full template. Everything else in the template is optional.

2. **Stage 1: research and shortlist.** Launch the `ig-competitive-analyst` agent with `run_in_background: false`. Pass it the full brief verbatim, prefixed with `STAGE 1 – research and shortlist only.` Wait for it to return a `COMPETITOR CHECKPOINT`.

3. **Ask the user which competitors to use.** Show the checkpoint's candidate-peer table and the agent's recommendation. Then use `AskUserQuestion` with:
   - Question 1 (multiSelect): "Which competitors should be in the peer set?" List the candidates, and put the agent's recommended set first, labelled "(Recommended)". AskUserQuestion allows at most 4 options; if there are more than 4 candidates, list the recommended ones and let "Other" take additions.
   - Question 2 (multiSelect): "Which competitors go into the head-to-head growth-strategy matrix (default 3)?"
   - If the brief listed must-include or must-exclude competitors, honour them and mention it.
   Don't continue until the user has answered.

4. **Stage 2: full report.** Continue the same agent with SendMessage if it's still available; otherwise launch a fresh `ig-competitive-analyst`. Send:
   ```
   CONFIRMED COMPETITORS: <Target>
   Peer set: <user's choice>
   Growth-matrix competitors: <user's choice>
   Exclusions / notes: <anything the user said>
   Working folder: reports/<slug>/working/
   ```
   This stage takes a while. Run it in the background and tell the user it's under way.

5. **Deliver.** When the agent's Completion Summary comes back, check that the two files exist, send them to the user with SendUserFile (`display: attach`), and relay the verdict, Critical/Warning audit findings and the N/D list. Commit the `reports/<slug>/` folder only if the user asks.
