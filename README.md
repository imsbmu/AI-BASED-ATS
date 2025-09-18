ResuMind — AI Resume Analyzer
AI-powered resume analyzer that securely uploads resumes, reads a job description, generates ATS-style scores and structured feedback using free client-side AI via Puter.js, and presents results in a responsive, production-ready UI.

Features
Serverless architecture: auth, storage, and AI from the frontend via Puter.js.

Secure sign-in/out with persistent session handling.

Resume upload with PDF-to-image preview and metadata capture.

Job description input with configurable fields.

AI evaluation: ATS score + category feedback (tone/style, content, structure, skills).

Clean UI: responsive grid, cards, and feedback detail page.

Data utilities: list user submissions, wipe/reset demo data.

Type-safe codebase with TypeScript and centralized state via Zustand.

Tech stack
Frontend: React, React Router v7, TypeScript, Tailwind CSS v4, Vite.

State: Zustand (global store for Puter integration and app state).

Cloud & AI: Puter.js (auth, storage, AI).

Utilities: PDF rendering/preview worker, class utilities (clsx, tailwind-merge).

Getting started
Prerequisites

Node.js 18+ and npm or pnpm or yarn.

A Puter account for local testing.

Installation

Clone the repository.

Install dependencies with preferred package manager.

Copy provided styles/assets into public and app CSS if using a kit.

Start the dev server at the indicated localhost port.

Environment

No server environment variables required for core flows.

Puter.js is loaded via a client-side script tag in the root layout.

If adding custom guards or quotas, create a local config file and import where needed.

Run scripts
dev: Start Vite dev server with HMR.

build: Production build.

preview: Preview the production build locally.

lint/format (optional): Run linters/formatters if configured.

Project structure
app/: application code

routes/: route files (home, auth, upload, review)

components/: UI units (Navbar, ResumeCard, ScoreCircle, Feedback sections)

lib/: Puter store/wrapper and helpers

types/: global and domain typings

constants/: mock data and prompt schemas for development

public/: static assets (icons, images, favicons)

tailwind config + app.css: theme tokens, utilities, component classes

Core flows
Authentication

Sign-in/out handled via a centralized store that wraps Puter auth.

Loading/auth states exposed via hooks for top-level UX.

Guarded routes redirect unauthenticated users to auth with return paths.

Upload

Form captures candidate info, job details, and PDF file.

Files uploaded to Puter FS with progress and error states.

PDF preview generated as image for card display.

AI evaluation

Submit resume context + job description to AI endpoint via Puter.

Strict response schema: overall score and per-category feedback.

Response parsing includes validation and safe fallbacks.

Data listing and detail

Home lists user submissions with thumbnails and scores.

Clicking a card opens the review page with full feedback.

Wipe/reset clears demo data quickly during development.

Configuration
Prompt schema

Keep prompts versioned and centralized; include expected JSON shape.

Add guards for missing or malformed fields; provide defaults.

File constraints

Enforce max file size and supported types (e.g., PDF).

Show progressive loading indicators for previews and uploads.

UI/Styling

Tailwind v4 utilities plus a small set of component classes (e.g., primary button, text gradient).

ScoreCircle rendered as a controlled SVG component for ATS score.

Deployment
Build using the production script.

Deploy static assets to a static host or CDN.

Ensure the Puter script loads on production domains and test auth/storage/AI end-to-end.

Provide a short runbook for redeploys and resets.
