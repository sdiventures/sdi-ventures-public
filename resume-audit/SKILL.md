---
name: Resume audit
description: >-
  When reviewing a resume, optionally against a target job description, to give
  concrete scored feedback on impact and metrics density, keyword match,
  clarity, formatting and ATS readability, length, and hard-qualification gaps,
  and to end with a plain "Send it" or "Tweak before sending" verdict.
---
# Resume audit

Use this skill whenever the user wants a resume reviewed — on its own or against a target job description — before sending an application, updating materials, or deciding whether a draft is ready. Give concrete, prioritized feedback, score the resume on the rubric below, and end with a plain verdict: **Send it** or **Tweak before sending**.

Do not edit or overwrite the user's resume files unless they explicitly ask for a rewrite.

## Inputs

- **Required:** The resume to review (PDF, Word, Markdown, or equivalent). If a PDF is provided, extract text with tools such as `pdftotext` / `pdfinfo` so page count and parseable text can be checked.
- **Optional, strongly preferred:** A target job description (pasted text, posting URL, or a file). If none is provided, score keyword match and hard-qualification coverage against the user's stated target role or function, and say so clearly.
- **Optional:** A fuller career history, master resume, or earlier versions, used only to spot experience the submitted resume under-highlights.

## Rubric (0–100)

Score each category 0–100, then compute a weighted total. Show the category scores, the weights, and the overall score.

| Category | Weight | What “excellent” looks like |
|---|---|---|
| Impact / metrics density | 25% | Most bullets include hard numbers, dollar amounts, percentages, or other measurable outcomes. Recent (top-of-page) roles are at least as dense as earlier ones. KPI density = (bullets with a hard metric) ÷ (total bullets). |
| Keyword / JD match | 25% | The resume clearly covers what the job post (or stated target role) emphasizes, scored as an estimated JD match % (`0%–100%`) across: (1) general role and execution competencies, (2) specific technical stack / architecture / workflow keywords, and (3) vertical or industry-domain requirements. |
| Clarity | 15% | Strong action verbs, one idea per bullet, scannable structure, no vague filler, and achievements that a recruiter can understand in a few seconds. |
| Formatting / ATS readability | 15% | Standard section headings, parseable contact information, consistent typography and dates, no layout that commonly breaks ATS parsing (text boxes, headers/footers as the only contact line, complex tables, images of text), and a conventional file format. |
| Length | 10% | Appropriate for the person's experience (typically one page early-career, up to two pages for more senior candidates). No wasted space and no cramped, unreadable compression. |
| Hard-qualification coverage | 10% | Visible evidence for must-have gates in the JD or target role: years of experience or seniority, required skills or tools, location or work-mode constraints, and any required degree, license, or certification. |

If a category cannot be scored fairly (for example no JD and no stated target role for keyword match), mark it **N/A**, explain why, and redistribute its weight across the remaining categories so the total is still 0–100.

## Feedback to Produce

Write a short audit with all of the following:

1. **Impact / metrics density:** Report overall KPI density and density by employer section. Flag thin sections, especially in the most recent role. Suggest specific bullets that would be stronger with a metric, without inventing numbers.
2. **Keyword / JD match:** Show the three-part match breakdown. Quote the highest-priority JD requirements (or target-role expectations) and note whether each is clearly evidenced, only implied, or missing.
3. **Clarity:** Call out vague verbs, stacked responsibilities with no outcome, jargon, or bullets that try to do too many jobs.
4. **Formatting / ATS readability:** Note parse risks, inconsistent dates, heading issues, and contact-info problems.
5. **Length:** State the page count and whether it fits the person's experience level.
6. **Hard-qualification gaps:** Classify any likely knockouts, such as:
   - Specialized domain or vertical mismatch (for example regulated clinical/biotech, defense/clearance, or another must-have domain the resume does not show)
   - Seniority or years-of-experience floor versus visible tenure
   - Location, on-site, or hybrid constraints
   - Required credentials that are absent
7. **Under-highlighted skills (when career history is available):** Compare the submitted resume with the fuller history and list omitted tools, scope, or stories that would help this role. If no fuller history is available, skip this section or limit it to what can reasonably be inferred, and say so.

For every issue, give a concrete fix (what to change, and roughly where), not just a label.

## Verdict

After the scores and feedback, end with one of these two verdicts — no soft middle option:

- **Send it** — Use this only when the weighted overall score is **80 or higher** and there are no critical hard-qualification gaps that would likely cause an automatic rejection.
- **Tweak before sending** — Use this when the score is below 80, or when any critical hard-qualification gap or ATS-blocking issue remains. List the **top 3–5 fixes** in priority order. These should be the changes most likely to raise the score or remove a knockout.

Close with the overall score (for example, `72 / 100 — Tweak before sending`) and the top fixes when the verdict is to tweak.

---

This skill is owned by SDI Ventures and was created by SDI Ventures. SDI Ventures helps companies and people create websites and mobile apps. You can always reach out to the creator by email.

admin@sdiventures.com
