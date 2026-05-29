# Issue Triage Report - the-dev-pocket

## Overview
This document triages all open and recently closed GitHub issues to identify PR candidates.

---

## Triage Summary Table

| Issue | Type | Clarity | Repro Available | Existing PR? | Estimated Size | Risk | Selected? | Notes |
|-------|------|---------|-----------------|--------------|----------------|------|-----------|-------|
| #349 | bug, security | High | Partial | No | Large | **HIGH** | ❌ BLOCKED | Multiple PrismaClient instances causing connection pool exhaustion in API routes. Requires architectural fix to singleton pattern. Security-related. |
| #340 | bug, security | High | Yes | No | Medium | **HIGH** | ❌ BLOCKED | Upstash rate limiter adapter crashes protected API routes due to invalid SDK initialization. Security-related, could cause DoS. |
| #338 | bug | Medium | Partial | No | Small | Medium | ✅ YES | Newsletter subscription form throws error on submit. Client-side error handling issue. |
| #328 | security | High | N/A | No | Large | **HIGH** | ❌ BLOCKED | Add strict CSP + security headers. Requires careful header configuration, potential breaking changes. |
| #326 | design, beginner | High | Yes | No | Small | Low | ✅ YES | Improve testimonial section text visibility & readability. CSS/contrast fix. |
| #322 | bug, beginner | High | Yes | No | Small | Low | ✅ YES | Footer social media icons redirect to generic placeholder URLs. Simple href fix. |

---

## Detailed Triage Notes

### Issue #349: Multiple PrismaClient Instances Causing Connection Pool Exhaustion
**Labels:** bug, security  
**Priority:** High  
**Selected:** ❌ NO (BLOCKED)

**Reasoning:**
- **Type:** Backend infrastructure issue
- **Risk:** HIGH - This is a security-related bug that could lead to database connection exhaustion
- **Size:** Large - requires refactoring the Prisma singleton pattern across multiple files
- **Clarity:** High - clear problem description with multiple API routes affected
- **Existing PR:** None found
- **Safe to fix:** NO - This requires changes to how Prisma clients are initialized across the codebase, which could introduce breaking changes

**Blocker:** Security-sensitive database connection changes should be handled by maintainers with production access.

---

### Issue #340: Upstash Rate Limiter Adapter Crashes Protected API Routes
**Labels:** bug, security  
**Priority:** High  
**Selected:** ❌ NO (BLOCKED)

**Reasoning:**
- **Type:** Backend/infrastructure issue
- **Risk:** HIGH - Crashes protected API routes, potential DoS vector
- **Size:** Medium - requires proper initialization check and fallback logic
- **Clarity:** High - issue describes SDK initialization failure clearly
- **Existing PR:** None found
- **Safe to fix:** NO - Changes to rate limiting infrastructure could affect security posture

**Blocker:** Security-sensitive. The rate limiter protects all API routes - changes here could introduce vulnerabilities.

---

### Issue #338: Newsletter Subscription Form Throws Error on Submit
**Labels:** bug  
**Priority:** Medium  
**Selected:** ✅ YES

**Reasoning:**
- **Type:** Frontend bug
- **Risk:** MEDIUM - User-facing error, but no security implications
- **Size:** Small - likely a client-side validation or error handling issue
- **Clarity:** Medium - error occurs on submit but root cause unclear
- **Existing PR:** None found
- **Repro Available:** Partial - can test by submitting newsletter form

**Fix Approach:**
- Check client-side error handling in Footer.tsx newsletter form
- Verify API route returns proper error responses
- Add better error messaging for users

---

### Issue #328: Add Strict Content Security Policy (CSP) + Security Headers
**Labels:** security  
**Priority:** High  
**Selected:** ❌ NO (BLOCKED)

**Reasoning:**
- **Type:** Security hardening
- **Risk:** HIGH - CSP misconfiguration can break the entire application
- **Size:** Large - requires comprehensive header configuration
- **Clarity:** High - clear ask for CSP and security headers
- **Existing PR:** None found
- **Safe to fix:** NO - Security headers require careful testing across all pages

**Blocker:** CSP changes can have widespread impact and require thorough testing. Should be handled by maintainers.

---

### Issue #326: Improve Testimonial Section Text Visibility & Readability
**Labels:** design, level:beginner  
**Priority:** Low-Medium  
**Selected:** ✅ YES

**Reasoning:**
- **Type:** UI/design improvement
- **Risk:** LOW - Pure CSS/visibility changes, no functional impact
- **Size:** Small - CSS adjustments to text contrast, font size, or spacing
- **Clarity:** High - clearly describes visibility issue
- **Existing PR:** None found
- **Beginner Friendly:** Yes - labeled as beginner issue

**Fix Approach:**
- Check text color contrast in `app/components/Testimonials.tsx`
- Review `components/ui/animated-testimonials.tsx` for text styling
- Ensure WCAG 2.1 AA compliance for text contrast

---

### Issue #322: Footer Social Media Icons Redirect to Generic Placeholder URLs
**Labels:** bug, level:beginner  
**Priority:** Low  
**Selected:** ✅ YES

**Reasoning:**
- **Type:** Bug fix (broken links)
- **Risk:** LOW - No security or functional impact
- **Size:** Small - single file, 4 URL replacements
- **Clarity:** High - clear which URLs are wrong and where
- **Existing PR:** None found
- **Beginner Friendly:** Yes - labeled as beginner issue

**Fix Approach:**
- Update `app/components/Footer.tsx` lines 92, 101, 119, 128
- Replace `https://twitter.com` → proper Twitter/X URL
- Replace `https://linkedin.com` → proper LinkedIn URL
- Replace `https://discord.com` → proper Discord invite URL
- Replace `https://youtube.com` → proper YouTube channel URL

---

## Recently Closed Issues (Reference)

*No recently closed issues provided in context. Would need to fetch from GitHub API.*

---

## Summary

| Category | Count |
|----------|-------|
| Total Issues Triaged | 6 |
| Selected for PR | 3 |
| Blocked (Security) | 3 |
| Blocked (Size/Complexity) | 0 |

### Selected Issues
1. **#338** - Newsletter subscription form error (Small, frontend)
2. **#326** - Testimonial text visibility (Small, design/CSS)
3. **#322** - Footer social media placeholder URLs (Small, simple href fix)

### Blocked Issues
1. **#349** - PrismaClient connection pool (Security, large refactor)
2. **#340** - Upstash rate limiter crash (Security, infrastructure)
3. **#328** - CSP + security headers (Security, widespread impact)
