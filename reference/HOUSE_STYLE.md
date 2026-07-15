# Memory

## Me
Raj, working on Tanya Thourani's 2026 job applications (CVs, cover letters, ATS submissions).

## Preferences

### Cover letters — sound human, not AI-generated
When writing any cover letter (or CV prose), strip anything that reads as AI-generated. Specifically:

- **No em dashes (—)** anywhere. Use a period, comma, or "and" instead. This is the single biggest AI tell — avoid it every time, no exceptions.
- No AI stock phrasing: avoid "I'm excited to," "I would be thrilled," "in today's fast-paced world," "leverage synergies," "passionate about," "seamlessly," "robust," "cutting-edge," "unlock potential," "dive deep," "at the intersection of."
- No triplet lists ("X, Y, and Z" used as a crutch in every paragraph) or overly balanced/symmetrical sentence structures — vary rhythm and sentence length like a real person writing.
- No excessive hedging or throat-clearing openers ("I am writing to express my interest in...").
- Keep it direct, specific, and grounded in real facts from the CV — no generic filler that could apply to any candidate.
- Read the draft back and ask: would a recruiter flag this as ChatGPT-written? If yes, rewrite the flagged sentence in plainer, more specific language.

This applies to every cover letter produced going forward for any application in this folder, not just the ones already submitted.

### Base CV source
The master CV lives in the `Latest_2026` folder, not the top-level folder (old versioned copies there — v3f, vff, vfff, vffff and other legacy source docs — have been deleted; `Latest_2026` is now the only source).

Two versions exist in `Latest_2026`, both current, used situationally:
- **`Tanya Thourani_CV_2026_vq.docx`** — names real clients (Visa, Mastercard, Adyen, UK Finance, Deutsche Bank, Vitality). Default choice: stronger for ATS keyword matching and credibility.
- **`Tanya Thourani_CV_2026_nc.docx`** — same experience, client names replaced with generic descriptions (e.g. "Netherland-headquartered listed global payments platform"). Use this instead of vq whenever the target employer is one of those named clients, or a close competitor of one, to avoid naming a conflicted party in the application.

Before starting any new application, check whether the employer conflicts with a named client in vq. If yes, use nc. If no, use vq. If genuinely unsure, ask before proceeding rather than defaulting silently.

### Page size — A4, not US Letter
All CVs and cover letters must be formatted for A4 portrait (11906 x 16838 DXA / 210mm x 297mm), not US Letter. Tanya is UK-based and applying to UK/EU roles, so US Letter is wrong by default. When creating a new docx with docx-js, set `page: { size: { width: 11906, height: 16838 } }` explicitly (docx-js actually defaults to A4, so this only needs attention if a US Letter template or prior file is reused). Applies to every document produced going forward.

### Confirm submission with a screenshot
After submitting any job application (Ashby, Workday, or any other ATS), take a screenshot of the confirmation page and share it in chat. Do this every time going forward, without being asked.

### Cover letters — always use the blank template
Every cover letter must be built from `Tanya_Thourani_Cover_Letter_2026_TEMPLATE.docx` in `Latest_2026`, not written freehand. Do not improvise a different structure.

The template's fixed structure and wording (fill in the bracketed parts, keep everything else exactly as-is):
1. `Dear [Company] Hiring Team,`
2. Fixed opening line, verbatim: "Few positions bring together as directly the work I have delivered, the market perspective I have since developed and the contribution I now want to make."
3. A role-specific hook paragraph (2-4 sentences, grounded in real CV facts).
4. Fixed line: "Some of the most directly relevant experience includes:"
5. The "Your ask / My evidence" table (2 columns, bold centered header row). Add or remove rows as needed, typically 5. Each row maps a JD requirement to a specific, honest piece of evidence from the CV.
6. Fixed line, verbatim: "Across all of this, I care deeply about whether strategy can actually work - beyond the slide, report, blog or memo."
7. "I bring a strong bias for [complete the sentence with a role-relevant trait]."
8. Fixed line: "In the first year, I would seek to contribute in five practical ways:" followed by exactly 5 bulleted, role-specific first-year actions.
9. "This opportunity feels like a natural progression [complete the sentence]."
10. "I would be proud to bring my [specific experience] to [company/programme]."
11. Fixed line, verbatim: "Thank you for considering my application."
12. Sign-off: "Regards, Tanya Thourani" (use the full name, not the "TT" initials from the raw template file).

The template file itself is saved in US Letter; always override to A4 (Mm(210) x Mm(297), or 11906 x 16838 DXA) when generating the output, per the A4 rule above. Trim table/bullet text as needed to keep the letter to one page. Convert to PDF as the final deliverable unless a docx is explicitly requested.

This replaces any earlier freehand cover letter format used in this folder. Applies to every cover letter produced going forward.
