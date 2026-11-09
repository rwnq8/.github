# Agent operating agreement

This repository follows the Quniverse unified agent doctrine:
https://github.com/QNFO/agent-operating-system/blob/main/GLOBAL-AGENTS.md

Fast loop: inspect the failure, make the smallest complete fix, run the
project's checks, and leave a reviewable branch/commit/PR with verification
evidence. Preserve existing conventions; never commit secrets or weaken
security controls to pass a task. Production deploy, credentials, DNS, billing,
permission escalation, and irreversible deletion stay human-gated unless this
repository's `.agentops/authority.yaml` explicitly enables them.

## 9. Ask the owner with prompted recall (PROMPTED-RECALL-1, owner directive 2026-11-09)
- When you need something only the owner knows (past work, experience, preferences, facts about their life), ask yes/no or multiple-choice questions: two to four concrete options plus "Not sure". Never ask for a typed free-form answer or recall from scratch.
- Make each option specific (job, employer, year, system, document) so a yes jogs memory: "At DVRPC, 2005 to 2008, did you run the regional travel model?", not "Tell me about your modeling work".
- Use tap cards, checkboxes or a short numbered batch. Ask whenever you are unsure instead of guessing or leaving a gap.
- Act on each answer at once: a yes goes into the record that needs it (resume, brand doc `rwnq8/resume` `docs/BRAND.md`, profile, application) marked "confirmed by owner, <date>"; a no removes the claim; "Not sure" keeps it out. Record answers so the same question is never asked twice.
- Before every job application, compare the posting's requirements with the resume and ask a prompted-recall question for each gap before tailoring.
- Full procedure: `.agents/skills/prompted-recall/SKILL.md` in `rwnq8/agent-operating-system`.
