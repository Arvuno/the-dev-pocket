# The Dev Pocket - Repository Map

## 1. Project Overview

**Name**: The Dev Pocket  
**Type**: Developer Resources Hub (Web Application)  
**Description**: A curated collection of learning resources, interactive tools, roadmaps, and career guidance for developers. Features AI-powered recommendations, quiz systems, resume building, and community features.

**Repository**: [Darshan3690/The-Dev-Pocket](https://github.com/Darshan3690/The-Dev-Pocket)  
**License**: MIT (Copyright 2025 Darshan Rajput)

---

## 2. Tech Stack

### Framework & Language
- **Framework**: Next.js 16.1.1 (App Router)
- **Language**: TypeScript 5.9.3
- **Runtime**: Node.js >=20.9.0

### Frontend
- **UI Library**: React 19.1.0, React DOM 19.1.0
- **Styling**: Tailwind CSS 4.1.18, PostCSS
- **Components**: Radix UI (multiple packages), class-variance-authority
- **Icons**: Lucide React, React Icons, Tabler Icons
- **Animations**: Framer Motion 12.23.19
- **Theming**: next-themes (dark mode support)

### Backend & Database
- **API**: Next.js API Routes + tRPC
- **ORM**: Prisma 6.19.1
- **Database**: PostgreSQL (Supabase)
- **Auth**: Clerk (@clerk/nextjs 6.36.5)

### Utilities & Libraries
- **Rate Limiting**: @upstash/ratelimit 2.0.7, @upstash/redis 1.36.0
- **Charts**: Recharts 3.7.0, React Flow 11.11.4, OGL 1.0.11
- **Calendar**: react-big-calendar 1.19.4
- **PDF**: jsPDF 3.0.3, html2canvas 1.4.1
- **Forms**: react-hook-form 7.75.0
- **Dates**: date-fns 4.1.0
- **Toasts**: react-hot-toast 2.6.0
- **Web Vitals**: web-vitals 5.1.0

### Testing & Dev Tools
- **Testing**: Jest 29.7.0, ts-jest 29.1.0, Testing Library, jsdom
- **Linting**: ESLint 9 (with next/core-web-vitals, next/typescript)
- **Build**: Turbopack (Next.js 15+)

---

## 3. Directory Structure

```
the-dev-pocket/
├── app/                          # Next.js App Router pages
│   ├── (auth)/                   # Auth routes (sign-in, sign-up)
│   ├── about/                    # About page
│   ├── api/                      # API routes
│   │   └── tech-feed/            # Tech feed API
│   ├── career/                  # Career guidance pages
│   ├── components/              # Shared components (Navbar, Footer, etc.)
│   ├── contact/                  # Contact page
│   ├── create-roadmap/           # Roadmap creation
│   ├── dashboard/               # Protected dashboard area
│   │   ├── achievements/         # Achievements/badges page
│   │   ├── quiz/                # Quiz center
│   │   │   └── [categorySlug]/[quizId]/  # Quiz runner
│   │   ├── resources/           # Resources management
│   │   ├── tech-feed/            # Tech feed with filtering
│   │   └── resume/               # Resume builder
│   ├── faq/                     # FAQ page
│   ├── job/                     # Job search page
│   ├── loading-demo/             # Loading states demo
│   ├── practice-hub/            # Practice hub
│   ├── privacy/                 # Privacy policy
│   ├── profile/[username]/      # Public user profiles
│   ├── resources/              # Resources listing
│   ├── search/                  # Global search
│   ├── settings/               # Settings pages
│   ├── terms/                   # Terms of service
│   ├── web-dev/                 # Web development resources
│   ├── layout.tsx               # Root layout with auth providers
│   └── page.tsx                 # Landing page
├── components/                   # UI components
│   ├── hero-with-mockup.tsx
│   ├── profile/                  # Profile components (ProfileCard, ProfileForm)
│   └── ui/                      # Radix UI primitives (dialog, popover, switch, etc.)
├── lib/                         # Utilities and helpers
│   ├── accessibility.tsx         # Accessibility utilities
│   ├── badge-checker.ts          # Badge validation
│   ├── bookmarks.ts             # Bookmark management
│   ├── env.ts                   # Environment validation
│   ├── error-handling.tsx        # Error boundaries
│   ├── performance.tsx          # Performance monitoring
│   ├── prisma.ts                # Prisma client singleton
│   ├── rate-limit.ts            # In-memory rate limiter
│   ├── rate-limit-upstash.ts    # Upstash Redis rate limiter
│   ├── toast.tsx                # Toast provider
│   ├── types/                   # TypeScript types
│   │   └── profile.ts
│   ├── badges.ts                # Badge definitions
│   ├── utils.ts                 # Utility functions
│   └── *.md                     # Documentation files
├── prisma/                      # Database schema & migrations
│   ├── schema.prisma            # Full database schema
│   ├── seed.ts                  # Database seeder
│   ├── seed-badges.ts           # Badge seeder
│   └── migrations/              # Prisma migrations
├── public/                      # Static assets
│   ├── quiz-icons/              # Quiz category icons
│   └── *.svg                   # SVG icons
├── roadmaps/                    # Markdown roadmap files
│   ├── dsa-problem-patterns.md
│   └── hft-cpp-roadmap.md
├── __tests__/                   # Jest test files
│   ├── api/                     # API route tests
│   └── app/                     # App component tests
├── bug-reports/                 # Issue templates and bug reports
├── middleware.ts                # Clerk auth middleware
├── next.config.ts               # Next.js configuration
├── tsconfig.json                # TypeScript configuration
├── tailwind.config.js           # Tailwind CSS configuration
├── postcss.config.mjs           # PostCSS configuration
├── eslint.config.mjs            # ESLint configuration
├── jest.config.cjs              # Jest configuration
├── jest.setup.ts                # Jest setup file
├── package.json                 # Dependencies and scripts
├── Dockerfile                   # Docker configuration
├── README.md                    # Project documentation
├── CONTRIBUTING.md              # Contribution guidelines
├── CODE_OF_CONDUCT.md           # Community code of conduct
└── LICENSE                      # MIT License

```

---

## 4. Key Pages & Routes

### Public Pages
| Route | Description |
|-------|-------------|
| `/` | Landing page with features, testimonials, how-it-works |
| `/about` | About the project |
| `/contact` | Contact form |
| `/faq` | Frequently asked questions |
| `/search` | Global resource search |
| `/resources` | Curated learning resources |
| `/resources/[id]` | Individual resource details |
| `/career-guidance` | Career guidance hub |
| `/job` | Job search and matching |
| `/practice-hub` | Practice exercises |
| `/privacy` | Privacy policy |
| `/terms` | Terms of service |
| `/profile/[username]` | Public user profiles |

### Protected Dashboard (requires auth)
| Route | Description |
|-------|-------------|
| `/dashboard` | Main dashboard with quick actions |
| `/dashboard/quiz` | Quiz categories listing |
| `/dashboard/quiz/[categorySlug]` | Quiz category detail |
| `/dashboard/quiz/[categorySlug]/[quizId]` | Quiz runner |
| `/dashboard/resources` | Saved resources |
| `/dashboard/tech-feed` | Tech news feed with category filters |
| `/dashboard/achievements` | Badges and achievements |
| `/dashboard/resume` | Resume builder |

### Auth Routes
| Route | Description |
|-------|-------------|
| `/sign-in` | Clerk sign-in page |
| `/sign-up` | Clerk sign-up page |

---

## 5. Database Schema (Prisma Models)

### Core User Models
- **User**: Primary user entity ( Clerk auth integration)
- **UserStats**: Points, streaks, daily goals, tasks
- **UserProfile**: Public profile (username, bio, avatar, skills, social links)
- **UserBadge**: Earned badges with metadata
- **UserProgress**: Roadmap milestone progress

### Content Models
- **Project**: AI project recommendations
- **Resource**: Curated learning resources with tags, difficulty, rating
- **Roadmap**: Learning paths with milestones
- **Milestone**: Individual roadmap steps

### Quiz System
- **QuizCategory**: Quiz categories (slug, name, icon)
- **Quiz**: Individual quizzes (title, difficulty, question count)
- **Question**: Quiz questions with JSON options and correct index
- **QuizAttempt**: User quiz attempts with scores

### Communication
- **ContactSubmission**: Contact form submissions
- **NewsletterSubscriber**: Email subscriptions

### Supporting
- **Bookmark**: User bookmarks
- **SearchHistory**: Search tracking
- **Badge**: Badge definitions with criteria

---

## 6. Build & Development Commands

```bash
# Development
npm run dev                  # Start Next.js dev server (port 3000)

# Production
npm run build                # Generate Prisma client + Next.js build
npm run start                # Start production server

# Code Quality
npm run lint                 # Run ESLint

# Testing
npm test                     # Run Jest tests (passWithNoTests)
npm run test:watch           # Jest watch mode
npm run test:coverage        # Jest with coverage report

# Database (Prisma)
npx prisma generate          # Generate Prisma client
npx prisma db push           # Push schema to database
npx prisma db seed           # Seed database with initial data
npx prisma studio            # Open Prisma Studio

# Install
npm install                  # Install dependencies
pnpm install                 # Or using pnpm
```

---

## 7. Environment Variables

### Required for Production
```env
DATABASE_URL="postgresql://..."        # Supabase session pooler URL
DIRECT_URL="postgresql://..."          # Supabase direct connection URL
CLERK_PUBLISHABLE_KEY="pk_..."        # Clerk publishable key
CLERK_SECRET_KEY="sk_..."              # Clerk secret key
```

### Optional
```env
RATE_LIMIT_MODE="INMEM"               # "INMEM" or "UPSTASH" (default: INMEM)
UPSTASH_REDIS_REST_URL="https://..."   # Required if UPSTASH mode
UPSTASH_REDIS_REST_TOKEN="..."         # Required if UPSTASH mode
CSRF_PROTECTION="true"                 # Enable CSRF protection
CSRF_PROTECTION_TOKEN="..."            # CSRF token if enabled
SECURITY_HEADERS="true"                # Enable security headers
```

---

## 8. Authentication & Middleware

**Clerk Middleware** (`middleware.ts`):
- Public routes: `/`, `/about`, `/contact`, `/sign-in`, `/sign-up`
- All other routes require authentication via `auth.protect()`
- CI bypass: If `CLERK_SECRET_KEY === 'dummy'`, auth is skipped
- Environment validation on startup (skipped in test mode)

**ClerkProvider** wraps the app in `app/layout.tsx` with dark mode support.

---

## 9. Rate Limiting

Two modes available via `RATE_LIMIT_MODE`:
- **INMEM** (default): In-memory rate limiting, no external dependencies
- **UPSTASH**: Redis-backed rate limiting using Upstash

Files:
- `lib/rate-limit.ts` - In-memory implementation
- `lib/rate-limit-upstash.ts` - Upstash implementation

---

## 10. Contribution Guidelines

### Quick Steps
1. Fork the repository
2. Clone your fork
3. Create feature branch: `git checkout -b feat/short-description`
4. Make changes and commit: `git commit -m "feat: add feature"`
5. Push and open PR: `git push origin feat/short-description`

### Commit Convention
- `feat:` - New features
- `fix:` - Bug fixes
- `docs:` - Documentation
- `style:` - Code style changes
- `refactor:` - Refactoring

### PR Checklist
- [ ] Clear title and description
- [ ] Small, focused changes
- [ ] Code compiles without errors
- [ ] Tests pass (if applicable)
- [ ] No sensitive data committed
- [ ] Documentation updated

### Contribution Ideas
- Dark mode toggle with persistence
- CourseCard component with tests
- Seed script for example AI projects
- Landing page accessibility improvements
- Missing images and social previews

---

## 11. Open Source Programs

- **GSSoC 2026** (GirlScript Summer of Code)
- **Hacktoberfest 2025** (6 quality PRs for swag)
- **ECWoC 2026** (Exciting Campus Winter of Code)

Issue labels: `gssoc`, `hacktoberfest`, `ecwoc`, `good first issue`, `help wanted`

---

## 12. Testing

**Jest Configuration** (`jest.config.cjs`):
- Environment: jsdom
- Test patterns: `**/__tests__/**/*.(test|spec).(ts|tsx)`
- Path alias: `@/*` → root directory

**Existing Tests**:
- `__tests__/app/footer.social-links.test.tsx`
- `__tests__/api/contact/route.test.ts`
- `__tests__/api/user-stats/detailed/route.test.ts`

**Test Commands**:
```bash
npm test                    # Run all tests
npm run test:watch          # Watch mode
npm run test:coverage       # With coverage
```

---

## 13. Risk-Sensitive Areas

⚠️ **High Risk** (requires careful review):
- `middleware.ts` - Auth protection logic, environment validation
- `lib/env.ts` - Environment variable validation
- `prisma/schema.prisma` - Database schema changes
- `lib/rate-limit.ts`, `lib/rate-limit-upstash.ts` - Rate limiting logic
- API routes handling user data

✅ **Safe PR Areas**:
- Documentation improvements (README, CONTRIBUTING, docs/*.md)
- Broken link fixes in README
- Resource metadata updates
- Quiz questions and categories
- Roadmap content additions
- Search/filter improvements
- UI component improvements (non-critical)
- Test coverage additions

---

## 14. Key Dependencies Summary

| Category | Package | Version |
|----------|---------|---------|
| Framework | next | ^16.1.1 |
| UI | react | ^19.1.0 |
| Styling | tailwindcss | ^4.1.18 |
| Database | prisma | ^6.19.1 |
| Auth | @clerk/nextjs | ^6.36.5 |
| Rate Limit | @upstash/ratelimit | ^2.0.7 |
| Animation | framer-motion | ^12.23.19 |
| Icons | lucide-react | ^0.544.0 |
| Testing | jest | ^29.7.0 |
| TypeScript | typescript | 5.9.3 |

---

## 15. Notes

- **Node.js Requirement**: >=20.9.0 (specified in `package.json` engines)
- **Post-install**: `prisma generate` runs automatically via `postinstall` script
- **Build**: Uses Turbopack via `next build --turbopack`
- **Dark Mode**: Enabled via `next-themes` with `class` strategy
- **Accessibility**: Custom utilities in `lib/accessibility.tsx`
- **Error Handling**: Error boundaries in `lib/error-handling.tsx`
- **Performance Monitoring**: Built-in in `lib/performance.tsx`