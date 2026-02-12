# Jobs-Ive Design Architect

A skill for AI coding agents that transforms them into premium UI/UX architects guided by the design philosophies of Steve Jobs and Jony Ive. It audits every screen, component, and pixel of your app, then delivers a phased design plan for your approval before touching anything.

Works with Claude Code and any agent that supports the [Agent Skills specification](https://agentskills.io).

## Install

```bash
npx skills add vxcozy/jobs-ive-design-architect
```

---

## Table of Contents

- [Tutorial](#tutorial) — Get started with your first design audit
- [How-To Guides](#how-to-guides) — Accomplish specific tasks
- [Reference](#reference) — Complete specification of every feature
- [Explanation](#explanation) — Why it works this way

---

## Tutorial

This tutorial walks you through your first design audit from start to finish. By the end, you will have a phased design plan for your app and understand the full audit-approve-implement cycle.

### Prerequisites

You need:
- An AI coding agent with skills support (Claude Code, Cursor, Windsurf, Gemini CLI, etc.)
- A running frontend app (local dev server or deployed URL)
- The skill installed (`npx skills add vxcozy/jobs-ive-design-architect`)

### Step 1: Prepare your project files

The skill reads your project documentation before forming any opinion. Create these files in your project root if they don't exist:

```
DESIGN_SYSTEM.md      — your tokens, colors, typography, spacing, shadows, radii
APP_FLOW.md           — every screen, route, and user journey
PRD.md                — your feature requirements
```

These three are the most important. The skill also looks for `FRONTEND_GUIDELINES.md`, `TECH_STACK.md`, `progress.txt`, and `LESSONS.md`, but they are optional.

You don't need to write perfect documentation. Even rough notes give the skill context it wouldn't otherwise have.

### Step 2: Start your dev server

The skill walks through your app in a browser at three viewport sizes. Make sure your app is running locally:

```bash
npm run dev
```

### Step 3: Trigger the audit

Tell your agent:

```
audit the design
```

The skill activates automatically. It will:
1. Search your project for documentation files
2. Read and internalize each one
3. Walk through every screen at mobile (375px), tablet (768px), and desktop (1440px)
4. Run a 15-dimension visual audit on every screen
5. Apply the Jobs Filter to every element

This takes a few minutes depending on the size of your app.

### Step 4: Review the design plan

The skill presents a phased plan. It looks like this:

```
DESIGN AUDIT RESULTS:

Overall Assessment: The app is functional but the visual hierarchy
is flat — nothing guides the eye, and spacing is inconsistent
across breakpoints.

PHASE 1 — Critical
- Dashboard header: Title and subtitle are the same visual weight
  -> Title should be 24px semibold, subtitle 14px regular
  -> Users can't parse the page hierarchy in under 2 seconds

PHASE 2 — Refinement
- Card grid: 12px gap between cards feels cramped
  -> 24px gap per DESIGN_SYSTEM spacing-lg token
  -> Breathing room signals quality

PHASE 3 — Polish
- Page transitions: Hard cuts between routes
  -> 200ms fade transition on route change
  -> Movement signals responsiveness
```

Read through every item. You can approve, reject, reorder, or modify any recommendation.

### Step 5: Approve a phase

Tell the agent which phase to implement:

```
approve phase 1
```

The skill implements only what was approved, then presents the result for your review before moving on.

### Step 6: Review and continue

After each phase is implemented, the skill pauses for your review. If something doesn't feel right, say so — it will propose a refinement pass. When you're satisfied, approve the next phase.

You have completed your first design audit. The skill updated your `progress.txt` and `LESSONS.md` automatically.

---

## How-To Guides

### How to run a focused audit on a single screen

If you don't want a full-app audit, tell the agent which screen to focus on:

```
audit the design of the settings page
```

The skill scopes its audit to that screen only, still running all 15 dimensions and the Jobs Filter, but delivers a smaller, focused plan.

### How to audit without a running app

If you can't run the app locally, the skill falls back to reading your component files and stylesheets directly. Tell the agent:

```
audit the design — the app isn't running, review the code only
```

The audit will be less complete (no visual verification, no responsive walkthrough), but it still covers consistency, token usage, hierarchy in markup, and spacing patterns in stylesheets.

### How to use the skill with a Figma file

If you have Figma connected as an MCP server, the skill can pull design context and screenshots from your Figma file. Point it to the file:

```
audit the design using the Figma file at [URL]
```

The skill compares the Figma source of truth against the implemented UI and flags deviations.

### How to add custom audit dimensions

The skill audits 15 dimensions by default. If your project has domain-specific concerns (e.g., data visualization density, map rendering, video player states), tell the agent before triggering the audit:

```
when you audit the design, also check the chart components for
data-ink ratio and axis label readability
```

The skill incorporates your custom dimensions into the same phased plan structure.

### How to skip phases

If you only care about critical issues:

```
only show me phase 1 — skip refinement and polish
```

### How to get implementation notes for a different agent

The design plan includes implementation notes written for a build agent. If your build agent uses a different tool (Cursor, Copilot, Codex), the notes are tool-agnostic — they specify exact file paths, component names, properties, and old-to-new values. Copy the approved plan into your build agent's context.

---

## Reference

### Trigger phrases

The skill activates automatically when the agent detects any of these patterns:

| Phrase | Category |
|--------|----------|
| `audit the design` | Direct trigger |
| `design review` | Direct trigger |
| `UI audit` / `UX review` | Direct trigger |
| `make this feel premium` | Quality trigger |
| `this doesn't feel right` | Quality trigger |
| `polish the UI` | Quality trigger |
| `run the Jobs filter` | Philosophy trigger |
| `apply Ive's philosophy` | Philosophy trigger |
| `design architect mode` | Mode trigger |
| `review the design system` | System trigger |
| `check visual consistency` | System trigger |

Manual invocation: `/jobs-ive-design-architect`

### Project files

The skill searches for these files in order of importance:

| File | Required | Purpose |
|------|----------|---------|
| `DESIGN_SYSTEM.md` | Recommended | Tokens, colors, typography, spacing, shadows, border radii |
| `FRONTEND_GUIDELINES.md` | Optional | Component architecture, state management, file structure |
| `APP_FLOW.md` | Recommended | Every screen, route, and user journey in the app |
| `PRD.md` | Recommended | Feature requirements and specifications |
| `TECH_STACK.md` | Optional | Stack capabilities and constraints |
| `progress.txt` | Optional | Current build state |
| `LESSONS.md` | Optional | Design mistakes and corrections from past sessions |

Search pattern: `**/<FILENAME>*` (flexible matching, works in any directory depth).

If a file is missing, the skill reports which files were not found and asks whether to proceed or wait.

### Audit dimensions

Every screen is reviewed against these 15 dimensions:

| # | Dimension | What it checks |
|---|-----------|---------------|
| 1 | Visual Hierarchy | Eye landing point, element prominence, 2-second comprehension |
| 2 | Spacing & Rhythm | Whitespace consistency, breathing room, vertical rhythm |
| 3 | Typography | Type size hierarchy, competing weights, calm vs. chaotic feel |
| 4 | Color | Restraint, purpose, attention guidance, contrast accessibility |
| 5 | Alignment & Grid | Grid consistency, pixel precision, locked-in feel |
| 6 | Components | Cross-screen consistency, interactive obviousness, state coverage |
| 7 | Iconography | Style/weight/size consistency, cohesive set, meaning vs. decoration |
| 8 | Motion & Transitions | Purposeful transitions, unnecessary motion, responsiveness |
| 9 | Empty States | No-data appearance, intentional vs. broken, first-action guidance |
| 10 | Loading States | Skeleton/spinner consistency, alive vs. frozen feel |
| 11 | Error States | Message styling consistency, helpful vs. hostile tone |
| 12 | Dark Mode / Theming | Designed vs. inverted, token/shadow/contrast integrity |
| 13 | Density | Element justification, redundancy, earning screen space |
| 14 | Responsiveness | Mobile/tablet/desktop, touch targets, fluid adaptation |
| 15 | Accessibility | Keyboard nav, focus states, ARIA labels, contrast ratios, screen reader flow |

### The Jobs Filter

Applied to every element after the dimension audit:

| Question | Action |
|----------|--------|
| "Would a user need to be told this exists?" | If yes, redesign until obvious |
| "Can this be removed without losing meaning?" | If yes, remove it |
| "Does this feel inevitable?" | If no, it's not done |
| "Is this detail as refined as the ones users never see?" | The back of the fence gets painted too |
| "Say no to 1,000 things" | Cut good ideas to keep great ones |

### Design plan structure

The output follows this exact format:

```
DESIGN AUDIT RESULTS:

Overall Assessment: [1-2 sentences]

PHASE 1 — Critical
[Visual hierarchy, usability, responsiveness, or consistency issues
that actively hurt the experience]
- [Screen/Component]: [What's wrong] -> [What it should be] -> [Why]

PHASE 2 — Refinement
[Spacing, typography, color, alignment, iconography adjustments
that elevate the experience]
- [Screen/Component]: [What's wrong] -> [What it should be] -> [Why]

PHASE 3 — Polish
[Micro-interactions, transitions, empty states, loading states,
error states, dark mode, subtle details]
- [Screen/Component]: [What's wrong] -> [What it should be] -> [Why]

DESIGN_SYSTEM UPDATES REQUIRED:
- [New tokens, colors, spacing, typography, or components needed]

IMPLEMENTATION NOTES FOR BUILD AGENT:
- [Exact file, component, property, old value -> new value]
```

### Scope boundaries

| In scope | Out of scope |
|----------|-------------|
| Visual design, layout, spacing | Application logic, state management |
| Typography, color, interaction design | API calls, data models |
| Motion, accessibility | Feature additions/removals |
| DESIGN_SYSTEM token proposals | Backend structure |
| Component styling | Functionality changes of any kind |

If a design improvement requires a functionality change, the skill flags it and defers to the build agent.

### Post-implementation behavior

After each approved phase is implemented, the skill:

1. Updates `progress.txt` with changes made
2. Updates `LESSONS.md` with patterns or mistakes to remember
3. Verifies DESIGN_SYSTEM.md is current if tokens were added
4. Flags remaining approved-but-unimplemented phases
5. Presents before/after comparisons when possible

### Design rules

Eight rules govern every recommendation:

1. **Simplicity Is Architecture** — every element justifies its existence or it's clutter
2. **Consistency Is Non-Negotiable** — same component, same appearance, everywhere
3. **Hierarchy Drives Everything** — one primary action per screen, unmissable
4. **Alignment Is Precision** — every element on the grid, no pixel off
5. **Whitespace Is a Feature** — space is structure, not emptiness
6. **Design the Feeling** — calm, confident, quiet, responsive, intentional
7. **Responsive Is the Real Design** — mobile first, every viewport intentional
8. **No Cosmetic Fixes Without Structural Thinking** — every change has a design reason

---

## Explanation

### Why Jobs and Ive?

Steve Jobs and Jony Ive shared a design philosophy that is unusually well-suited to systematic application by an AI agent. Their approach was not about personal taste or trends. It was about a set of repeatable principles: remove everything that doesn't serve the user, make hierarchy unmistakable, obsess over details that most people will never consciously notice, and treat simplicity as an architectural decision rather than a stylistic preference.

These principles translate directly into auditable criteria. "Can this be removed without losing meaning?" is a yes/no question an agent can apply to every element on every screen. "Does the eye land where it should?" can be evaluated against visual weight, size, contrast, and position. The philosophy works as a skill because it is disciplined, not subjective.

### Why a phased plan instead of immediate fixes?

Design changes interact with each other. Fixing visual hierarchy on one screen might make a spacing issue on another screen more obvious. Changing a color token affects every component that references it.

The phased approach (Critical, Refinement, Polish) accomplishes three things:

1. **Priority triage.** Not all design issues are equal. A flat visual hierarchy that prevents users from finding the primary action is more urgent than a 4px spacing inconsistency.
2. **Controlled blast radius.** Implementing one phase at a time means you can review the cumulative effect before adding more changes. If Phase 1 makes Phase 2 items irrelevant, they get dropped.
3. **User control.** You approve each phase. You can reorder, cut, or modify any recommendation. The skill proposes; you decide.

### Why doesn't the skill just fix things automatically?

Design is contextual. The skill can identify that a button's visual weight doesn't match its functional importance, but it cannot know whether the business decision is to emphasize that button or de-emphasize it. It can detect that spacing is inconsistent, but the right spacing value depends on the density your users prefer.

The "propose everything, implement nothing without approval" discipline exists because design decisions have product implications. An AI agent that silently changes your UI is not an architect — it's a liability.

### Why read all those project files first?

A design audit without context produces generic advice. "Add more whitespace" and "use consistent spacing" are true for every app and helpful for none.

By reading your DESIGN_SYSTEM, APP_FLOW, PRD, and other files first, the skill understands: what tokens already exist and should be reused, what the user journeys are and which screens matter most, what features are required and cannot be visually deprioritized, and what the tech stack can actually support for motion and transitions.

The result is recommendations that reference your actual tokens, name your actual components, and respect your actual constraints.

### Why mobile-first auditing?

Mobile is the most constrained viewport. If the design works at 375px — hierarchy is clear, touch targets are sized for thumbs, spacing gives elements room to breathe — it almost always works at larger viewports with enhancements.

The reverse is not true. Designs that start at desktop frequently break at mobile: text gets too small, touch targets overlap, horizontal layouts stack awkwardly, and information density becomes overwhelming on a small screen.

The skill walks mobile, then tablet, then desktop, in that order, because that's the order in which design problems reveal themselves most honestly.

### Why exclude functionality changes?

Scope discipline is the difference between a useful tool and an unpredictable one. If a design skill can also modify application logic, every recommendation becomes a risk assessment: "will this change break something functional?"

By drawing a hard line — visual design only, functionality untouched — the skill can be trusted to operate without fear of side effects. If a design improvement genuinely requires a functionality change, the skill flags it explicitly and defers to the build agent. This separation of concerns mirrors how real design and engineering teams operate.
