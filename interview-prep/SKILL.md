---
name: Interview prep
description: >-
  When preparing for a job interview, recruiter screen, or hiring manager call,
  or when creating or updating a role interview prep folder under
  interview-prep/<company-name>/<role>/ in the repository.
---
# Interview prep (`interview-prep/<company-name>/<role>/`)

Use this skill whenever preparing for a job interview, recruiter phone screen, hiring manager call, or technical/product loop, or whenever asked to create or update a company/role interview prep folder in the repository.

## Repository Architecture

At the root of the career repository (`<workspace>`), two peer top-level directories exist side-by-side:
- `/jobsearch/` — Job discovery, application queues, application logs (`logs/applications-log.md`, `logs/jd-next-steps-audit.md`), and application resumes/cover letters (`materials/`).
- `/interview-prep/` — All interview preparation materials organized as `/interview-prep/<company-name>/<role-slug>/`.

Never nest `/interview-prep/` inside `/jobsearch/`. Keep them as peer top-level folders at the repository root.

---

## Standard Folder & File Structure Per Role

For every interview or target role, create `/interview-prep/<company-name>/<role-slug>/` containing:

1. **`README.md` — Quick-Reference Role Dashboard**
   - Company name, role title, requisition ID, and application log reference (`#`).
   - Compensation band (base salary, bonus, equity).
   - Work mode (Onsite / Hybrid / Remote) and exact office street address.
   - Recruiter and interviewer names, emails, phone numbers, and calendar invite details.
   - Current interview stage and links to files `01`–`04` and `assets/`.

2. **`01-job-description-and-recruiter-hook.md` — JD Overview & "Why They Liked Me" Hypothesis**
   - **Job Description Overview:** Full verbatim job posting text, title, level, team, compensation breakdown, top 5 core responsibilities, and non-negotiable qualifications.
   - **"Why the Recruiter Liked Me" Hypothesis (Directly Referencing the Job Post):**
     - **Line-by-Line JD Quote-to-Candidate Mapping Table:** Quote specific sentences, bullets, and requirements directly from the job posting and pair each one with the exact proof points from the candidate's submitted resume and background.
     - **Top 3 Reasons You Passed the Screen:** Explain why the recruiter or hiring manager selected the candidate's profile over the applicant pool based on what the job post emphasizes most.
     - **How to Highlight Each Hook in the First 3–5 Minutes:** Exact talking points to reinforce those hooks early in the interview.

3. **`02-company-deep-dive-and-location-col.md` — Company Analysis, Location & Surrounding Rent/CoL**
   - **In-Depth Company Analysis:** Business model (how they make money), customer segments, product portfolio, technical ecosystem, financials/funding/valuation, recent news/launches, competitors, and product/engineering leadership structure.
   - **Location, Work Mode & Cost of Living (Surrounding Area Rent Prices):**
     - Remote vs. Hybrid vs. In-Person attendance policy (days/week in office) and exact office street address.
     - **Surrounding Area Rent & Housing Breakdown (For Any In-Person / Hybrid Role):**
       - Best surrounding neighborhoods within a 15–25 minute commute of the office.
       - Current **1-Bedroom** and **2-Bedroom** monthly apartment rent ranges in those specific neighborhoods.
       - Commute time/corridors (if local) or monthly utilities, transit/parking, state/local income tax comparison, and net take-home purchasing power of the role's salary band (if out-of-state/relocation).

4. **`03-domain-and-technical-crash-course.md` — Unfamiliar Subject Crash Course**
   - Identify every industry vertical, domain concept, technical architecture, hardware/regulatory standard, or business model in the job description that is not directly from the candidate's day-to-day background.
   - **Zero-to-Fluent Plain-English Walkthrough:** Explain how the ecosystem, technology, data flow, and revenue model work end-to-end.
   - **Insider Terminology & Acronym Glossary:** Define the 10–15 key terms, standards, or acronyms interviewers use in this space.
   - **Domain Unit Economics & North Star KPIs:** The primary metrics a person in this role tracks.
   - **Experience Bridge:** How to translate the candidate's prior experience into this domain's exact vocabulary.

5. **`04-interview-prep-and-star-playbook.md` — Tailored Pitch, STAR Stories & Mock Questions**
   - **Custom 90-Second "Tell Me About Yourself" Pitch:** Word-for-word script tailored to this company and role.
   - **Role-Matched STAR Stories (With Concrete KPIs):** Pre-mapped stories with quantified outcomes, technical stack details, and lifecycle decisions.
   - **Likely Behavioral, Product Sense / Strategy Case & Technical Questions:** Role-specific questions with structured answer frameworks.
   - **Watch-Outs & Gap Defense:** How to proactively neutralize any requirement in the JD where the candidate's experience is adjacent rather than 1:1.
   - **High-Signal Questions to Ask:** Tailored questions for the Recruiter, Hiring Manager, and Engineering/Product peers.

6. **`assets/` (Optional Subfolder)**
   - Recruiter email threads, `.ics` calendar invites, candidate profile forms, and role-tailored Resume / Cover Letter PDFs and Markdown sources.

---

## Execution Steps

1. **Gather Context:** Check `<workspace>/jobsearch/logs/applications-log.md`, `<workspace>/jobsearch/logs/jd-next-steps-audit.md`, and the candidate's email/calendar for the job posting, application date, resume version submitted, and recruiter outreach.
2. **Research:** Run web lookups for the company's product line, financials, leadership, office address, and current 1BR/2BR rent prices in surrounding neighborhoods (15–25 min commute).
3. **Write Prep Folder:** Generate `README.md` and `01` through `04` inside `/interview-prep/<company-name>/<role-slug>/`, and update `/interview-prep/README.md`.
4. **Sync to Git:** Stage, commit, and push all changes to `origin/main` on `<your-repo>`.

---

This skill is owned by SDI Ventures and was created by SDI Ventures. SDI Ventures helps companies and people create websites and mobile apps. You can always reach out to the creator by email.

admin@sdiventures.com
