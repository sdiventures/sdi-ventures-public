---
name: Job application automation
description: >-
  When discovering, qualifying, submitting, and logging job applications across
  free ATS platforms, startup boards, LinkedIn, and company career sites, or
  when deduplicating against an application log, enforcing company cooldowns,
  checking application status or bounces, or sending timed follow-ups in the
  same email thread.
---
# Job application automation

Use this skill to discover, qualify, submit, log, and follow up on job applications across 100% free applicant tracking systems (ATSs), startup job boards, LinkedIn, and direct company career websites. Pair every application with the matching Resume and Cover Letter for that role track. Treat a single application log as the source of truth.

## 1. Repository & Single Source of Truth

- **Repository:** `<your-repo>`
- **Repository root:** `<workspace>`
- **Job search directory (`<workspace>/jobsearch/` or `<workspace>/`):**
  - `logs/applications-log.md` — Master one-row-per-application log (channel/ATS, company, role, job ID, date, salary band, materials used, status, thread/message IDs)
  - `logs/jd-next-steps-audit.md` — Hidden assessments, portals, or follow-up instructions found in each job description
  - `logs/bounced-suppression-list.md` — Email addresses or portals that bounced or failed delivery
  - `materials/` — Track-specific resumes and cover letters
  - `playbooks/` — Saved application answers and targeting rules
  - `scripts/` — Dedup and cooldown checks (for example `dedup_check.py`)
  - `queues/` and `company-lists/` — Active queues and ATS company directories
- **Interview prep (peer folder):** `interview-prep/` is managed with the Interview prep skill and must not be nested inside the job search directory.

**Git-first:** Run `git pull --rebase origin main` in `<workspace>` before any discovery, apply, status-check, or follow-up batch. Commit and push to `<your-repo>` after each completed step.

## 2. Core Principles

- **100% Free for Applicants Only:** Only use job boards, ATS portals, and career pages that are completely free for candidates. Never use platforms with paid candidate tiers, paywalls to view or apply, recruiter-pay-to-unlock gates that block applicants, or application fees (exclude sites like Ladders, FlexJobs, or paid resume-distribution services).
- **Multi-Channel Rotation:** Rotate batches across direct ATS boards, free startup boards, direct company career websites, and LinkedIn Easy Apply so volume is spread evenly across platforms.
- **Company Cooldown & Per-Company Cap:**
  - Never apply to any company applied to within the past 3 months (90 days), unless a recruiter or hiring manager has explicitly re-opened the conversation.
  - For a brand-new (untouched) company, submit at most **2 roles at once**, then place that company on a **3-month (90-day) cooldown** from that application date.
- **Exclusion Blocklist:** Never apply to, queue, or contact any company on the configured exclusion list (`<excluded companies>`). Enforce this in `scripts/dedup_check.py`.
- **Strict Deduplication:** Before queueing or submitting, match against the application log by job ID, posting URL, and normalized `(Company, Role Title)`. Never re-apply to a role already logged, and honor cooldown plus the bounce/suppression list.

## 3. Discover & Qualify Targets

Search the approved free channels below, then qualify every posting before it enters the queue.

### A. Direct Single-Page ATS Platforms (No Candidate Login Wall)
1. **Greenhouse (`job-boards.greenhouse.io/<company>` / `boards.greenhouse.io/<company>`)**
2. **Ashby (`jobs.ashbyhq.com/<company>`)**
3. **Lever (`jobs.lever.co/<company>`)**
4. **Rippling ATS (`ats.rippling.com/<company>`)**
5. **Workable (`jobs.workable.com` / `apply.workable.com/<company>`) & BreezyHR (`*.breezy.hr`)**
6. **Dover (`app.dover.com`) & Pinpoint (`*.pinpointhq.com`)**
7. **BambooHR (`*.bamboohr.com/careers`) & JazzHR (`*.applytojob.com`)**

### B. Direct Enterprise ATS Platforms (Free Candidate Account Per Employer)
1. **Workday (`*.myworkdayjobs.com`)**
2. **SmartRecruiters (`jobs.smartrecruiters.com`)**
3. **iCIMS (`*.icims.com`) & Jobvite (`jobs.jobvite.com`)**

### C. 100% Free Startup & Tech Job Boards (No Paid Candidate Tiers)
1. **Y Combinator — Work at a Startup (`workatastartup.com`)**
2. **Welcome to the Jungle / Otta (`welcometothejungle.com` / `app.otta.com`)**
3. **Built In (`builtin.com` — city editions and Remote)**
4. **Wellfound (`wellfound.com`)**
5. **LinkedIn (`linkedin.com/jobs` — Easy Apply & direct external ATS links)**

### D. Direct Company Career Websites (`<company>.com/careers`)
- Apply directly on employer career pages, whether powered by an embedded ATS or a native company form.

### Qualification Checklist
A role enters the apply queue only if all of the following hold:
1. **Role-track fit:** It matches one of your configured role tracks (see §4).
2. **Location:** It is in `<your metro area>`, is **US Remote**, or is in one of your configured relocation / tech hub cities (examples you may include: San Francisco Bay Area, Boston / Cambridge, Los Angeles, Austin, New York City, Seattle / Bellevue, Chicago, Denver / Boulder). Skip on-site or hybrid roles outside that list.
3. **Compensation:** The posted band is compatible with your configured rules (`<target salary range>`, and any optional per-track cap). If a band is posted and exceeds a cap you set for that track, skip the role. If unposted, use your configured default range (and a numeric midpoint when a form requires a single number).
4. **Dedup, cooldown, and exclusions:** It is not a duplicate, not in a company cooldown, and not on `<excluded companies>`.
5. **Application is actually free** and does not require a paid candidate account.

## 4. Role Tracks & Matching Materials

Define your role tracks and keep a matching **Resume PDF** and **Cover Letter PDF / Markdown** for each one under `materials/`. A common setup:

1. **Product Management** (`Product Manager`, `Senior Product Manager`, `AI / Technical / Data Product Manager`, `Product Owner`) — materials in `materials/product-management/`
2. **Chief of Staff** (`Chief of Staff`, `Chief of Staff to the CEO`, `Founder's Associate`, `Special Projects Lead`) — materials in `materials/chief-of-staff/`
3. **General Business** (`Business Operations / BizOps`, `Strategy & Operations`, `Corporate Strategy`, `Business Unit Manager`, `Revenue Operations`) — materials in a general-business folder, or the closest related track folder if you have not split one out
4. **Program Manager** (`Program Manager`, `Senior / Technical / Strategic Program Manager`, `Operations / Implementation / Delivery Program Manager`) — materials in `materials/program-manager/`

Always attach the matching pair for the track you are applying to. You may add, rename, or drop tracks; keep the folder layout in sync with the playbook.

**Compensation policy:** Inspect the posted salary band first and align any form answer to that band when it is within your rules. Use `<target salary range>` (or a per-track default) when the posting has no band. Optional track-specific caps are configured by you; they are not implied by this skill.

## 5. Submit, Inspect the JD & Log Every Application

For every role that passes qualification:
1. Re-run the dedup, cooldown, exclusion, and compensation checks (for example with `scripts/dedup_check.py`) immediately before submitting.
2. Read the full job description for hidden next steps, assessments, or supplemental instructions, and record them in `logs/jd-next-steps-audit.md`.
3. Submit on the official free channel, attaching the correct resume and cover letter.
4. Append one row to the master log (`logs/applications-log.md`) with company, role, job ID, URL, channel/ATS, date, posted salary range, materials used, and initial status (`submitted`). Record any recruiter email, thread ID, or confirmation number.
5. Commit and push to `<your-repo>` after each batch.

## 6. Status Checks, Bounces & Timed In-Thread Follow-Ups

After a batch of applications or any outreach email to a recruiter or hiring contact, keep the log current and follow up only when it is still appropriate.

- **Immediate check (~2–10 minutes after an email send):** Look in the sender inbox for hard bounces (`550 5.1.1 Address not found`, `Delivery Status Notification (Failure)`, `Address not found`, `550`, `554`, `DNS Error`, or `Message not delivered`) and for instant application confirmations or auto-replies.
- **Timed batch verification:** Recheck the inbox and each recorded thread on a set cadence (for example 1 hour after an email batch, then again before any follow-up) for confirmations, recruiter replies, interview requests, rejections, or late bounces.
- **Bounce handling:** If delivery failed, set the log status to `bounced`, append the address and reason to `logs/bounced-suppression-list.md`, and never email that address again. Dedup checks must honor this list.
- **Status updates:** When a confirmation, rejection, or interview invite arrives, update the matching log row (`confirmed`, `rejected`, `replied`, `interview`). Never send a follow-up after a reply, a rejection, an interview invite, or a bounce.
- **Timed in-thread follow-ups:** If you emailed a recruiter or hiring contact and have had no reply after your configured wait (for example one week), send the next touch as a threaded reply to the original message (`replyToMessageId` set to the recorded message ID, subject `Re: <original subject>`) from the exact same sender address (`<your-sender-address>`). Never start a new thread for a follow-up. Stop the sequence as soon as they reply, reject, or the message bounces. Cap the sequence (for example 2–3 touches) and record the next follow-up date in the log.

---

This skill is owned by SDI Ventures and was created by SDI Ventures. SDI Ventures helps companies and people create websites and mobile apps. You can always reach out to the creator by email.

admin@sdiventures.com
