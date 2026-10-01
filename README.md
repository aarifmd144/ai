# AI-Powered Career & Employability Intelligence Platform

> **Master's in Computer Science Final-Year Project Demonstration**  
> A production-grade, full-stack intelligence platform that empowers university students and career switchers to audit resumes against ATS algorithms, analyze skill gaps, generate adaptive learning roadmaps, practice AI-evaluated mock interviews, and calculate multidimensional job readiness scores.

---

## 🌟 Executive Summary & Features

### 🎓 1. Student Employability Portal
- **Interactive Command Dashboard (`/dashboard`)**:
  - Profile completion metric, Resume quality score, Skill count, and composite Job Readiness score.
  - Interactive Recharts Radar Chart illustrating multidimensional employability across 6 core pillars.
  - Active target career alignment progress and high-priority competency gap summary.
  - Timeline of recent mock interview attempts and quick action triggers.
- **Academic & Career Profile Management (`/profile`)**:
  - Full personal details, phone, location, education degree, department, university, and graduation year.
  - Career interest tagging and professional biography editing.
- **AI Resume ATS Scanner & Management (`/resume`)**:
  - Drag-and-drop file upload supporting `.pdf` and `.docx` documents up to 5MB.
  - Server-side document text parsing via `pdf-parse` and `mammoth`.
  - Comprehensive ATS Compatibility Score (0-100), Keyword Match Density, Formatting Quality, Experience Impact, and Education credentials.
  - Categorized Strengths, Weaknesses, and actionable suggestions using the Google XYZ formula.
  - Extracted skills keyword badges and parser verification viewer.
- **Skill Analysis & Inventory (`/skills`)**:
  - Catalog of 40+ standardized skills across 12+ categories (Programming, Web Dev, Databases, DevOps, Cloud, AI/ML, Cybersecurity, Soft Skills).
  - Four proficiency tiers: **Beginner**, **Intermediate**, **Advanced**, and **Expert** with estimated years of experience.
- **AI Career Recommendations (`/careers`)**:
  - Real-time ranking of career opportunities based on current student skills and proficiency depth.
  - Side-by-side career comparison tool evaluating salary ranges, growth outlooks, and missing competencies.
- **Skill Gap Analysis Matrix (`/skill-gap`)**:
  - Compares student proficiencies against target career requirements.
  - Segregates competencies into **Matching Skills (Green)**, **Needs Improvement (Yellow)**, and **Missing Skills (Red with High/Medium/Low priority)**.
  - One-click trigger to generate a custom milestone roadmap.
- **Personalized Learning Roadmap (`/roadmap`)**:
  - Stage-by-stage milestone sprints addressing identified skill deficiencies.
  - Interactive timeline with estimated hours, difficulty badges, and curated external learning resources.
  - Toggle stage completion checkboxes with instant recalculation of roadmap progress %.
- **Multidimensional Job Readiness Score (`/readiness`)**:
  - Composite 0-100 score weighted across: Resume Quality (20%), Tech Skills (20%), Soft Skills (10%), Projects/Education (15%), Mock Interview Performance (20%), and Roadmap Progress (15%).
  - Multi-axis Recharts radar chart and targeted strategic recommendations.
- **AI Mock Interview Simulator (`/mock-interview`)**:
  - Question-by-question interview runner with real-time session timer.
  - Configurable by Career, Difficulty (Junior, Mid, Senior), and Question Type (Technical, Behavioral STAR, HR, Mixed).
  - NLP evaluation delivering Overall Score, Technical Accuracy, Communication Clarity, Relevance, Confidence Verdict, Strengths, and Polish areas.
  - Full interview history log with historical performance tracking.
- **AI Career Assistant Chatbot (`/assistant`)**:
  - Conversational counseling interface with suggested prompt chips.
  - Context-aware: Injects student's target career, profile details, and scores into system prompts.
  - Dual-mode intelligence: Works with OpenAI / Google Gemini API keys, or falls back to an internal heuristic NLP engine.
- **Notification Center (`/notifications`)**:
  - Real-time notifications for resume ATS evaluation, skill gap calculations, and interview completions.
  - Navbar dropdown with unread badge counter and mark-as-read actions.
- **Account & Security Settings (`/settings`)**:
  - Profile identity overview, dark/light mode toggle, and password security updates.

---

### 🛡️ 2. Administrator Governance Portal
- **Executive Command Dashboard (`/admin/dashboard`)**:
  - Platform KPIs: Total users, Active/Inactive counts, Total resumes, Total careers, Mock interviews conducted, and Cohort average readiness.
  - Career path popularity distribution charts and monthly cohort registration trends.
- **User Management (`/admin/users`)**:
  - Paginated table with live search by name/email, role filtering (Student/Admin), and account status filtering.
  - Inspect full student profiles (degree, department, resume count, skill count, mock interviews).
  - Account actions: Activate, Deactivate, and Delete users.
- **Career Management (`/admin/careers`)**:
  - Full CRUD operations on career definitions.
  - Configure salary ranges, growth outlooks, and assign required skills with **Importance Weightings** (Critical, Important, Nice to Have) and **Minimum Proficiency**.
- **Skill Catalog Management (`/admin/skills`)**:
  - Standardize tech competencies, assign categories, and view student adoption counts.
- **Interview Question Repository (`/admin/questions`)**:
  - Curate interview questions across technical, behavioral, HR, and scenario categories with evaluation rubrics and sample answers.
- **Learning Resource Management (`/admin/resources`)**:
  - Curate documentation, video courses, books, and interactive tutorials mapped to skills and careers.
- **Advanced Cohort Analytics (`/admin/analytics`)**:
  - Deep-dive reporting on skill bottlenecks, interview score distributions, and registration trajectories.
- **System Telemetry & Settings (`/admin/settings`)**:
  - Real-time telemetry on PostgreSQL database engine, Next.js App Router runtime, AI intelligence fallback, and admin password reset.

---

## 💻 Technology Stack

| Layer | Technology |
|---|---|
| **Frontend Framework** | [Next.js 14](https://nextjs.org/) (App Router, Server Components & Client Hydration) |
| **Language** | [TypeScript](https://www.typescriptlang.org/) (Strict mode) |
| **Styling & Design** | [Tailwind CSS](https://tailwindcss.com/) with custom design system and CSS variables |
| **Theme Engine** | [next-themes](https://github.com/pacocoursey/next-themes) (Dark & Light mode support) |
| **Icons** | [Lucide React](https://lucide.dev/) |
| **Data Visualization** | [Recharts](https://recharts.org/) (Radar charts, Bar charts, Line charts) |
| **Database** | [PostgreSQL 14/18](https://www.postgresql.org/) (ACID relational models, indexes, cascades) |
| **ORM** | [Prisma ORM 5.22](https://www.prisma.io/) (Type-safe client, migrations, seeding) |
| **Authentication & RBAC** | JWT (JSON Web Tokens) with HTTP-only cookies, bcryptjs password hashing, Next.js Edge Middleware |
| **Document Processing** | `pdf-parse` (PDF resume extraction) & `mammoth` (DOCX resume parsing) |
| **AI Intelligence Layer** | Dual-mode: OpenAI / Google Gemini API connectors with high-fidelity offline heuristic NLP fallback |
| **Input Validation** | [Zod](https://zod.dev/) |

---

## 🏛️ System Architecture

```
                                  ┌────────────────────────┐
                                  │      Web Browser       │
                                  │ (Responsive / Desktop) │
                                  └───────────┬────────────┘
                                              │ HTTP / HTTPS
                                              ▼
                                  ┌────────────────────────┐
                                  │   Next.js Middleware   │
                                  │ (RBAC / Auth Guardian) │
                                  └───────────┬────────────┘
                                              │
                      ┌───────────────────────┴───────────────────────┐
                      │                                               │
                      ▼                                               ▼
         ┌─────────────────────────┐                     ┌─────────────────────────┐
         │     Student Routes      │                     │      Admin Routes       │
         │   /dashboard, /resume   │                     │  /admin/dashboard,      │
         │  /skills, /skill-gap    │                     │  /admin/users, /careers │
         │  /roadmap, /readiness   │                     │  /admin/questions, etc. │
         └────────────┬────────────┘                     └────────────┬────────────┘
                      │                                               │
                      └───────────────────────┬───────────────────────┘
                                              │
                                              ▼
                                  ┌────────────────────────┐
                                  │     Next.js Server     │
                                  │   (API Route Handlers) │
                                  └───────────┬────────────┘
                                              │
                ┌─────────────────────────────┼─────────────────────────────┐
                │                             │                             │
                ▼                             ▼                             ▼
   ┌─────────────────────────┐   ┌─────────────────────────┐   ┌─────────────────────────┐
   │    Document Parsers     │   │   AI Intelligence API   │   │       Prisma ORM        │
   │  (pdf-parse / mammoth)  │   │  (LLM / Heuristic NLP)  │   │  (Type-safe DB Client)  │
   └─────────────────────────┘   └─────────────────────────┘   └────────────┬────────────┘
                                                                            │
                                                                            ▼
                                                               ┌─────────────────────────┐
                                                               │  PostgreSQL Database    │
                                                               │    (career_intel_db)    │
                                                               └─────────────────────────┘
```

---

## 🗄️ Database Relational Schema

The database model is normalized in `prisma/schema.prisma` with 19 tables:
- **`User`**: Account credentials, email, password hash, role (`STUDENT` | `ADMIN`), active status.
- **`StudentProfile`**: Phone, education level, degree, department, university, graduation year, location, bio, career interests.
- **`Resume`**: Metadata, file URL, file type, file size, raw parsed text, primary flag.
- **`ResumeAnalysis`**: ATS score, skill score, experience score, education score, keyword score, formatting score, strengths, weaknesses, actionable suggestions.
- **`Skill`**: Name, domain category, description.
- **`UserSkill`**: User proficiency level (`BEGINNER`, `INTERMEDIATE`, `ADVANCED`, `EXPERT`), experience in years.
- **`Career`**: Title, slug, category, salary range, growth outlook, description.
- **`CareerSkill`**: Required skills per career with importance weight (`CRITICAL`, `IMPORTANT`, `NICE_TO_HAVE`) and minimum proficiency.
- **`SkillGap`**: Computed match percentage, matching skills, weak skills, missing skills with priority.
- **`LearningRoadmap`**: Title, total stages, completed stages, progress percentage.
- **`LearningRoadmapItem`**: Stage number, title, description, skills covered, curated resources, estimated hours, completion checkbox.
- **`LearningResource`**: Title, description, URL, duration, difficulty, type (Course, Book, Tutorial).
- **`InterviewQuestion`**: Career link, question text, category, difficulty, question type (`TECHNICAL`, `BEHAVIORAL`, `HR`, `SCENARIO`), sample answers.
- **`MockInterview`**: Completed session score, technical score, communication score, relevance score, confidence feedback, strengths, weaknesses, suggestions.
- **`InterviewAnswer`**: Question link, user typed answer, score, rubric feedback.
- **`Notification`**: Title, message, link, read status, notification type.
- **`ChatConversation` & `ChatMessage`**: AI assistant message threads.
- **`ActivityLog`**: Audit trail of authentication and platform operations.

---

## 🔑 Demo Login Credentials

The application comes pre-seeded with rich demo accounts so it can be demonstrated immediately:

### 1. Student Account (Alex Chen - CS Senior)
- **Email**: `student@careerintel.com`
- **Password**: `Student@123456`
- **Pre-populated with**: Complete profile, uploaded resume with ATS analysis (89%), 12 technical skills, 82% Full Stack Developer match, 6-stage roadmap (50% complete), mock interview evaluation (86/100), and notifications.

### 2. Secondary Student Account (Sarah Jenkins - Data Science)
- **Email**: `sarah.data@university.edu`
- **Password**: `Student@123456`

### 3. Administrator Account (Dr. Arthur Vance)
- **Email**: `admin@careerintel.com`
- **Password**: `Admin@123456`
- **Privileges**: Executive command, cohort analytics, user activation/deactivation, career curriculum editing, skill management, and interview question repository.

*(Note: The login screen also features one-click "Student Demo" and "Admin Demo" pre-fill buttons for fast presentation.)*

---

## 🚀 Installation & Local Setup

### Prerequisites
- **Node.js**: v18 or later (tested on v25.9)
- **npm**: v9 or later
- **PostgreSQL**: v14, v15, v16, or v18 running locally on port 5432

### 1. Clone or Open the Repository
```bash
cd c:\Users\Aarif\Downloads\ai
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Environment Variables
Create a `.env` file in the project root (see `.env.example`):
```env
# PostgreSQL connection URL
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/career_intel_db?schema=public"

# Authentication JWT secret
AUTH_SECRET="career-intel-jwt-secret-key-32-chars-long-secure-token"

# Optional external AI keys (OpenAI or Google Gemini)
# The platform features an intelligent internal NLP heuristic engine that works out of the box!
AI_API_KEY=""
GEMINI_API_KEY=""
OPENAI_API_KEY=""

# Application URL
NEXT_PUBLIC_APP_URL="http://localhost:3000"
```

### 4. Apply Database Migrations & Seed Data
```bash
# Push schema to PostgreSQL database
npx prisma db push

# Seed initial admin, students, careers, skills, questions, resources, and demo data
npx prisma db seed
```

### 5. Run Automated Test Suite
Verify that all 26 unit & integration assertions pass:
```bash
npx tsx scripts/testSuite.ts
```

### 6. Start the Development Server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your web browser.

### 7. Production Build & Start
```bash
npm run build
npm start
```

---

## 📂 Project Structure

```
ai/
├── prisma/
│   ├── schema.prisma           # Relational PostgreSQL database schema
│   └── seed.ts                 # Realistic database seeder script
├── public/
│   └── uploads/resumes/        # Designated storage for uploaded resume files
├── scripts/
│   └── testSuite.ts            # Automated verification suite (26 assertions)
├── src/
│   ├── app/
│   │   ├── admin/              # Administrator Portal Pages
│   │   │   ├── analytics/      # Cohort analytics & distribution charts
│   │   │   ├── careers/        # Career CRUD & skill requirements
│   │   │   ├── dashboard/      # Executive KPI overview
│   │   │   ├── questions/      # Question bank management
│   │   │   ├── resources/      # Learning resource curation
│   │   │   ├── settings/       # System telemetry & admin credentials
│   │   │   ├── skills/         # Global skill catalog CRUD
│   │   │   └── users/          # User management & activation
│   │   ├── api/                # REST-style Next.js API Endpoints
│   │   │   ├── admin/          # Admin protected API endpoints
│   │   │   ├── auth/           # Login, Register, Logout, Me, Forgot/Reset
│   │   │   └── student/        # Student dashboard, resume, skills, roadmap, etc.
│   │   ├── assistant/          # AI Career Assistant Chatbot page
│   │   ├── careers/            # Career recommendations & comparison page
│   │   ├── dashboard/          # Student Command Dashboard page
│   │   ├── forgot-password/    # Password recovery request page
│   │   ├── login/              # Sign in page with demo credentials
│   │   ├── mock-interview/     # AI Mock Interview Simulator page
│   │   ├── notifications/      # Notification & activity feed page
│   │   ├── profile/            # Student academic profile page
│   │   ├── readiness/          # Multi-dimensional Job Readiness page
│   │   ├── register/           # Registration with academic fields
│   │   ├── reset-password/     # Password reset execution page
│   │   ├── resume/             # AI Resume ATS Analyzer page
│   │   ├── roadmap/            # Personalized Learning Roadmap page
│   │   ├── settings/           # Student account & theme settings page
│   │   ├── skill-gap/          # Skill Gap Matrix analysis page
│   │   ├── skills/             # Student skill inventory page
│   │   ├── globals.css         # Tailwind base, dark/light CSS variables
│   │   ├── layout.tsx          # Root HTML layout with ThemeProvider
│   │   └── page.tsx            # High-conversion public SaaS landing page
│   ├── components/
│   │   ├── AppShell.tsx        # Responsive layout shell with navbar & sidebar
│   │   ├── Navbar.tsx          # Top navigation bar
│   │   ├── NotificationsDropdown.tsx # Real-time notification bell dropdown
│   │   ├── Sidebar.tsx         # Collapsible sidebar for Student & Admin RBAC
│   │   ├── ThemeProvider.tsx   # Next-themes wrapper
│   │   ├── ThemeToggle.tsx     # Dark / Light theme toggle button
│   │   └── UserNav.tsx         # User avatar menu & sign out
│   ├── lib/
│   │   ├── auth.ts             # JWT signing, password hashing & verification
│   │   ├── edgeAuth.ts         # Edge-compatible session decoder for middleware
│   │   ├── prisma.ts           # Singleton Prisma Client instance
│   │   ├── serverAuth.ts       # Server Component session extractor
│   │   └── utils.ts            # Class merge (clsx + twMerge) and date utilities
│   ├── middleware.ts           # Next.js Route Protection & RBAC enforcement
│   └── services/
│       ├── aiService.ts        # External LLM adapter & heuristic fallback
│       ├── careerMatcher.ts    # Career matching & gap analysis algorithms
│       ├── mockInterviewEvaluator.ts # Technical & communication evaluator
│       ├── readinessCalculator.ts # 6-pillar Job Readiness Index calculator
│       ├── resumeAnalyzer.ts   # Document parser (PDF/DOCX) & ATS auditor
│       └── roadmapGenerator.ts # Stage generator addressing missing competencies
├── .env.example                # Documented environment configuration template
├── package.json                # Project dependencies and npm scripts
├── tailwind.config.ts          # Tailwind CSS theme configuration
└── tsconfig.json               # TypeScript configuration
```

---

## 🔒 Security & RBAC Enforcement

- **Password Hashing**: Stored exclusively as 10-round salted bcrypt hashes; never exposed in database records or API responses.
- **Role-Based Access Control**:
  - `STUDENT`: Permitted to access `/dashboard`, `/profile`, `/resume`, `/skills`, `/careers`, `/skill-gap`, `/roadmap`, `/readiness`, `/mock-interview`, `/assistant`, `/notifications`, `/settings`, and `/api/student/*`.
  - `ADMIN`: Permitted to access `/admin/*` management tools and `/api/admin/*`.
  - Unauthorized role access returns HTTP 403 Forbidden or redirects to `/dashboard`.
  - Unauthenticated access redirects automatically to `/login?callbackUrl=...`.
- **File Validation**:
  - Validates document MIME types (`application/pdf`, `application/vnd.openxmlformats-officedocument.wordprocessingml.document`).
  - Strict 5MB file size limit with sanitized unique filenames on disk.
- **Input Validation**: All API route inputs parsed and sanitized with Zod schemas.

---

## 🔮 Future Enhancements

1. **Audio & Video Mock Interviews**: Integrate browser WebRTC and Whisper Speech-to-Text for live audio responses and facial confidence analysis.
2. **GitHub Repository Crawler**: Automatically scan student public repositories and extract commit frequencies, test coverage, and language distributions.
3. **LinkedIn Profile Importer**: OAuth integration to sync work experiences and education directly.
4. **Employer Portal**: A 3rd role for corporate recruiters to search students by verified skill readiness tiers and schedule interviews.
