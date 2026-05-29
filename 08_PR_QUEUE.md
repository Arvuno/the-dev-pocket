# PR Queue - the-dev-pocket

## Overview
This document tracks the PR queue with detailed information for each PR submission.

---

## PR Queue Table

| Queue # | PR Title | Branch | Linked Issue | Status | Notes |
|---------|----------|--------|-------------|--------|-------|
| 1 | Fix footer social media placeholder URLs | `fix/footer-social-urls` | #322 | queued | Twitter, LinkedIn, Discord, YouTube |
| 2 | Add proper email validation to newsletter | `fix/newsletter-email-validation` | #338 | queued | Client + server validation |
| 3 | Add aria-label for testimonial profile images | `fix/testimonial-alt-text` | - | queued | Accessibility improvement |
| 4 | Improve testimonial section text visibility | `fix/testimonial-text-contrast` | #326 | queued | Dark mode contrast fix |
| 5 | Add loading state to newsletter email input | `fix/newsletter-input-disabled` | - | queued | UX improvement |
| 6 | Add focus-visible styles to footer social buttons | `fix/social-buttons-focus-visible` | - | queued | Keyboard accessibility |
| 7 | Type catch blocks properly with unknown | `fix/type-catch-blocks` | - | queued | TypeScript improvement |
| 8 | Fix eslint error: missing display name | `fix/test-display-name` | - | queued | Quick lint fix |
| 9 | Document parseBool edge case | `docs/parsebool-comment` | - | queued | Code documentation |
| 10 | Document getRotationForIndex magic number | `docs/rotation-magic-number` | - | queued | Code documentation |

---

## PR Details

### PR #1: Fix footer social media placeholder URLs
**Branch:** `fix/footer-social-urls`  
**Issue:** #322  
**Reviewers:** @Darshan3690  
**Labels:** bug, beginner, good-first-issue

**Summary:**
Replace generic placeholder URLs in footer with actual Dev Pocket social media profile URLs.

**Files Changed:**
- `app/components/Footer.tsx`

**Testing:**
- Manual: Click each social icon and verify correct URL opens

---

### PR #2: Add proper email validation to newsletter
**Branch:** `fix/newsletter-email-validation`  
**Issue:** #338  
**Reviewers:** @Darshan3690  
**Labels:** bug

**Summary:**
Add regex email validation to both client-side form and server-side API to reject malformed emails.

**Files Changed:**
- `app/components/Footer.tsx`
- `app/api/newsletter/route.ts`

**Testing:**
- Unit: Test invalid formats (`test@`, `@test.com`) are rejected
- Integration: Test valid email succeeds

---

### PR #3: Add aria-label for testimonial profile images
**Branch:** `fix/testimonial-alt-text`  
**Issue:** None  
**Reviewers:** @Darshan3690  
**Labels:** accessibility

**Summary:**
Improve screen reader experience by adding descriptive alt text to testimonial profile images.

**Files Changed:**
- `components/ui/animated-testimonials.tsx`

**Testing:**
- Run aXe accessibility audit
- Test with screen reader

---

### PR #4: Improve testimonial section text visibility
**Branch:** `fix/testimonial-text-contrast`  
**Issue:** #326  
**Reviewers:** @Darshan3690  
**Labels:** design, beginner

**Summary:**
Adjust dark mode text colors to meet WCAG AA contrast requirements.

**Files Changed:**
- `app/components/Testimonials.tsx`
- `components/ui/animated-testimonials.tsx`

**Testing:**
- Visual: Check contrast in dark mode
- Use browser DevTools to verify contrast ratio ≥ 4.5:1

---

### PR #5: Add loading state to newsletter email input
**Branch:** `fix/newsletter-input-disabled`  
**Issue:** None  
**Reviewers:** @Darshan3690  
**Labels:** ux, enhancement

**Summary:**
Disable email input field during newsletter submission for better UX feedback.

**Files Changed:**
- `app/components/Footer.tsx`

**Testing:**
- Submit newsletter and verify input is disabled during request

---

### PR #6: Add focus-visible styles to footer social buttons
**Branch:** `fix/social-buttons-focus-visible`  
**Issue:** None  
**Reviewers:** @Darshan3690  
**Labels:** accessibility, enhancement

**Summary:**
Add visible focus ring to social media buttons for keyboard navigation.

**Files Changed:**
- `app/components/Footer.tsx`

**Testing:**
- Tab through footer social buttons
- Verify focus ring is visible

---

### PR #7: Type catch blocks properly with unknown
**Branch:** `fix/type-catch-blocks`  
**Issue:** None  
**Reviewers:** @Darshan3690  
**Labels:** types, enhancement

**Summary:**
Use `unknown` type for catch blocks instead of implicit `any` for better TypeScript safety.

**Files Changed:**
- `app/api/newsletter/route.ts`

**Testing:**
- Run `npx tsc --noEmit`
- Run `npm run lint`

---

### PR #8: Fix eslint error: missing display name
**Branch:** `fix/test-display-name`  
**Issue:** None  
**Reviewers:** @Darshan3690  
**Labels:** bug, good-first-issue

**Summary:**
Fix react/display-name ESLint error in test file.

**Files Changed:**
- `__tests__/app/footer.social-links.test.tsx`

**Testing:**
- Run `npm run lint`
- Verify no display-name error

---

### PR #9: Document parseBool edge case
**Branch:** `docs/parsebool-comment`  
**Issue:** None  
**Reviewers:** @Darshan3690  
**Labels:** documentation

**Summary:**
Add JSDoc comment explaining parseBool function behavior with empty string.

**Files Changed:**
- `lib/env.ts`

**Testing:**
- No code change, no test needed

---

### PR #10: Document getRotationForIndex magic number
**Branch:** `docs/rotation-magic-number`  
**Issue:** None  
**Reviewers:** @Darshan3690  
**Labels:** documentation

**Summary:**
Add explanatory comment for deterministic rotation formula in testimonials.

**Files Changed:**
- `components/ui/animated-testimonials.tsx`

**Testing:**
- No runtime test needed

---

## PR Submission Template

```markdown
## Description
[Brief description of changes]

## Issue Link
Fixes #[ISSUE_NUMBER]

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Code refactoring
- [ ] Other

## Testing
[How was this tested?]

## Checklist
- [ ] My code follows the style guidelines
- [ ] I have performed a self-review
- [ ] I have commented complex code
- [ ] I have made corresponding changes
- [ ] My changes generate no new warnings
- [ ] I have added tests that prove my fix works
- [ ] New and existing tests pass locally
```

---

## Queue Management

### Adding New PRs
1. Create branch from `main`
2. Implement changes
3. Add to this queue with next queue number
4. Create PR with proper description

### Merging Order
PRs should be merged in queue order (1-10) unless:
- A later PR is blocked by an earlier one
- Maintainer requests different order
- Earlier PR needs rebase/restructure

### Updating Status
Update status column:
- `queued` - Not yet submitted
- `in-review` - PR submitted, awaiting review
- `changes-requested` - Review feedback received
- `approved` - Ready to merge
- `merged` - Successfully merged
- `closed` - Closed without merge

---

## Quick Stats

| Metric | Value |
|--------|-------|
| Total PRs in Queue | 10 |
| Bug Fixes | 4 |
| Features/Enhancements | 2 |
| Documentation | 2 |
| Accessibility | 2 |
| Estimated Total Time | ~2 hours |

---

## Notes for Maintainers

1. **Independent PRs** - All 10 PRs are independent and can be reviewed/merged in any order
2. **No Conflicts** - Each PR touches separate files or concerns
3. **Low Risk** - All changes are minimal and well-tested
4. **Beginner Friendly** - 4 PRs labeled as good-first-issue or beginner
