# Capstone Proposal

**Course:** Building AI-Powered Applications  
**Team Name:** Synapse Squad  
**Project Title:** AI-Powered CV Generator Assistant  
**Date:** 17.10.2025

---

## 1. Problem Statement

### The Problem

Creating an effective and professional CV is a major challenge for students and early-career professionals. Many struggle to present their achievements clearly, use the right tone, or tailor their experience to specific job descriptions. The tools most people rely on — static Word templates or basic online CV builders — often produce generic, one-size-fits-all results that fail to stand out.

As a result, users spend hours editing their CVs manually, uncertain whether their formatting, keywords, or structure meet modern hiring standards like Applicant Tracking Systems (ATS). This frustration often leads to missed opportunities and reduced confidence in job applications.

Our AI-Powered CV Generator Assistant aims to solve this problem by using intelligent text generation and adaptive templates. It helps users instantly create polished, tailored CVs optimized for each job description — saving time, improving quality, and increasing their chances of success in the hiring process.

---

### Scope

**What's In Scope:**
- AI-powered CV text generation (summary, experience, skills sections)
- Job-specific tailoring based on job description input
- Modern, exportable CV templates (PDF/Word)
- Editing and version history for multiple CVs

**What's Out of Scope (but maybe future work):**
- Full portfolio or cover letter generator
- Job search or application tracking features

**Why This Scope Makes Sense:**
These core features can be built and evaluated within a semester while clearly showcasing AI text generation, structured output, and user interface design.

---

## 2. Target Users

### Primary User Persona

**User Type:** Everyone

**Demographics:**
- Age range: 17-*
- Technical proficiency: Comfortable with web apps but not developers
- Context of use: Desktop-first web application, used before applying for jobs or internships

**User Needs:**
1. **Need #1:** Generate a professional CV quickly
   - Why it matters: Saves time during job application periods
   - Current workaround: Editing Word templates manually

2. **Need #2:** Tailor CV to a specific job posting
   - Why it matters: Increases hiring chances
   - Current workaround: Manually rewriting sections for each role

3. **Need #3:** Improve language and presentation quality
   - Why it matters: Many non-native English speakers struggle with tone and
   - Current workaround: Asking friends or ChatGPT informally

**User Pain Points:**
- Difficulty choosing what to include/exclude
- Poor formatting or inconsistent structure
- Uncertainty about how to highlight achievements effectively


## 3. Success Criteria

### Product Success Metrics

**How we'll know our solution works:**

1. **Metric #1:** Task completion time
   - Target: Reduce from 30 → <5 minutes
   - Measurement method: User task timing

2. **Metric #2:** Output helpfulness
   - Target: 90% rated “helpful” or “very helpful”
   - Measurement method: Post-task survey

3. **Metric #3:** User satisfaction
   - Target: ≥4/5 average
   - Measurement method: Exit survey

4. **Metric #4:** Engagement
   - Target: ≥5 active testers use app 3+ times
   - Measurement method: Usage analytics

5. **Metric #5:** Cost efficiency
   - Target: <$0.10 per generated CV
   - Measurement method: API cost logs

---

### Technical Success Criteria

**Minimum viable performance:**
- Response latency: <4s per generation (p95)
- Availability: 95% uptime
- Error rate: <5% failed requests
- Cost per user: <$0.10/session

---


### Technical Risks

**Risk #1: API Rate Limits**
- Likelihood: Medium
- Impact: Medium/Low
- Mitigation: Cache outputs, retry logic

**Risk #2: LLM output inconsistency**
- Likelihood: High
- Impact: High
- Mitigation:
  - Use strict prompt templates
  - Few-shot examples

**Risk #3: Response Latency**
- Likelihood: Medium
- Impact: Medium
- Mitigation: Stream responses, pre-process templates

---

### Product Risks

**Risk #1: Users don’t find tool useful**
- Likelihood: Medium
- Impact: High
- Mitigation:
  - Early user testing
  - Iterative feedback

**Risk #2: Scope Creep**
- Likelihood: Medium
- Impact: Medium
- Mitigation: Feature freeze after Week 8

---

### Team Risks

**Risk #1: Unequal Workload Distribution**
- Likelihood: Medium
- Impact: High
- Mitigation:
  - Weekly standup with clear task ownership and progress updates.
  - Track contributions via GitHub (issues, PRs, commits) and use lightweight peer evaluations mid-project.
  - Keep a shared Kanban board (GitHub Projects / Trello) so work is visible.

**Risk #2: Team Member Availability (scheduling conflicts / illness)**
- Likelihood: Medium
- Impact: Medium
- Mitigation:
  - Maintain a shared calendar and agree on core overlap hours.
  - Cross-train at least two members on each critical component (frontend, backend, prompt engineering).
  - Maintain short written runbooks for critical tasks (deploy, test, restore).

**Risk #3: Skill Gaps for Critical Tech (e.g., FastAPI, PDF export, prompt engineering)**
- Likelihood: Medium
- Impact: High
- Mitigation:
  - Early learning sprints and pair-programming sessions (Weeks 1–3).
  - Assign one “owner + backup” per component; share short how-to docs in repo.
  - Use third-party libraries (e.g., pdfkit/reportlab) to reduce low-level implementation risk.


---

### Safety & Ethical Risks

**Risk #1: Prompt Injection / Malicious Input**
- Likelihood: Medium
- Impact: High
- Mitigation:
  - Sanitize and escape user-provided job descriptions and uploads.
  - Keep system prompts immutable and separate from user content; never concatenate raw user content into system-level instructions.
  - Rate-limit and monitor unusual request patterns.

**Risk #2: Bias in AI Outputs (gender, ethnicity, age bias in phrasing/role recommendation)**
- Likelihood: Medium
- Impact: High
- Mitigation:
  - Test outputs with diverse synthetic and real input profiles to detect biased phrasing.
  - Add post-generation filters and neutral phrasing templates; surface flagged suggestions to users rather than auto-applying.
  - Provide a clear disclaimer and editing UI so users can review and correct outputs.

**Risk #3: Privacy / Data Leakage (storing personal PII unintentionally)**
- Likelihood: Low
- Impact: High
- Mitigation:
  - Do not store raw PII by default. If storing is required (e.g., user wants to save CVs), encrypt stored CVs and log minimal metadata.
  - Provide clear consent UI for any saved data and an easy delete flow.
  - Anonymize analytics and rotate/secure API keys and secrets.

---

### Contingency Plans

**If our primary model is unavailable:**
- Switch to a lower-cost fallback (e.g., GPT-3.5-turbo) with a displayed “degraded quality” notice. Cache recent successful prompts/responses to reduce immediate dependence.

**If we can't recruit enough user testers:**
- Use synthetic evaluation with a curated golden dataset of job descriptions + candidate profiles and run internal heuristic checks and peer reviews.

**If we fall behind schedule:**
- Cut lower-priority features in this order: (1) multi-template design gallery, (2) version history UI, (3) advanced ATS-scoring analytics. Keep core flow: profile input → tailored CV generation → PDF export.


---


**Do we need IRB approval?**
- [ ] Yes - we're collecting sensitive data or working with minors
- [X] No - but we've completed the IRB Light Checklist (see `docs/irb-checklist.md`)

**Data we'll collect:**
- Task completion times, task success/failure, post-task surveys (Likert), optional screen recordings (with consent), anonymized system logs (latency/errors).
- Storage duration: until end of semester + 3 months for analysis, then deleted.
- Access: Only team members; raw data stored in password-protected folder.

**User consent:**
- [X] We've adapted the course consent template
- [X] Users can withdraw at any time
- [X] We've explained data usage clearly

---

### Recruitment Plan

**Target participants:**
- Number: 5–8 users per testing round
- Criteria: Students or recent grads actively applying for jobs; no prior experience required
- Where: Course announcements, student Slack groups, campus mailing lists

**Compensation:**
- Coffee

**Timeline:**
- Week 3-4: Recruit first batch (3-5 users)
**Session Structure (45-60 minutes):**

1. **Introduction (5 min)**
   - Explain study purpose and get consent; describe think-aloud protocol.

2. **Background Questions (5 min)**
   - Current CV workflow, frequency of updates, biggest pain points.

3. **Task 1: Create a baseline CV from profile (10 min)**
   - Scenario: "Produce a professional CV using the profile we uploaded."
   - Success: User is satisfied with structure and primary wording (self-reported).
   - Observe: Time, edits made, confusion points.

4. **Task 2: Tailor CV to a provided job description (10 min)**
   - Scenario: "Tailor the CV to this specific job posting using keyword optimization."
   - Success: User identifies appropriate role-specific bullets present.
   - Observe: Time, perceived relevance.

5. **Task 3: Export and review (10 min)**
   - Scenario: "Export as PDF and make manual edits if necessary."
   - Success: User completes export and can make one key edit quickly.
   - Observe: Export issues, formatting complaints.

6. **Post-Task Questions (10 min)**
   - What worked? What was confusing? Would you use this? Rate 1–5.

7. **Wrap-up (5 min)**
   - Thank participant, provide compensation, ask permission for follow-up.

---

### Data Collection Methods

- [X] Screen recording (with permission)
- [X] Observer notes
- [X] Task completion metrics (time, success rate)
- [X] Post-session survey
- [X] System logs (latency, errors, costs)

**Where data will be stored:**
- Raw notes/recordings: password-protected Google Drive (team only)
- Analysis: anonymized summaries in `docs/user-research/`
- No identifiable data will be committed to public repo

---

### Analysis Plan

**Quantitative:**
- Task completion rate and average time per task
- Error rate (failed exports, generation failures)
- User satisfaction scores (1–5)

**Qualitative:**
- Thematic coding of comments to identify common UX or content issues
- Prioritize fixes based on frequency and impact

**Deliverables:**
- User research summary (Week 8 and Week 12)
- Updated feature priority list
- Input for final case study and demo

---

### Major Milestones

**✅ Milestone 1: Proposal (Week 2)** - YOU ARE HERE
- Submission: 17.10.2025
- Points: 10

**🎯 Milestone 2: Design Review (Week 4)**

---


### Backup Plan

**If we fall behind, we'll cut (in this order):**
1. Multi-template design gallery (visual polish)
2. Version history / CV comparison UI
3. Advanced ATS scoring dashboard

**Core features we won't cut:**
- Profile input → tailored CV generation
- Job-description tailoring / keyword mapping
- PDF export functionality

---


### Team Contract Summary

Our team, **Synapse Squad**, has established a detailed team contract outlining our mission, communication plan, roles, responsibilities, conflict resolution process, and quality standards.  
We are committed to maintaining accountability, collaboration, and professionalism throughout the development of our AI-Powered CV Generator Assistant project.

➡️ See the full contract here: [docs/team-contract.md](./docs/team-contract.md)


---


### Revision History

|    Date    |     Author     |    Changes    |
|------------|----------------|---------------|
| 17.10.2025 | Ana Maisuradze | Initial draft |
| [Date] | [Name] | Added architecture diagram|
| [Date] | All | Final review and approval    |

---
