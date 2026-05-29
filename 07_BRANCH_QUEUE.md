# Branch Queue - the-dev-pocket

## Overview
This document tracks the ordered queue of branches to be created for the top 10 selected PRs.

## Branch Naming Convention
```
fix/<issue-description>   - Bug fixes
feat/<feature-name>        - New features
docs/<doc-improvement>    - Documentation improvements
chore/<maintenance-task>   - Maintenance/refactoring
```

---

## Branch Queue (Ordered)

| Queue # | Branch Name | PR Candidate | Priority | Status | Notes |
|---------|------------|-------------|----------|--------|-------|
| 1 | `fix/footer-social-urls` | CAND-001 | 1 | pending | Footer placeholder URLs |
| 2 | `fix/test-display-name` | CAND-015 | 6 | pending | ESLint react/display-name |
| 3 | `docs/parsebool-comment` | CAND-008 | 9 | pending | Document parseBool behavior |
| 4 | `docs/rotation-magic-number` | CAND-013 | 10 | pending | Document testimonial rotation |
| 5 | `fix/testimonial-alt-text` | CAND-004 | 3 | pending | aria-label for images |
| 6 | `fix/newsletter-input-disabled` | CAND-009 | 4 | pending | Add disabled state to input |
| 7 | `fix/social-buttons-focus-visible` | CAND-011 | 8 | pending | Focus ring for a11y |
| 8 | `fix/testimonial-text-contrast` | CAND-002 | 5 | pending | Dark mode contrast fix |
| 9 | `fix/newsletter-email-validation` | CAND-003 | 2 | pending | Proper email regex |
| 10 | `fix/type-catch-blocks` | CAND-012 | 7 | pending | Type unknown for catch |

---

## Branch Creation Commands

Run these commands in order:

```bash
# 1. Ensure main is up to date
git checkout main
git pull origin main

# 2. Branch for CAND-001 - Footer social URLs
git checkout -b fix/footer-social-urls
# ... implement CAND-001 ...

# 3. Branch for CAND-015 - Display name
git checkout main
git checkout -b fix/test-display-name
# ... implement CAND-015 ...

# 4. Branch for CAND-008 - parseBool comment
git checkout main
git checkout -b docs/parsebool-comment
# ... implement CAND-008 ...

# 5. Branch for CAND-013 - Rotation comment
git checkout main
git checkout -b docs/rotation-magic-number
# ... implement CAND-013 ...

# 6. Branch for CAND-004 - Testimonial alt text
git checkout main
git checkout -b fix/testimonial-alt-text
# ... implement CAND-004 ...

# 7. Branch for CAND-009 - Newsletter input disabled
git checkout main
git checkout -b fix/newsletter-input-disabled
# ... implement CAND-009 ...

# 8. Branch for CAND-011 - Social buttons focus
git checkout main
git checkout -b fix/social-buttons-focus-visible
# ... implement CAND-011 ...

# 9. Branch for CAND-002 - Testimonial contrast
git checkout main
git checkout -b fix/testimonial-text-contrast
# ... implement CAND-002 ...

# 10. Branch for CAND-003 - Newsletter email validation
git checkout main
git checkout -b fix/newsletter-email-validation
# ... implement CAND-003 ...

# 11. Branch for CAND-012 - Type catch blocks
git checkout main
git checkout -b fix/type-catch-blocks
# ... implement CAND-012 ...
```

---

## Dependency Notes

| Branch | Depends On | Notes |
|--------|-----------|-------|
| None | None | All PRs are independent, can be worked on in parallel |

---

## Queue Status Summary

| Status | Count |
|--------|-------|
| Pending | 10 |
| In Progress | 0 |
| Completed | 0 |
| Blocked | 0 |

---

## Quick Reference

| PR | Target File(s) | Estimated Time |
|----|----------------|----------------|
| CAND-001 | `app/components/Footer.tsx` | 15 min |
| CAND-015 | `__tests__/app/footer.social-links.test.tsx` | 10 min |
| CAND-008 | `lib/env.ts` | 5 min |
| CAND-013 | `components/ui/animated-testimonials.tsx` | 5 min |
| CAND-004 | `components/ui/animated-testimonials.tsx` | 10 min |
| CAND-009 | `app/components/Footer.tsx` | 10 min |
| CAND-011 | `app/components/Footer.tsx` | 15 min |
| CAND-002 | `app/components/Testimonials.tsx`, `components/ui/animated-testimonials.tsx` | 20 min |
| CAND-003 | `app/components/Footer.tsx`, `app/api/newsletter/route.ts` | 20 min |
| CAND-012 | `app/api/newsletter/route.ts` | 15 min |

**Total estimated implementation time:** ~2 hours
