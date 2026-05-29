# PR Candidates - the-dev-pocket

## Overview
This document lists 15+ PR candidate ideas derived from issue triage and quality audit findings.

---

## PR Candidate Table

| candidate_id | title | category | linked_issue | source | problem | proposed_solution | target_files | test_plan | risk_level | expected_diff_size | merge_likelihood | maintainer_discussion_needed | selected |
|-------------|-------|----------|--------------|--------|---------|-------------------|--------------|-----------|------------|-------------------|------------------|-----------------------------|----------|
| CAND-001 | Fix footer social media placeholder URLs | bug-fix | #322 | Issue #322 | Footer has generic placeholder URLs for Twitter, LinkedIn, Discord, YouTube | Replace with actual Dev Pocket social media profile URLs | `app/components/Footer.tsx` | Manual: Click each social icon and verify correct URL | low | ~10 lines | high | no | ✅ |
| CAND-002 | Improve testimonial section text visibility | design | #326 | Issue #326 + Audit | Testimonial text may not meet WCAG AA contrast on dark mode | Adjust text color shade or add text-shadow for better contrast | `app/components/Testimonials.tsx`, `components/ui/animated-testimonials.tsx` | Visual: Compare contrast ratio in dark mode | low | ~15 lines | high | no | ✅ |
| CAND-003 | Add proper email validation to newsletter form | bug-fix | #338 | Issue #338 + Audit | Email validation `includes("@")` is too permissive | Add regex validation like `/^[^\s@]+@[^\s@]+\.[^\s@]+$/` | `app/components/Footer.tsx`, `app/api/newsletter/route.ts` | Unit: Test valid/invalid email formats | low | ~10 lines | high | no | ✅ |
| CAND-004 | Add aria-label for testimonial profile images | a11y | - | Audit | Alt text only contains name, not description | Change to `alt={`Profile photo of ${testimonial.name}`}` | `components/ui/animated-testimonials.tsx` | A11y: Screen reader test | low | ~5 lines | high | no | ✅ |
| CAND-005 | Add rate limiting to newsletter stats endpoint | security | - | Audit | GET /api/newsletter/stats has no rate limiting | Add same rate limiting as POST endpoint (3 req/hour) | `app/api/newsletter/route.ts` | Integration: Test rate limit headers | medium | ~20 lines | medium | no | ❌ |
| CAND-006 | Replace unsafe JSON type assertions in profile page | types | - | Audit | Using `as` assertions for social links bypasses type safety | Define proper interface and use type guards | `app/profile/[username]/page.tsx` | Type check: Ensure no runtime errors | medium | ~30 lines | high | no | ❌ |
| CAND-007 | Add .env.example template file | dx | - | Audit | No .env.example exists, variables documented only in README | Create .env.example with all env vars and placeholder values | `.env.example` (new) | Manual: Verify new contributors can use it | low | ~40 lines | high | no | ✅ |
| CAND-008 | Fix parseBool edge case documentation | docs | - | Audit | parseBool behavior with empty string is not documented | Add comment explaining that empty string = false | `lib/env.ts` | None needed | low | ~5 lines | high | no | ✅ |
| CAND-009 | Add loading state to newsletter email input | ux | - | Audit | Input doesn't visually indicate disabled state during submission | Add `disabled={isSubmitting}` to email input | `app/components/Footer.tsx` | Visual: Submit newsletter and verify input disabled | low | ~3 lines | high | no | ✅ |
| CAND-010 | Add toast announcement for newsletter errors | a11y | - | Audit | Newsletter errors not announced to screen readers | Add `role="alert"` to error toast or use aria-live | `lib/toast.tsx`, `app/components/Footer.tsx` | A11y: Test with screen reader | low | ~10 lines | high | no | ✅ |
| CAND-011 | Add focus-visible styles to footer social buttons | a11y | - | Audit | Social buttons may lack visible focus indicators | Add `focus-visible:ring` classes to social links | `app/components/Footer.tsx` | Manual: Tab through social links | low | ~8 lines | high | no | ✅ |
| CAND-012 | Type catch blocks properly with unknown | types | - | Audit | Error catch blocks use implicit `any` type | Change to `catch (error: unknown)` with type guards | `app/api/newsletter/route.ts`, `app/api/contact/route.ts` | Type check: Verify no type errors | low | ~15 lines | high | no | ✅ |
| CAND-013 | Document getRotationForIndex magic number | docs | - | Audit | Magic number 12345 in testimonial rotation has no explanation | Add comment explaining the deterministic rotation formula | `components/ui/animated-testimonials.tsx` | None needed | low | ~3 lines | high | no | ✅ |
| CAND-014 | Add missing security headers to API responses | security | #328 | Issue #328 (partial) | API responses lack security headers | Add X-Content-Type-Options, X-Frame-Options headers | `app/api/newsletter/route.ts` | Integration: Check response headers | medium | ~15 lines | medium | yes | ❌ |
| CAND-015 | Fix eslint error: missing display name | lint | - | Baseline | Component display name error in test file | Add displayName to anonymous component | `__tests__/app/footer.social-links.test.tsx` | Run lint: Verify no react/display-name error | low | ~3 lines | high | no | ✅ |
| CAND-016 | Update README broken links | docs | - | Baseline | README may have broken external links | Verify and fix all external links | `README.md` | Manual: Click all external links | low | ~10 lines | high | no | ✅ |
| CAND-017 | Add missing alt props from lint warnings | a11y | - | Baseline | 134 lint warnings include missing alt props | Add alt to all img elements or use Next/Image | Various | Run lint: Verify warnings reduced | medium | ~50 lines | high | no | ❌ |
| CAND-018 | Add loading skeleton to tech-feed page | ux | - | Audit | Tech-feed page lacks loading skeleton state | Add Suspense boundary with skeleton | `app/dashboard/tech-feed/page.tsx` | Visual: Navigate to page during load | low | ~30 lines | medium | no | ✅ |
| CAND-019 | Improve error message for newsletter duplicate | ux | - | Audit | "This email is already subscribed" could be clearer | Add suggestion to use unsubscribe flow | `app/api/newsletter/route.ts` | Manual: Test duplicate subscription | low | ~5 lines | high | no | ✅ |
| CAND-020 | Add keyboard navigation to testimonials | a11y | - | Audit | Testimonials lack keyboard controls | Add keyboard support for prev/next with arrow keys | `components/ui/animated-testimonials.tsx` | Manual: Navigate testimonials with keyboard | medium | ~25 lines | medium | no | ❌ |

---

## Candidate Details

### CAND-001: Fix footer social media placeholder URLs
**Problem:** Footer social icons link to generic `https://twitter.com`, `https://linkedin.com`, `https://discord.com`, `https://youtube.com` instead of actual Dev Pocket profiles.

**Solution:** Replace with real URLs:
- Twitter: `https://twitter.com/devpocket` (or similar official handle)
- LinkedIn: `https://linkedin.com/company/devpocket` (or similar)
- Discord: Specific invite link
- YouTube: Dev Pocket YouTube channel

**Files:** `app/components/Footer.tsx`

---

### CAND-002: Improve testimonial section text visibility
**Problem:** Testimonial quote text uses `text-gray-500 dark:text-neutral-300` which may not meet WCAG AA contrast on the dark gradient background.

**Solution:** 
1. Increase contrast by using `dark:text-neutral-200` or `dark:text-gray-200`
2. Or add text shadow for better readability
3. Verify contrast ratio meets 4.5:1

**Files:** `app/components/Testimonials.tsx`, `components/ui/animated-testimonials.tsx`

---

### CAND-003: Add proper email validation to newsletter form
**Problem:** Client validation `email.includes("@")` allows invalid emails like `test@` or `@test.com`.

**Solution:** Add regex validation:
```typescript
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
if (!email || !emailRegex.test(email)) {
  showError("Please enter a valid email address");
  return;
}
```

**Files:** `app/components/Footer.tsx` (client), `app/api/newsletter/route.ts` (server)

---

### CAND-004: Add aria-label for testimonial profile images
**Problem:** `alt={testimonial.name}` doesn't adequately describe profile photos.

**Solution:** Change to `alt={`Profile photo of ${testimonial.name}`}`

**Files:** `components/ui/animated-testimonials.tsx`

---

### CAND-005: Add rate limiting to newsletter stats endpoint
**Problem:** `GET /api/newsletter/stats` has no rate limiting, allowing enumeration.

**Solution:** Add same rate limiting as POST (3 requests/hour per IP).

**Files:** `app/api/newsletter/route.ts`

**Risk:** Medium - may affect legitimate users hitting stats frequently.

---

### CAND-006: Replace unsafe JSON type assertions in profile page
**Problem:** Multiple `as` assertions like `(profile.socialLinks as { github?: string })` bypass type safety.

**Solution:** Define proper interface and use type guards or optional chaining with defaults.

**Files:** `app/profile/[username]/page.tsx`

---

### CAND-007: Add .env.example template file
**Problem:** No `.env.example` exists, making onboarding harder.

**Solution:** Create `.env.example` with all required env vars and placeholder values.

**Files:** `.env.example` (new file)

---

### CAND-008: Fix parseBool edge case documentation
**Problem:** `parseBool("")` returns `false` but this isn't documented.

**Solution:** Add JSDoc comment explaining behavior.

**Files:** `lib/env.ts`

---

### CAND-009: Add loading state to newsletter email input
**Problem:** Email input doesn't visually disable during submission.

**Solution:** Add `disabled={isSubmitting}` to email input field.

**Files:** `app/components/Footer.tsx`

---

### CAND-010: Add toast announcement for newsletter errors
**Problem:** Error/success toasts not announced to screen readers.

**Solution:** Add `role="alert"` or `aria-live="polite"` to toast container when showing messages.

**Files:** `lib/toast.tsx`, `app/components/Footer.tsx`

---

### CAND-011: Add focus-visible styles to footer social buttons
**Problem:** Social buttons may lack visible focus indicators.

**Solution:** Add `focus-visible:ring-2 focus-visible:ring-blue-500` to button styles.

**Files:** `app/components/Footer.tsx`

---

### CAND-012: Type catch blocks properly with unknown
**Problem:** `catch (error)` uses implicit any type.

**Solution:** Change to `catch (error: unknown)` and use type guards.

**Files:** `app/api/newsletter/route.ts`, `app/api/contact/route.ts`

---

### CAND-013: Document getRotationForIndex magic number
**Problem:** Magic number 12345 in rotation calculation unexplained.

**Solution:** Add comment:
```typescript
// Deterministic rotation: seed ensures same rotation per index across renders
```

**Files:** `components/ui/animated-testimonials.tsx`

---

### CAND-014: Add missing security headers to API responses
**Problem:** API responses lack security headers.

**Solution:** Add `X-Content-Type-Options: nosniff`, `X-Frame-Options: DENY` headers.

**Files:** `app/api/newsletter/route.ts`

**Note:** Issue #328 requests full CSP - this is a partial fix.

---

### CAND-015: Fix eslint error: missing display name
**Problem:** Test file has `react/display-name` error.

**Solution:** Add displayName to anonymous component or name the component.

**Files:** `__tests__/app/footer.social-links.test.tsx`

---

### CAND-016: Update README broken links
**Problem:** README external links may be broken.

**Solution:** Verify all external links and update as needed.

**Files:** `README.md`

---

### CAND-017: Add missing alt props from lint warnings
**Problem:** 134 lint warnings include missing alt props.

**Solution:** Add alt to all `<img>` elements or convert to `<Image>`.

**Files:** Various

**Note:** This is a larger task - may need multiple PRs.

---

### CAND-018: Add loading skeleton to tech-feed page
**Problem:** Tech-feed page lacks loading skeleton.

**Solution:** Add Suspense boundary with skeleton component.

**Files:** `app/dashboard/tech-feed/page.tsx`

---

### CAND-019: Improve error message for newsletter duplicate
**Problem:** "This email is already subscribed" doesn't suggest unsubscribe.

**Solution:** Append "Use the unsubscribe link in any previous email to update your preferences."

**Files:** `app/api/newsletter/route.ts`

---

### CAND-020: Add keyboard navigation to testimonials
**Problem:** Testimonials can't be navigated via keyboard.

**Solution:** Add `onKeyDown` handlers for arrow keys.

**Files:** `components/ui/animated-testimonials.tsx`

---

## Summary

| Category | Total | Selected | Blocked |
|----------|-------|----------|---------|
| bug-fix | 3 | 3 | 0 |
| design | 1 | 1 | 0 |
| a11y | 5 | 4 | 1 |
| security | 2 | 0 | 2 |
| types | 2 | 1 | 1 |
| dx | 1 | 1 | 0 |
| docs | 2 | 2 | 0 |
| ux | 3 | 3 | 0 |
| lint | 1 | 1 | 0 |
| **TOTAL** | **20** | **16** | **4** |

### Selected for Top 10: CAND-001, CAND-002, CAND-003, CAND-004, CAND-007, CAND-008, CAND-009, CAND-010, CAND-011, CAND-012

### Blocked (needs maintainer discussion or risky):
- CAND-005: Rate limiting change
- CAND-006: Type assertion refactor
- CAND-014: Security headers (partial CSP)
- CAND-017: Large a11y task
- CAND-020: Keyboard navigation (medium complexity)
