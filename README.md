# 🚀 KRPMS  
## 🧠 K1000 Research & Publication Management System

**KRPMS** is a full-stack, role-aware platform designed to manage the **entire academic research lifecycle** — from topic ideation and recruitment to peer review, mini-conference evaluation, and publication readiness.

Built with **process integrity, scalability, and academic rigor** at its core, KRPMS enables research organizations to operate with the discipline of established laboratories and editorial boards.

---

## ✨ Why KRPMS?

Academic research workflows are often fragmented across emails, spreadsheets, shared drives, and informal approvals.  
**KRPMS replaces this chaos** with a **single, secure, process-driven system** that enforces standards *without* slowing innovation.

### 🎯 Design Philosophy
- ✅ **Quality over volume**
- ✅ **Accountability over convenience**
- ✅ **Process clarity over informal coordination**

---

## 🌟 Key Highlights

- 🧩 **Role-based dashboards** for Director, Deputy Director, HoR, HoP, Management, Faculty, and Students  
- 🧠 **Research topic lifecycle** with multi-stage approvals (**HoR → HoP**)  
- 📂 **Project creation** with strict authorship & mentorship constraints  
- 🕵️ **Blind peer review system** with automatic thresholds and publication gating  
- 🎓 **Mini-conference workflows** (submissions, panels, evaluations, final results)  
- 🧑‍🎓 **Recruitment & onboarding** with temporary applicant portal and interviews  
- ⚡ **Optimistic UI updates** with conflict handling and periodic revalidation  

---

## 🛠️ Tech Stack

### Frontend
- ⚛️ Next.js 16 (App Router)
- ⚛️ React 19
- 🟦 TypeScript
- 🎨 TailwindCSS, Radix UI, shadcn/ui

### Backend
- 🔐 NextAuth (credentials-based authentication)
- 🗄️ PostgreSQL
- 🔗 Prisma ORM with **Row-Level Security (RLS)**

### State & UX
- 🧠 Zustand for predictable client-side state
- ⚡ Optimistic updates with server-side conflict resolution

### Analytics
- 📊 @vercel/analytics

---

## 🏗️ Architecture Overview

- 📁 App Router under `app/`
- 🔌 API routes in `app/api/*`
- 🧩 Shared UI components in `components/`
- 🧠 Client state in `lib/stores/*` (Zustand)
- 🗄️ Prisma schema in `prisma/schema.prisma`
- 📄 Detailed workflows in `docs/Workflow-Process.md`

### 🔑 Architectural Principles
- Atomic server updates to prevent race conditions  
- Server-side RBAC (never client-only)  
- Explicit state machines for auditability  
- Scalable design without premature over-engineering  

---

## 🔐 Roles & RBAC (Implemented)

### Roles
- `director`
- `deputy_director`
- `hor`
- `hop`
- `management`
- `faculty`
- `student`

### Responsibility Boundaries
- 🧠 **HoR** → scientific & methodological approval  
- 📝 **HoP** → publication quality, ethics, final decisions  
- 🏛️ **Director / Deputy Director** → strategic oversight & onboarding  
- 👩‍🏫 **Faculty / Management** → evaluation & throughput  
- 👨‍🎓 **Students** → research execution  

All role checks are enforced **server-side**.

---

## 🔄 Core Workflows

### 📌 Topic Lifecycle
Create → HoR Approval → HoP Approval → Approved → Project Eligible  

### 🧑‍🎓 Recruitment
Applicant → Interview Panel → Leadership / HoP Approval → Active / Inactive  

### 📄 Publication
Stage Submissions → Blind Peer Reviews → Final Review → Repository  

### 🎤 Mini-Conference
Submission → Panel Evaluation → HoP Finalization  

📘 For complete and precise workflows, see:  
`docs/Workflow-Process.md`

---

## 🔌 API Overview (Selected)

All backend routes are exposed under `/api/*`.

### 👥 Users & Approvals
- `/api/users`
- `/api/users/[id]/approve`
- `/api/users/[id]/reject`

### 🧠 Topics
- `/api/topics`
- `/api/topics/[id]/approve-hor`
- `/api/topics/[id]/approve-hop`

### 📂 Projects & Reviews
- `/api/projects`
- `/api/peer-reviews`

### 🎓 Interviews
- `/api/interviews/*`

### 🎤 Mini-Conference
- `/api/mini-conference`
- `/api/mini-conference/panels`
- `/api/mini-conference/evaluations`

### 🧑‍🎓 Temporary Applicant Portal
- `/api/auth/temp-signin`
- `/api/temp-portal/profile`

---

## ⚙️ Getting Started

### 📋 Prerequisites
- Node.js **18.18+** (LTS recommended)
- PNPM **8+**
- PostgreSQL (local or managed)

### 📦 Installation
```bash
pnpm install
```

### 🔐 Environment Configuration
Create a `.env` file in the project root:
```env
DATABASE_URL="postgres://user:password@host:5432/dbname"
NEXTAUTH_SECRET="your-strong-random-secret"
TEMP_PORTAL_SECRET="optional-override-secret"
```

### 🗄️ Database Setup
```bash
pnpm prisma generate --schema=./prisma/schema.prisma
pnpm prisma migrate dev --name init --schema=./prisma/schema.prisma
# or
pnpm prisma db push --schema=./prisma/schema.prisma
```

### ▶️ Run Locally
```bash
pnpm dev
# http://localhost:3000
```

---

## 🔒 Security

- 🔑 Passwords hashed using bcrypt  
- 🛡️ Role-based authorization on every sensitive API  
- 🗄️ Row-Level Security (RLS) enforced at DB level  
- ⏳ Temporary applicant access auto-revoked post-onboarding  

---

## 📁 Project Structure (Partial)

```text
krpms/
├─ app/                  # App Router & API routes
├─ components/           # UI components and role dashboards
├─ docs/                 # Workflow & process documentation
├─ lib/                  # Stores, helpers, and types
├─ prisma/               # Prisma schema
├─ public/               # Static assets
└─ README.md
```

---

## 🚫 Contributing

This is **proprietary software**.  
External contributions are not accepted.

For demos, institutional adoption, or collaboration discussions, please contact the author.

---

## 📜 License

🔒 **Proprietary Software**  
No license is granted.

---

## 📬 Contact

**Anjishnu Saw**  
📧 Email: **sawanjishnu6@gmail.com**
