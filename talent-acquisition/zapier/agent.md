# IT Recruiter AI Agent Pipeline

## Overview
This workflow is a 4-step pipeline (3 AI agents + 1 LinkedIn lookup step) that helps IT recruiters find and evaluate the best candidates based on a job description. Each step can be triggered individually or as part of the full pipeline.

---

## 🔁 FULL PIPELINE TRIGGER
**Triggered when:** The user submits a Job Description (JD) to start the full pipeline from scratch.

---

## STEP 1 — Agent 1: Job Position Analyzer
**Can also be triggered individually by:** Submitting a JD directly to Agent 1.

1. Accept the user's raw Job Description (JD) as input.
2. Send the JD to AI Agent 1 with the following prompt focus:
- Identify the core role, seniority level, and department.
- Extract must-have vs. nice-to-have technical skills, tools, and technologies.
- Identify soft skills, years of experience, and any industry-specific requirements.
- Summarize the ideal candidate profile in a structured format (role summary, key skills, experience level, location/remote preferences).
3. Output a **Structured Position Summary** containing: role title, required skills list, experience range, and candidate profile description.
4. Pass the Structured Position Summary to Step 2.

---

## STEP 2 — Agent 2: Boolean Search String Generator
**Can also be triggered individually by:** Submitting a Structured Position Summary (or raw JD) directly to Agent 2.

1. Accept the Structured Position Summary from Step 1 (or a manual input) as input.
2. Send it to AI Agent 2 with the following prompt focus:
- Generate optimized Boolean search strings tailored for LinkedIn Recruiter.
- Include variations using AND, OR, NOT operators for job titles, skills, and technologies.
- Provide multiple Boolean string options ranked by specificity (broad → narrow).
- Suggest relevant LinkedIn filters to apply alongside the Boolean strings (e.g., location, industry, years of experience).
3. Output a **Boolean Search Package** containing: 2–5 Boolean search strings + recommended LinkedIn filters.
4. Pass the Boolean Search Package to Step 3.

---

## STEP 3 — LinkedIn Candidate Lookup
**Can also be triggered individually by:** Submitting a Boolean Search Package directly to this step.

1. Accept the Boolean Search Package from Step 2 (or a manual input) as input.
2. Use the Boolean search strings and filters to query LinkedIn Recruiter and fetch matching candidate profiles.
3. Collect candidate data for each result, including: full name, current title, current company, years of experience, location, skills listed, and a link to their LinkedIn profile/CV.
4. Compile all fetched candidates into a **Candidate List**.
5. Pass the Candidate List (along with the original Structured Position Summary) to Step 4.

---

## STEP 4 — Agent 3: Candidate-JD Match Analyzer
**Can also be triggered individually by:** Submitting a Candidate List + JD or Position Summary directly to Agent 3.

1. Accept the Candidate List and the Structured Position Summary from the previous steps (or manual inputs) as input.
2. For each candidate, send their LinkedIn profile/CV data along with the Position Summary to AI Agent 3 with the following prompt focus:
- Score the candidate's match against the JD on a scale of 0–100%.
- Highlight matching skills, experience, and qualifications.
- Flag missing or mismatched requirements.
- Provide a short written justification for the score.
3. Rank all candidates from highest to lowest match score.
4. Output a **Final Ranked Candidate Report** containing: candidate name, match score, strengths, gaps, and LinkedIn profile link.
5. Present the Final Ranked Candidate Report to the recruiter.

---

## ⚙️ CONDITIONAL LOGIC

- **If triggered as full pipeline:** Execute Steps 1 → 2 → 3 → 4 sequentially, passing outputs automatically.
- **If triggered individually at Step 1:** Run only Agent 1 and output the Structured Position Summary.
- **If triggered individually at Step 2:** Accept manual input (JD or Position Summary), run only Agent 2, and output the Boolean Search Package.
- **If triggered individually at Step 3:** Accept manual Boolean strings, run only the LinkedIn lookup, and output the Candidate List.
- **If triggered individually at Step 4:** Accept manual Candidate List + JD, run only Agent 3, and output the Ranked Candidate Report.
- **If LinkedIn Recruiter returns no results:** Notify the recruiter and suggest broadening the Boolean search strings before retrying Step 3.

---

**Expected Outcome:** The recruiter receives a ranked list of the most relevant LinkedIn candidates, each scored and analyzed against the original job description — saving hours of manual sourcing and screening time. Every step can also be run independently for maximum flexibility.