---
name: launch-checklist
description: Use when the human asks to prepare a launch of a product, app, feature or site, or to review how a launch went. Checks measurement, legal pages, store listing, announcement, feedback channel and rollback plan, with an owner and evidence for every item.
disable-model-invocation: true
---

# Launch checklist

Most launch problems are not the product: nobody can tell if it worked, the legal pages are missing, the announcement promises something that is not live, users have nowhere to complain, and there is no way back. Check each item with evidence before the launch, and review the same list after it.

## Before starting

Ask for: what is launching, the date, the audience, the channels (site, stores, social, email, communities), the goal and its number, and who owns each area. Read `.agents/product-context.md` if it exists. Without a goal there is nothing to measure, so ask for one.

## Before the launch

Each item is pass, fail or not applicable, with the evidence (link, screenshot, command output). "Probably fine" is a fail.

**Measurement**
- The goal has a metric, a baseline and a target, and the event that measures it is firing in production or staging.
- Analytics and consent work together: no tracking before consent where consent is required.
- A dashboard or saved query shows the metric; someone owns reading it.

**Legal pages**
- Privacy policy, terms and cookie notice are published, linked from the product and up to date with what the product collects. Run `legal-pages-check`.
- Consent for emails or data collection is recorded, with an unsubscribe link in every marketing email.

**Store and pages**
- Store listings are approved and consistent with the app (`app-store-listing`).
- Landing page copy is final, every claim has proof (`landing-copy`), and the SEO audit passed.
- Links, forms, payments and sign-up work end to end on mobile and desktop.

**Announcement**
- The announcement describes only what is live on launch day.
- Each channel has its post or email drafted, reviewed (`post-review`) and approved by the owner. Nothing is sent or scheduled without that approval.
- Anyone quoted or named has agreed in writing.

**Feedback channel**
- Users know where to report problems (email, form, community), and someone watches it during the first days.
- Support answers for the likely first questions are ready.

**Rollback**
- There is a written way back: feature flag, previous build, previous page, or a pause on campaigns, with who decides and how long it takes.
- Known risks have a trigger ("if errors exceed X, roll back") decided before launch.

## After the launch

At the review date agreed before launch (for example day 1, day 7 and day 30):

- The metric against the target, with the data source.
- What users reported, grouped by theme, with counts.
- What broke and whether the rollback plan was used.
- Learnings, added to the Learnings section of `.agents/product-context.md`.
- Next three actions with owners.

## Rules

- This skill checks and reports. It never publishes, sends, schedules, spends money or changes prices.
- Do not mark an item as passed without evidence.
- A fail in measurement, legal pages or rollback is a blocker; say so plainly and let the owner decide.

## Output

```
Launch: what — date — goal (metric, baseline, target)
Blockers: - item — why — owner
Checklist: - area — item — pass | fail | n/a — evidence
After-launch review dates: ...
```

## Known failures

_Record real mistakes here with a date and the rule that prevents them._
