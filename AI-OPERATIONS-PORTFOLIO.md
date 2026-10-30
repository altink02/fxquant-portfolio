# AI Operations — Selected Project Examples

**Altin Kalludra** · [GitHub profile](https://github.com/altink02) · [Full portfolio](PORTFOLIO.md)

This page highlights three projects relevant to an **AI Operations Specialist** role: practical automation, AI-assisted workflows, APIs, background jobs, human review, and operational safeguards.

**[Browse the permanent visual portfolio and screenshots](https://altink02.github.io/localcanvas-ai/portfolio/)** — available independently of hosted application demos.

> **Review note:** These public repositories are project case studies with screenshots and architecture notes. The application source is kept private. Hosted demonstrations and static showcases are identified separately below. Features described as planned or incomplete are not presented as working.

## Start here — 3 examples

| Project | Relevant workflow | Evidence / how to review |
| --- | --- | --- |
| [SocialMedia Manager](https://github.com/altink02/socialmedia-manager) | Content idea → structured script → rendered video → approval → publishing queue | [Interactive mock-mode studio](https://socialmedia-manager-eight.vercel.app/studio) · [Screenshots](https://github.com/altink02/socialmedia-manager#screenshots) |
| [AI Call Agent](https://github.com/altink02/ai-call-agent) | Agent configuration → API/tool permissions → background jobs and compliance checks | [Backend case study](https://github.com/altink02/ai-call-agent#what-is-verified) · [Interface screenshots](https://github.com/altink02/ai-call-agent#screenshots) |
| [LocalCanvas AI](https://github.com/altink02/localcanvas-ai) | Image upload → text detection → human review/correction → editable text layers | [Editor/screenshots](https://github.com/altink02/localcanvas-ai#screenshots) · [Static showcase](https://altink02.github.io/localcanvas-ai/) |

## 1. SocialMedia Manager — Workflow automation and monitoring

**Problem:** Moving from a content idea to a finished video and scheduled social post normally involves repetitive manual handoffs.

**What the project demonstrates:**
- A staged workflow for script and scene planning, FFmpeg video rendering, thumbnails, subtitles, and a review queue.
- Human approval before publishing, plus topic-bank, scheduling, and controlled automation modes.
- Individual outcomes for Facebook, Instagram, and YouTube adapters, with retry/idempotency design and guardrails such as daily caps and quiet hours.
- A public studio using a **mock-mode publishing and AI provider**; it includes a read-only snapshot of media produced by the separate rendering pipeline.

**Inspect:** [Studio demo](https://socialmedia-manager-eight.vercel.app/studio) · [Architecture](https://github.com/altink02/socialmedia-manager/blob/master/ARCHITECTURE.md) · [Studio screenshot](https://github.com/altink02/socialmedia-manager/blob/master/screenshots/02-studio.png)

**Boundary:** The hosted demo does **not** send live posts to external accounts or render new media in its serverless environment.

## 2. AI Call Agent — AI assistants, APIs, and reliable background workflows

**Problem:** An AI-assisted contact workflow needs configurable agents, permission checks, auditability, and reliable handling of failed jobs.

**What the project demonstrates:**
- A Python/FastAPI backend for multilingual agent configuration, versioning, a text-mode agent workflow, and tool permissions.
- Background jobs with retry handling and HMAC-signed webhooks; consent and do-not-call checks are enforced outside the language model.
- A documented test and evaluation approach, including simulated providers that are explicitly labeled as simulated.
- A Next.js operations console for agents, providers, knowledge, and system status.

**Inspect:** [Agent case study](https://github.com/altink02/ai-call-agent) · [Agent screenshot](https://github.com/altink02/ai-call-agent/blob/main/screenshots/02-agents.png) · [Tool catalogue screenshot](https://github.com/altink02/ai-call-agent/blob/main/screenshots/08-tools.png)

**Boundary:** The backend and console are documented; the realtime voice worker and actual WebRTC/SIP calling are **not built**. This is **not** presented as a working phone bot.

## 3. LocalCanvas AI — Human-in-the-loop AI processing

**Problem:** Editing text embedded in images requires detection, error review, and a repeatable non-destructive editing workflow.

**What the project demonstrates:**
- Local OCR-based text detection, confidence review, manual correction, and replacement with editable text.
- An application pipeline involving a web app, API, object storage, and a Python AI worker.
- Reviewable project revisions and a workflow that preserves original image files.

**Inspect:** [Project case study](https://github.com/altink02/localcanvas-ai) · [Text-in-image screenshot](https://github.com/altink02/localcanvas-ai/blob/main/screenshots/10-text-in-image.png) · [Static showcase](https://altink02.github.io/localcanvas-ai/)

**Boundary:** This is a local/private implementation, not a public interactive editor. Object/text removal is blocked by model licensing; the documented text-recognition and correction workflow is the relevant completed portion.

---

### How these projects relate to AI operations

- **Automation design:** multi-step processes, queues, retries, status tracking, and approval checkpoints.
- **AI workflows:** prompts, agent configuration, simulated versus real provider boundaries, and human oversight.
- **Integration fundamentals:** HTTP APIs, webhooks, and application-to-service communication.
- **Practical operations:** failure handling, observability, access controls, and clear documentation.

**Important:** These projects do **not** claim production experience with Zapier, Make, or n8n. They demonstrate related workflow-engineering concepts through custom applications. Those platforms are a separate skill to demonstrate if used.

For a quick review, start with **SocialMedia Manager's interactive studio**, then explore **AI Call Agent's screenshots and architecture**.
