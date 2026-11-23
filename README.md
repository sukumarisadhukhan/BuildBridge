
# BuildBridge

> **Bridging traditional learning to real-world work.**

**Learn it. Build it. Prove it. Earn from it.**

BuildBridge is an AI-assisted learning-to-work platform designed to help students turn traditional learning into practical capability and evidence-backed experience. It connects learning resources, career and coursework pathways, hands-on projects, skill evidence, feedback, credentials and professional opportunities in one connected journey.

<p align="left">
  <a href="build-bridge-iuqj5812p-sukumari-sadhukhan.vercel.app"><strong>Open BuildBridge</strong></a> ·
  <a href="https://build-bridge-demo.vercel.app"><strong>Interactive demo</strong></a> ·
  <a href="https://github.com/sukumarisadhukhan/BuildBridge"><strong>Source code</strong></a> ·
  <a href="https://github.com/sukumarisadhukhan/BuildBridge-Demo"><strong>Demo repository</strong></a>
</p>

> **Deployment note:** These are the Vercel URLs currently recorded in the GitHub repository settings. Confirm public access and the active Production deployment in Vercel before sharing the links as a live judge-facing release.

---

## The problem

Students can find lectures, videos, courses, tutorials and certificates across many platforms. But finishing content does not necessarily show that someone can apply the knowledge, build a solution, deliver against requirements or contribute to a real project.

The next steps are often disconnected: students must independently find projects, understand unfamiliar requirements, collect proof of their work, obtain useful feedback and search for relevant opportunities.

BuildBridge is designed to connect those steps. It does not replace existing learning providers. It helps students organise and apply the learning they already access, then preserve evidence of what they can actually do.

## The BuildBridge journey

**Discover → Personalise → Learn → Build → Prove → Validate → Grow and Earn**

| Stage | What happens |
|---|---|
| Discover | Find learning resources, pathways and practical project options. |
| Personalise | Connect career goals, coursework, skills, experience and knowledge gaps to next steps. |
| Learn | Use videos, courses, tutorials, documentation, coursework and AI-assisted explanations. |
| Build | Apply knowledge through practice projects, open-source issues and verified company assignments. |
| Prove | Keep repositories, deployments, reports, screenshots, deliverables, milestone submissions and feedback. |
| Validate | Distinguish learning and practice from demonstrated work and explicit company approval. |
| Grow and earn | Explore relevant internships, freelance assignments, paid micro-projects and other opportunities when available and eligibility criteria are met. |

## What BuildBridge brings together

### Career-first and coursework-first pathways

Students can start with a career direction or with academic material. Career-first planning connects a target role to prerequisite skills, resources, practice and projects. Coursework-first mapping analyses a syllabus or assignment and connects its concepts to skills, career relevance and possible project work.

The coursework workflow supports PDF and plain-text inputs (`.txt`, `.md`, `.csv`) up to 4 MB. Gemini is used for structured concept extraction and learning suggestions when the server-side integration is configured. Uploaded source material is processed as an input; the mapping workflow is not intended to retain the original upload.

### Learning resources and AI guidance

BuildBridge brings together links to existing courses, videos, tutorials and documentation. Its YouTube integration can recommend embeddable learning videos and uses an embedded player to record playback progress. The current player only records completion after **100% continuous playback**; seeking through a video does not count as completed learning. BuildBridge does not read a student's private YouTube watch history.

The AI Mentor is designed to explain concepts, help interpret errors, guide project planning and connect advice to the student's learning context. AI output is guidance, not proof of achievement and not a substitute for company or administrator approval.

### Practical project pathways

BuildBridge keeps three kinds of project work distinct:

- **BuildBridge Practice Projects:** platform-published projects for practice and portfolio evidence. They are not employer assignments and do not qualify for company completion certificates.
- **Verified Company Projects:** projects published by verified organisations with scope, deliverables, acceptance criteria, deadlines, milestone reviews and compensation terms where supplied. Only the assigning company can approve its own project work.
- **External / open-source projects:** external issue listings, currently including GitHub issue discovery. These remain external to BuildBridge and do not imply a partnership with the repository owner.

Evidence can include repository and deployment links, reports, screenshots, technical documentation, test results, reflections, milestone submissions and other requested deliverables.

### Evidence-backed skill progression

BuildBridge distinguishes four levels instead of treating every profile claim or course certificate as proof of practical ability:

| State | Meaning |
|---|---|
| **Studied** | The student engaged with learning resources or coursework covering the skill. |
| **Practised** | The student applied the skill in exercises or practice work. |
| **Demonstrated** | The student supplied accepted project or other evidence of application. |
| **Company-verified** | The assigning verified company explicitly approved relevant industry work or milestones. |

A self-declared skill or completed course should not automatically become demonstrated or company-verified.

### My Learning & Work Vault

The Student Vault brings learning history, coursework mappings, saved resources, skill evidence, projects, submissions, reports, feedback and credentials into a persistent record. Uploaded supporting documents use the private `student-vault` Supabase Storage bucket; file access is issued through time-limited signed URLs. Repository, deployment and learning-resource links remain external links.

### Professional opportunities

The opportunity model is intended to connect demonstrated skills and project evidence to internships, freelance assignments, paid micro-projects, company projects and other suitable opportunities. Matching should consider evidence, experience, career goals and eligibility, not just self-declared skills or course completion.

Opportunity details should show the source-provided requirements, scope, deadline, compensation and application status where those details exist. A match is informational: BuildBridge does not guarantee selection, payment, stipends or employment.

## Three role-based workspaces

### Student workspace

Career and coursework pathways, learning resources, YouTube learning activity, AI Mentor, projects, open-source discovery, milestone evidence, opportunities, applications, the Learning & Work Vault, achievements and settings.

### Company workspace

Organisation profile and verification status, project and opportunity publishing, student applications, assignments, milestone management, evidence review, revision requests, explicit approvals, authorised certificate signatory settings and company preferences.

### Administrator workspace

Company verification queue, practice-project moderation, platform certificate administration, users and access, AI/operational management, disputes, audit trail, platform health and administrator settings.

Administrator access is not granted through public sign-up. The platform owner is provisioned separately and checked against the configured owner identity.

## Trust, verification and credentials

- A company representative's sign-up choice is a request for company access, not an automatic role grant.
- Company verification requires the organisation's email/domain workflow, DNS TXT ownership proof and a separate administrator decision.
- Only the assigning verified company can approve its own project submissions and milestones.
- A practice project is learning evidence, not employer-approved professional experience.
- Company project-completion credentials are separate from BuildBridge platform credentials and theory-learning certificates. Company completion issuance depends on the required project approvals and an authorised company signatory.
- The coursework theory knowledge check has a separate grading flow; a score of **80% or higher** is the threshold for its Theory Learning Certificate. This is not a project-experience credential.

## System architecture

The architecture document describes the **original BuildBridge product** and its current application topology. It covers the Vercel-hosted Next.js application, Supabase authentication/database/storage, role-aware server routes, the notification worker and optional external integrations.

**[Read the BuildBridge system architecture](docs/ARCHITECTURE.md)**

The demo repository links to this same original-product architecture. There is no separate demo architecture diagram: the demo is a synthetic-data presentation of the original product's workflows.

## Technology stack

| Layer | Technology |
|---|---|
| Web application | Next.js 15 App Router, React 19, TypeScript |
| Styling and UI | Tailwind CSS 3, custom responsive CSS, Lucide icons |
| Authentication | Supabase Auth with `@supabase/ssr`, PKCE and cookie-based sessions |
| Database | Supabase PostgreSQL, Row Level Security, SQL functions, triggers and migrations |
| File storage | Supabase Storage with private student-vault files and signed access URLs |
| AI | Google Gemini through `@google/genai` server-side routes |
| Learning resources | YouTube Data API v3 and the YouTube IFrame Player |
| External project discovery | GitHub Search API |
| Transactional email | Resend through a database outbox and scheduled worker |
| Hosting and scheduled work | Vercel, including the configured notification cron route |

External services are conditional integrations. A route or environment variable existing in the repository does not prove that the provider is configured, reachable or fully tested in the deployed environment.

## Run locally

### Prerequisites

- Node.js 22 or newer
- npm
- A Supabase project for authentication and database-backed workflows

### Install and configure

```bash
git clone https://github.com/sukumarisadhukhan/BuildBridge.git
cd BuildBridge
npm ci
cp .env.example .env.local
```

On Windows PowerShell, use `Copy-Item .env.example .env.local` and, if needed, `npm.cmd` instead of `npm`.

Edit `.env.local` with the values required by the features you intend to test. Never commit this file.

### Start the development server

```bash
npm run dev
```

Open `http://localhost:3000`.

### Validation commands

```bash
npm run typecheck
npm run lint
npm run build
```

These commands are provided by the current `package.json`. Passing a local build does not prove that the deployed Supabase schema, OAuth providers, AI generation, email delivery or every end-to-end workflow is operational.

## Environment configuration

The `.env.example` file is the starting point. Configure only the integrations you use.

| Variable | Purpose |
|---|---|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase project URL. |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` or `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY` | Public client key; use the supported key for the project. |
| `SUPABASE_SERVICE_ROLE_KEY` | Server-only privileged operations. Never expose it to the browser. |
| `ADMIN_OWNER_EMAIL` | Confirmed and manually provisioned platform-owner email. |
| `NEXT_PUBLIC_APP_URL` | Public application origin. |
| `APP_BASE_URL` | Server-side canonical links and email URLs. |
| `GEMINI_API_KEY` | Gemini AI Mentor, roadmap and coursework analysis. |
| `GEMINI_MODEL` | Optional primary Gemini model. |
| `GEMINI_FALLBACK_MODELS` | Optional comma-separated fallback models. |
| `YOUTUBE_API_KEY` | YouTube Data API v3 resource discovery. |
| `GITHUB_TOKEN` | Optional server-side GitHub API token for improved rate limits. |
| `RESEND_API_KEY` | Resend transactional email delivery. |
| `EMAIL_FROM`, `EMAIL_FROM_NAME` | Verified sender address and display name. |
| `CRON_SECRET` | Authorises the scheduled notification worker. |
| `UNSUBSCRIBE_TOKEN_SECRET` | Server-only signing secret for unsubscribe links. |

OAuth provider client secrets belong in Supabase Auth provider settings (and the provider's own secure console), not in source control. Google, GitHub, LinkedIn OIDC and Microsoft/Azure sign-in each require provider-specific configuration and callback testing.

## Supabase database setup

**Do not run `database-schema.sql` against an existing BuildBridge database.** It is an initial-install schema, not a production upgrade script.

- For a genuinely empty Supabase project, follow the fresh-project sequence in [Database migrations](docs/DATABASE-MIGRATIONS.md).
- For an existing project, take a backup, run the read-only preflight checks and follow the existing-database migration sequence in that guide.
- Run SQL in the correct Supabase project and verify the resulting tables, policies, triggers and PostgREST schema state.
- Vercel deployments do not apply Supabase SQL migrations automatically.

The repository includes preflight/postflight scripts and versioned migrations. Treat their output and the live database catalog as authoritative; do not infer that a migration ran merely because its file exists in GitHub.

## Deployment

The app is designed for Vercel. Connect the `BuildBridge` GitHub repository, configure the required Production environment variables, confirm the Production branch and canonical domain, and validate a Preview deployment before promoting changes.

Read **[Deployment and rollback](docs/DEPLOYMENT.md)** before changing Production. Vercel hosting and Supabase database changes are separate release operations.

The repository's `vercel.json` schedules `/api/cron/notifications` with the configured `0 8 * * *` schedule. The worker requires the server-side cron, Supabase and Resend configuration described in the deployment guide. Without a verified sender and valid provider credentials, application-triggered email delivery should not be assumed to work.

## Repository map

```text
app/
  api/                 Next.js route handlers for AI, coursework, projects,
                       resources, Vault, certificates, notifications and health
  auth/                Sign-in, sign-up, callback and account recovery
  student/             Student dashboard route
  company/             Company dashboard route
  admin/               Administrator dashboard route
components/            Role workspaces and product workflows
lib/                   Supabase clients, auth helpers, API clients and domain logic
supabase/              Initial schema, SQL repair scripts and versioned migrations
docs/
  ARCHITECTURE.md      Original BuildBridge system architecture
  DATABASE-MIGRATIONS.md
  DEPLOYMENT.md
```

## Important product boundaries

- AI explanations and recommendations are assistance, not proof of skill or an approval decision.
- External GitHub issues remain external listings; they are not BuildBridge projects or partnerships.
- Student evidence is private by default and must remain protected by authenticated access, RLS and private Storage policies.
- Public certificate verification should expose only the intended certificate fields, not private profile or evidence data.
- Configuration checks and `/api/health` are not substitutes for real end-to-end tests of every integration.
- Employment, selection, payment, stipend and project outcomes are never guaranteed.

## Documentation

- [System architecture](docs/ARCHITECTURE.md)
- [Database migrations](docs/DATABASE-MIGRATIONS.md)
- [Deployment and rollback](docs/DEPLOYMENT.md)
- [Windows quick start](QUICKSTART-WINDOWS.md)
- [Build validation notes](BUILD_VALIDATION.md)
- [Backend repair validation notes](BACKEND_REPAIR_VALIDATION.md)

## License

No open-source license is currently specified in this repository. All rights remain with the project owner unless a license is added.


