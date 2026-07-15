# TansJobApply

Working notes and reference files from Tanya Thourani's 2026 job application process. This repo captures the house style rules, a step-by-step submission runbook, the ATS-specific quirks learned while submitting applications, and copies of the CVs/cover letters produced so far.

## Repo structure

```
reference/
  Tanya Thourani_CV_2026_vq.docx        - master CV, names real clients (Visa, Mastercard, Adyen, UK Finance, Deutsche Bank, Vitality)
  Tanya Thourani_CV_2026_nc.docx        - same CV, client names anonymised (use when the target employer conflicts with a named client)
  Tanya_Thourani_Cover_Letter_2026_TEMPLATE.docx - the blank cover letter template; every letter should be built from this
  HOUSE_STYLE.md                        - the standing rules (copy of CLAUDE.md)
applications/
  <Company>/                            - the CV and/or cover letter actually produced for each application
```

## How to submit a new application, step by step

This is the actual procedure to follow end to end, not just a list of quirks. It assumes you already have the job posting open.

1. **Read the JD and decide on the CV version.** Check whether the target employer, or a close competitor of it, appears in the vq CV's named-client list (Visa, Mastercard, Adyen, UK Finance, Deutsche Bank, Vitality). If yes, use `nc`. If no, use `vq`. If genuinely unsure, stop and ask rather than guessing. Being a past direct employer (e.g. Barclays) is not the same as a client conflict and doesn't require switching to `nc`.
2. **Build the cover letter from the template**, not freehand. Open `reference/Tanya_Thourani_Cover_Letter_2026_TEMPLATE.docx`, keep every fixed line verbatim, and fill in only the bracketed sections: the role-specific hook paragraph, the "Your ask / My evidence" table (usually 5 rows, each mapping a real JD requirement to a specific honest CV fact), the bias sentence, the five first-year actions, and the closing lines. Sign off "Regards, Tanya Thourani".
3. **Run the house style check** on every sentence you wrote (not the fixed template text): no em dashes, no AI stock phrasing, no triplet-list crutch, no throat-clearing openers. Read it back and ask whether a recruiter would flag it as AI-written.
4. **Set the page size to A4** (210mm x 297mm) before exporting, since the template file itself is saved in US Letter. Trim text as needed to keep the letter to one page.
5. **Convert to PDF** as the final deliverable, and visually check the render (page count, no overflow, no clipped text) before using it.
6. **Fill out the ATS form.** Use the platform-specific technique notes below for Ashby or Workday. Take a fresh screenshot before any click in a busy multi-field form rather than chaining blind coordinate clicks, since these forms often auto-scroll after typing.
7. **Answer compliance/disclosure questions honestly**, grounded in the real CV. Expect categories like: prior relationship with the employer, relatives or close relationships at the company, Senior Government Official referral or relation, outside business or second-job disclosure (this includes things like a personal content brand, answered "Yes" with a plain description, not "No" by default), and whether the candidate worked at the target's external accounting firm within the last two years (relevant here given the EY background) plus whether that work touched the target company. The exact wording used varies by application and isn't reproduced here; the principle is always to answer factually rather than to optimise the answer.
8. **Ground salary and notice period in a real market check** for the role's seniority and location rather than guessing or reusing a previous figure verbatim, and flag it to Raj if there's no solid data to base it on.
9. **Submit, then immediately take a screenshot of the confirmation page** and share it. This is a standing rule, not optional, and applies every time regardless of platform.
10. **Update the application tracker table below** with the company, role, CV version, cover letter type, and status.

## House style, in short

Full detail is in `reference/HOUSE_STYLE.md`. The short version:

- No em dashes anywhere, no AI stock phrasing ("I'm excited to," "at the intersection of," "leverage," etc.), no triplet-list crutch, no throat-clearing openers. Read cover letters back and ask if a recruiter would flag them as AI-written.
- CV source of truth lives in `Latest_2026` (now mirrored here as `reference/`). Use `vq` by default; switch to `nc` only when the target employer is one of the named clients (or a close competitor) to avoid naming a conflicted party. When unsure, ask before defaulting.
- All documents are A4 portrait (210mm x 297mm / 11906 x 16838 DXA), not US Letter. The raw template file is saved in US Letter, so this needs an explicit override every time it's reused.
- Cover letters are always built from `Tanya_Thourani_Cover_Letter_2026_TEMPLATE.docx`, not written freehand. Fixed lines stay verbatim; only the bracketed sections get filled in per role (hook paragraph, the "Your ask / My evidence" table, the bias sentence, five first-year actions, the closing lines). Sign-off is "Regards, Tanya Thourani" (the raw template's "TT" initials get expanded to the full name).
- After submitting any application through an ATS, take a screenshot of the confirmation page and share it before considering the task done.

## What was learned about specific ATS platforms

### Ashby
- The "Autofill from resume" upload auto-populates name/email; the Resume field is separate from that upload.
- Yes/No screening questions render as buttons with an `_active_` CSS class marking the selected one, not a native radio `checked` state, so selection has to be verified visually or via that class, not via standard form-state assumptions.
- When there's no dedicated cover-letter upload, the free-text "Additional Information" box is where a condensed cover letter goes.
- Final step is an "I confirm I have read the above" checkbox plus a "Submit Application" button.
- React-based date pickers and location comboboxes generally need an actual click on the rendered option element (`[role="option"]`), not just a typed value, or the underlying field never registers a real selection.

### Workday
- Multi-step wizard: My Information, My Experience, Application Questions (1 and 2), Voluntary Disclosures, Review.
- Segmented MM/YYYY date fields corrupt easily. Typing a full string like "08/2025" in one go can garble into nonsense. The reliable method: click the field, press Home to land on the month segment, then send the month digits and year digits as separate `type` calls with no slash characters at all.
- Workday's internal validation state does not reliably update from a native `.value` setter plus a dispatched `input` event, and can also fail to register from a synthetic `type` action if the preceding click didn't truly focus the live input. The fix that consistently worked: explicitly `.focus()` the element (fetched fresh via `getElementById`), then use `document.execCommand('insertText', false, value)`.
- `button.disabled` read via JavaScript can be stale or wrong. A fresh screenshot showing the button visually enabled is the more trustworthy signal before clicking something like "Save and Continue."
- The page can auto-scroll after typing into a field, which invalidates previously-known click coordinates for the next field. In busy multi-field sections, re-screenshot before every single click rather than chaining blind coordinate clicks.
- School/University is a combobox that falls back to a literal "Other" option when the real institution isn't in Workday's database (per the form's own on-page instructions): type "Other," press Enter to convert it into a selected chip.
- Field of Study is a large, alphabetically sorted, virtualized checkbox list. The visible search box does not actually filter the list, so an exact match sometimes isn't present at all and the closest available option has to be chosen, with the actual checkbox icon clicked rather than the label text.
- Voluntary Disclosures / compliance questions worth expecting: Senior Government Official referral/relation, outside business or second-job disclosure (answer honestly, including things like a personal content brand or newsletter), and whether the candidate worked at the target company's external accounting firm within the last two years (relevant here because of the EY background) plus whether that work touched the target company specifically.
- Salary expectation and notice period fields should be grounded in an actual market-rate check for the role's seniority and location rather than guessed, and flagged to Raj if there's no hard data to base them on.

### General
- LinkedIn job postings often render behind a loading skeleton; a short wait plus a re-fetch of the page text is usually enough, no special handling required beyond that.
- When a target company is also somewhere Tanya used to work directly (e.g. Barclays), that is not the same as a "named client" conflict; the vq CV already names it as employment history and that's a strength to lean into, not something to anonymise.

## What this README does not cover

To be explicit about the limits of this document: it does not include Tanya's personal contact details (those live in the CV files themselves, not here), the verbatim wording used to answer any specific compliance/disclosure question (only the categories and the honesty principle are documented), or a fixed salary figure to reuse (each was derived from a live market check for that specific role and location, not a fixed number). Anyone continuing this work will need to make those same judgment calls fresh each time, not copy a prior answer.

## Application tracker

| Company | Role | CV version | Cover letter | Status |
|---|---|---|---|---|
| Lloyds Banking Group | Senior Manager, Platform & Software Payments BD (Europe) | vq | Freehand (pre-template) | Submitted |
| FIS Global | Go-To-Market Lead, Working Capital Solutions | vq | Freehand (pre-template) | Submitted |
| BCG | Global Sector Senior Manager, Payments & Fintech | vq | Freehand (pre-template) | Submitted |
| Edenred | Strategic & Transformation Manager | vq | Freehand (pre-template) | Submitted |
| JPMorgan Chase | Business Manager, Sr Associate/VP, CIB Operations | vq | Freehand (pre-template) | Submitted |
| S&P Global / With Intelligence | Head of Audience Engagement | vq | Freehand (pre-template) | Submitted |
| Marqeta | Senior Account Executive, EU/UK | vq | Freehand (pre-template) | Submitted |
| Profound | Engagement Manager, Mid-Market | vq | Template (table format) | Submitted |
| OpenAI | Head of GTM Partnerships, EMEA | vq (light edit) | Template (table format) | Submitted |
| Capital One | Senior Relationship Management and Business Development | vq (unmodified) | Not required (Workday flow) | Submitted |
| Barclays | Partnerships, External Engagement & Governance Support Manager | vq | Template | Drafted, not yet submitted |
| HSBC | Investment Manager, HSBC Ventures | vq | Template | Drafted, not yet submitted |
| techUK | Programme Manager, International Trade | vq | Template | Drafted, not yet submitted (salary band £35k-42k is below Tanya's likely target, worth a decision before applying) |

Note: the earlier freehand-format cover letters (Lloyds through Marqeta) predate the standing rule to always use the blank template. Profound and OpenAI onward use the template format and are the pattern to follow going forward.
