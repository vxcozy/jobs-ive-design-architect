# Jobs-Ive Design Architect

A Claude Code skill that transforms the agent into a premium UI/UX architect guided by the design philosophies of Steve Jobs and Jony Ive.

## What It Does

- Audits every screen, component, and pixel of your app
- Reviews visual hierarchy, spacing, typography, color, alignment, motion, responsiveness, and accessibility
- Applies the "Jobs Filter" — removing anything that doesn't earn its place
- Delivers a phased design plan (Critical, Refinement, Polish) for your approval
- Implements changes surgically, only after approval, one phase at a time

## What It Does NOT Do

- Write features or application logic
- Touch state management, API calls, or data models
- Add, remove, or modify functionality
- Make changes without explicit approval

## How to Use

### Automatic triggers

The skill activates when you say things like:
- "audit the design"
- "design review" / "UI audit" / "UX review"
- "make this feel premium"
- "this doesn't feel right"
- "run the Jobs filter"
- "polish the UI"
- "check visual consistency"

### Manual invocation

Type `/jobs-ive-design-architect` in Claude Code.

## Recommended Project Files

For the best results, have these files in your project:

| File | Purpose |
|------|---------|
| `DESIGN_SYSTEM.md` | Tokens, colors, typography, spacing, shadows, radii |
| `FRONTEND_GUIDELINES.md` | Component engineering patterns, file structure |
| `APP_FLOW.md` | Every screen, route, and user journey |
| `PRD.md` | Feature requirements |
| `TECH_STACK.md` | Stack capabilities and constraints |
| `progress.txt` | Current build state |
| `LESSONS.md` | Design mistakes and corrections from past sessions |

The skill will search for these automatically. Missing files are flagged, not assumed.

## Workflow

1. Skill reads all project documentation
2. Walks through the live app at mobile (375px), tablet (768px), desktop (1440px)
3. Runs the full 15-dimension audit
4. Applies the Jobs Filter to every element
5. Presents a phased design plan
6. Waits for your approval before touching anything
7. Implements approved changes surgically
8. Presents results for review before moving to the next phase

## Version

1.0.0
