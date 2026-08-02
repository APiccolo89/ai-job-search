# Job Evaluation Framework

<!-- SETUP: Skill match areas and career goals are personalized by running /setup -->

## Scoring Dimensions

Evaluate each job posting against these five dimensions:

### 1. Technical Skills Match (0-100)
How well do the required/preferred skills align with the candidate's capabilities?

| Score | Meaning |
|-------|---------|
| 80-100 | Core requirements are primary skills |
| 60-79 | Most requirements match, 1-2 gaps that are learnable |
| 40-59 | Partial match, significant upskilling needed |
| 0-39 | Fundamental mismatch |

**Strong match areas:** Python, numerical modelling, large-scale data analysis, FEniCSx/FEM, HPC (SLURM/PBS), earth sciences, computational geodynamics, data pipelines, regression testing, Git/CI
**Moderate match areas:** MATLAB, Julia, C, scientific visualisation, LaTeX/Sphinx documentation, cross-institutional collaboration
**Weak match areas:** ML/AI frameworks (no experience), cloud platforms (AWS/GCP/Azure), commercial software development, SQL (learning), web development, product management

**Calibration note (2026-07-30):** Don't over-credit broad methodological adjacency (e.g. "numerical methods," "HPC," "scientific programming") when the essential criteria name a specific specialist subfield Andrea hasn't worked in (e.g. CFD techniques like compressible flows/turbulence/multiphase flow, a different engineering discipline, a different natural-science domain). A Cambridge CFD/contrail-modelling role scored "high" at the scrape stage on methodological overlap alone, but Andrea judged it a poor fit on full review — it would mean learning an entire new specialist domain under real job pressure, not just picking up new tooling. **How to apply:** when essential criteria list a named specialist subfield outside Andrea's actual domain (computational geodynamics/earth sciences), score Technical Skills more conservatively (cap around 40-50 even with strong general numerical/HPC overlap) and flag the domain gap prominently rather than let broad-category overlap carry the score.

### 2. Experience Match (0-100)
Does work history align with what they're looking for?

| Score | Meaning |
|-------|---------|
| 80-100 | Direct experience in the same domain and role type |
| 60-79 | Related experience, transferable skills clear |
| 40-59 | Adjacent experience, would need to make the case |
| 0-39 | Unrelated experience |

**Strong:** Computational geodynamics, numerical simulation, scientific data analysis, earth sciences, HPC workflows, Python development for science
**Moderate:** Environmental modelling, scientific software development, data engineering, cross-institutional research
**Entry-level:** Commercial data science, industry consulting, environmental consulting (transitioning from academia)

### 3. Behavioral/Culture Fit (0-100)
Does the role and company culture match the behavioral profile?

| Score | Meaning |
|-------|---------|
| 80-100 | Culture strongly matches behavioral preferences |
| 60-79 | Mixed signals but mostly compatible |
| 40-59 | Some friction areas |
| 0-39 | Significant culture mismatch |

**Red flags to research:** Department disorganization, work dominated by maintenance over development, poor chemistry with leadership, culture mismatches. Check reviews, media coverage, LinkedIn connections, and network contacts for insider perspective.

### 4. Location & Logistics (Pass/Fail + Notes)
- Anywhere in the UK: PASS (radius restriction lifted 2026-07-28 — priority is landing a first industry role)
- Remote with occasional office: PASS
- Scotland, Netherlands (any city), Ireland (any city), Norway (any city), Switzerland (any city), or Berlin (Germany only): PASS (secondary relocation options)
- Requires relocation elsewhere: FAIL (deal-breaker)
- Frequent international travel: FLAG (discuss with user)
- **Requires UK nationality / security clearance (SC, DV) / defence sector with clearance mentioned: FLAG explicitly.** Andrea's UK right-to-work (Global Talent Visa) does not satisfy UK nationality or security clearance requirements — same principle as the UK Civil Service exclusion (see CLAUDE.md). Don't silently screen out, but flag clearly so Andrea can confirm case-by-case.

### 5. Career Alignment & Motivation (0-100)
Does this role advance career goals and contain tasks that energize?

| Score | Meaning |
|-------|---------|
| 80-100 | Strongly aligned with career direction, clear growth path |
| 60-79 | Good role but only partially aligned with long-term goals |
| 40-59 | Decent job but doesn't build toward career goals |
| 0-39 | Dead end or backwards step |

**Career goals:**
- Land a first industry role from academia — as of July 2026, sector and location are secondary to breaking in
- Join a structured technical team with clear deliverables and genuine professional development opportunities
- Open to anywhere in the UK; secondary international options: Scotland, Netherlands, Ireland, Norway, Switzerland, Berlin only. Salary target £39,000–£45,000 is a soft reference point, not a hard floor — do not screen out a reasonable permanent role for low salary alone
- Longer-term: grow into a recognised in-house expert and mentor/support role within a company. A visible technical career ladder or mentoring culture is a positive signal, not a requirement, for a first role

**Motivation filter (revised 2026-07-30):** Task type (whether the day-to-day is modelling/Python/analysis specifically, versus data administration, coordination, QC, or other technical-adjacent work) is **no longer a scoring factor** for Career Alignment — as of July 2026, landing a first industry role matters more than the tasks matching a specific "energizing" profile. Do not mark a role down just because it isn't modelling/analysis work.

Still relevant to flag (not as a score penalty, but as context for the user to weigh):
- Genuinely draining conditions remain worth noting: highly ambiguous or chaotic environments (this is a deal-breaker, see below), frequent context-switching with no clear priorities
- Non-task factors: leadership style, department culture, company values, degree of autonomy
- Seniority mismatch: a role titled "Junior"/"Entry-level"/"Early Careers" for a candidate with a PhD + a decade of experience is a distinct concern from task type — it can mean a real step backward in pay and career trajectory, and is still worth flagging explicitly

**Life situation alignment:** Consider personal constraints:
- **Security**: Currently employed until Feb 2027 — not desperate, can be selective
- **Flexibility**: Needs hybrid or flexible working; open to relocation anywhere in the UK
- **Professional development**: Growth, learning, and technical challenge are must-haves — not just a job title change

### 6. Salary Benchmark (Optional)

If the salary lookup tool is configured (`salary_data.json` exists), look up the company:
```
python salary_lookup.py "<Company Name>" --json
```

If a city is known from the posting, add `--city "<City>"` to narrow results.

Present findings as:
```
### Salary Benchmark
| Metric | Value |
|--------|-------|
| [Category] index | XX.X (+/-X.X% vs baseline) |
| Overall index | XX.X (+/-X.X% vs baseline) |
```

Interpret results relative to the baseline defined in the data file's metadata. For index-based data, higher typically means above-market compensation.

If the salary tool is not configured, skip this section.

## Output Format

Present the evaluation as:

```
## Job Fit Evaluation: [Role] at [Company]

| Dimension | Score | Notes |
|-----------|-------|-------|
| Technical Skills | XX/100 | [brief note] |
| Experience Match | XX/100 | [brief note] |
| Behavioral Fit | XX/100 | [brief note] |
| Location | PASS/FAIL | [brief note] |
| Career Alignment | XX/100 | [brief note] |

**Overall Score: XX/100** (weighted average of scored dimensions)

### Verdict: [Strong Fit / Good Fit / Moderate Fit / Weak Fit / Poor Fit]

### Key Strengths for This Role
- [bullet points]

### Gaps to Address
- [bullet points]

### Recommendation
[1-2 sentences: apply/skip/apply with caveats]

### Company Research Checklist
- [ ] Checked company website (mission, values, recent news)
- [ ] Checked review sites (Glassdoor, Jobindex, etc.)
- [ ] Checked LinkedIn for team size, recent hires, connections
- [ ] Checked media for restructuring, growth, or workplace issues
- [ ] Identified network contacts who may know the team/manager
```

## Weighting
- Technical Skills: 30%
- Experience Match: 25%
- Behavioral Fit: 15%
- Career Alignment: 30%

(Location is pass/fail, not weighted)

## Thresholds
- **Strong Fit** (75+): Definitely apply, tailor everything
- **Good Fit** (60-74): Apply, address gaps in cover letter
- **Moderate Fit** (45-59): Consider carefully, discuss with user
- **Weak Fit** (30-44): Probably skip unless strategic reasons
- **Poor Fit** (<30): Skip

## Pre-Application: Call the Employer (Best Practice)

Before writing the application, consider whether the candidate should call the contact person listed in the posting. **Only call if there are substantive questions** - never call just to "be remembered."

### When to Suggest Calling
- The posting has unclear or ambiguous requirements
- It's unclear which competencies are essential vs. nice-to-have
- The role description is vague about day-to-day tasks
- There's a named contact person who invites questions

### Good Questions to Ask
- "What are the primary challenges in this role?"
- "How is time typically divided across the listed responsibilities?"
- "Which competencies are most critical for success in this position?"
- "What does success look like in the first 6-12 months?"

### Rules for the Call
- Prepare a 30-second "elevator pitch" about your background in case they ask
- The call's purpose is **gathering information**, not delivering a pitch
- Take notes - use what you learn to tailor the application
- Reference the conversation naturally in the cover letter ("After speaking with [name], I was especially drawn to...")
