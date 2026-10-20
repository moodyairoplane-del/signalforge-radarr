# SignalForge Radar — Manual Smoke-Test Checklist

Run this checklist against the deployed site after the production branch is updated. Record the date, browser, device width, and outcome for each item. Do not mark a test passed unless it was actually performed.

## Core page
- [ ] Homepage loads over HTTPS without a browser error.
- [ ] Header and primary calls to action render and navigate to the intended sections.
- [ ] No horizontal overflow at 320 px, 375 px, 768 px, and desktop width.
- [ ] Browser console has no uncaught JavaScript errors.

## Prospect explorer
- [ ] Search returns matching records and shows a useful empty state for a no-match query.
- [ ] Each filter can be applied and cleared; combined filters behave consistently.
- [ ] Sorting options produce the expected order.
- [ ] Open/close details controls work by mouse, touch, Enter, and Space.
- [ ] Focus indicator is visible when navigating with the keyboard.
- [ ] Source links open the expected destinations and use safe new-tab attributes where applicable.
- [ ] Counts and verification labels match the actual records shown.

## Outreach and calls to action
- [ ] Sample outreach content changes when its selector/tab changes.
- [ ] Copy action copies the currently displayed sample and provides visible feedback.
- [ ] Every CTA opens the expected destination or clearly explains that the feature is demo-only.
- [ ] No form suggests a message was sent unless a real submission endpoint confirms it.

## Data integrity and launch claims
- [ ] Every prospect and signal has a working source that supports the specific claim.
- [ ] Record research dates and freshness labels match the evidence.
- [ ] Unverified or stale entries are clearly flagged.
- [ ] Sample/demo data is visibly labeled; no sample is described as a live lead.
- [ ] Do not advertise live monitoring, accounts, saved searches, paid tiers, credits, or payments until those capabilities exist and are tested.

## Release gate
- [ ] Test results and any failures are recorded in the release notes.
- [ ] Production deployment is confirmed from the intended Git commit.
- [ ] Re-test the production URL after deployment; a successful GitHub commit alone does not prove the live site changed.

## Current known limitation
This checklist is a test plan, not evidence that the checks have already passed. The current implementation is a static demo; live research ingestion, persistent storage, authentication, membership/credits enforcement, and payment processing require separate implementation and verification.
