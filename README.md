# KRPMS  
## K1000 Research & Publication Management System

KRPMS is a full-stack, role-aware platform designed to manage the **entire academic research lifecycle** — from topic ideation and recruitment to peer review, mini-conference evaluation, and publication readiness.

Built with **process integrity, scalability, and academic rigor** at its core, KRPMS enables research organizations to operate with the discipline of established laboratories and editorial boards.

---

## Why KRPMS?

Academic research workflows are often fragmented across emails, spreadsheets, ad-hoc drives, and informal approvals. KRPMS replaces this fragmentation with a **single, secure, process-driven system** that enforces standards without slowing innovation.

**Design principles**
- Quality over volume  
- Accountability over convenience  
- Process clarity over informal coordination  

---

## Highlights

- Role-based dashboards for Director, Deputy Director, HoR, HoP, Management, Faculty, and Students
- Research topic lifecycle with multi-stage approvals (HoR → HoP)
- Project creation with strict authorship and mentorship constraints
- Blind peer reviews with automatic thresholds and publication gating
- Mini-conference submissions, panels, evaluations, and results finalization
- Recruitment and onboarding with temporary applicant portal and interviews
- Optimistic UI updates with conflict handling and periodic revalidation

---

## Tech Stack

**Frontend**
- Next.js 16 (App Router)
- React 19
- TypeScript
- TailwindCSS, Radix UI, shadcn/ui

**Backend**
- NextAuth (credentials-based authentication)
- PostgreSQL
- Prisma ORM with Row-Level Security (RLS)

**State & UX**
- Zustand for predictable client state
- Optimistic updates with server-side conflict resolution

**Analytics**
- @vercel/analytics

---

## Architecture Overview

- App Router under `app/`
- API routes in `app/api/*`
- Shared UI components in `components/`
- Client state in `lib/stores/*` (Zustand)
- Prisma schema in `prisma/schema.prisma`
- Detailed workflows in `docs/Workflow-Process.md`

**Key architectural patterns**
- Atomic server updates to prevent race conditions
- Server-side role enforcement (never client-only)
- Explicit state machines for auditability
- Scalable design without premature over-engineering

---

## Roles & RBAC

Implemented roles:
- `director`
- `deputy_director`
- `hor`
- `hop`
- `management`
- `faculty`
- `student`

**Responsibility boundaries**
- **HoR**: scientific and methodological approval
- **HoP**: publication quality, ethics, and final decisions
- **Director / Deputy Director**: strategic oversight and onboarding authority
- **Faculty / Management**: evaluation and operational throughput
- **Students**: research execution

All role checks are enforced server-side.

---

## Core Workflows

### Topic Lifecycle
Create → HoR Approval → HoP Approval → Approved → Project Eligible

### Recruitment
Applicant → Interview Panel → Leadership / HoP Approval → Active / Inactive

### Publication
Stage Submissions → Blind Peer Reviews → Final Review → Repository

### Mini-Conference
Submission → Panel Evaluation → HoP Finalization

For the complete, precise workflow definitions and API semantics, see  
`docs/Workflow-Process.md`.

---

## API Overview (Selected)

All backend routes are available under `/api/*`.

**Users & Approvals**
- `/api/users`
- `/api/users/[id]/approve`
- `/api/users/[id]/reject`

**Topics**
- `/api/topics`
- `/api/topics/[id]/approve-hor`
- `/api/topics/[id]/approve-hop`

**Projects & Reviews**
- `/api/projects`
- `/api/peer-reviews`

**Interviews**
- `/api/interviews/*`

**Mini-Conference**
- `/api/mini-conference`
- `/api/mini-conference/panels`
- `/api/mini-conference/evaluations`

**Temporary Applicant Portal**
- `/api/auth/temp-signin`
- `/api/temp-portal/profile`

---

## Getting Started

### Prerequisites
- Node.js 18.18+ (LTS recommended)
- PNPM 8+
- PostgreSQL (local or managed)

### Installation
```bash
pnpm install
