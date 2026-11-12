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
- Full procedure: `.agents/skills/prompted-recall/SKILL.md` in `QNFO/agent-operating-system`.

## Design standard (DESIGN-STANDARD-1, owner directive 2026-11-09)

- Owner: "bad UI makes me sad ... when I see shitty design, it freezes me up ... Don't give me shitty design anywhere." Every page, dashboard, form, card or README layout an agent builds follows professional UI and UX practice.
- Fleet web pages use the shared design system in `QNFO/qnfo-workers` `_shared/design-system.js` (tokens, components, `dsHead`, `dsLint`), inlined with `_shared/inline-design-system.mjs`; `_shared/design-system.test.mjs` proves WCAG 2.2 AA contrast in light and dark and lints each adopter's rendered page. A page outside the fleet copies its tokens (colours, 16 px body text, 44 px tap size, 8 px spacing scale).
- The standard: one primary action per screen; a title, one status sentence, then the content; tap instead of type (Yes / No / Not sure as equal buttons, never free text for a choice); 44 px tap targets, 16 px body and field text, 14 px minimum for secondary text; secondary tools and links behind a disclosure, not crowded into the top bar; one accent colour, with colour only for good, warning and bad; loading, empty and error states each say what happens next; phone first, and tables scroll instead of crushing.
- Before calling UI work done, look at it: take a phone-width screenshot (390 px) in light and dark and fix what a person would trip over.

## Closed loops, no external input (CLOSED-LOOP-1, Rowan 2026-11-12)
- Rowan, verbatim: "Never assume that anything is needed externally ... documents and memories are useless. Don't rely on them. Everything must be translated into something that can be executed by code ... Don't ever assume that anything will ever be reviewed ... All of your loops must be closed by you."
- Assume nothing you produce is ever read, reviewed or decided by a person, and that no external input arrives: no owner decision, no human review, no reader. Every loop closes itself on an automated default, with its own check and rollback. Documents and memories are not storage or communication: a decision, plan or lesson lands as code, a policy value or a check that a loop executes.
- Never produce a document, report, owner-decision card or review request that no loop consumes. Resolve a blocker by building the capability. Only a credential, money, a legal signature or the owner's own account waits on the owner, marked `IDENTITY-BOUND:` with a default in effect that the loop runs on meanwhile.
- Enforced by `scripts/closed_loop_check.py` in `.github/workflows/closed-loop.yml` on every pull request: it fails when this rule is missing, when a new Markdown file has no code that reads it, or when an added line parks work on a person. Fleet copies: QNFO/qnfo-workers `scripts/closed_loop_guard.py` and `v_human_wait_states`; ultrastable `python3 -m foundation closedloop`.
