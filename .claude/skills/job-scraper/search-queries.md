# Search Queries for Job Scraper

## Search Sites

**SCRAPE SCOPE as of 2026-10-21: only the UK (incl. Scotland), the Netherlands, Germany and Switzerland.** Andrea narrowed it after the search had spread across 11 countries with little to show for it. Run only those four region sets every scrape. Ireland, Norway, Italy, Canada, Australia and New Zealand are NOT scraped (their sections below are kept for reference, marked INACTIVE); they remain acceptable locations if Andrea brings a posting himself. The UK is a full target again, not a fallback (a UK job suits his relationship). Netherlands sources:
- **linkedin.com/jobs** (location: Netherlands)
- **werkzoeken.nl / nationalevacaturebank.nl / indeed.nl** - Dutch generalist boards (many tech postings in English)
- **academictransfer.com** - Dutch research/university jobs (RSE roles at TU Delft, Utrecht, etc.)
- Direct career pages: **Deltares** (https://www.deltares.nl/en/careers), **TNO** (https://www.tno.nl/en/careers/), **KNMI** (https://www.knmi.nl/over-het-knmi/werken-bij-het-knmi), **Netherlands eScience Center** (https://www.esciencecenter.nl/vacancies/), **Fugro** (https://careers.fugro.com), **Shell** (https://www.shell.com/careers)

UK job market:
- **linkedin.com/jobs** - LinkedIn job listings (filter: Leeds / Yorkshire / UK)
- **indeed.co.uk** - largest UK generalist job board
- **totaljobs.com** - large UK generalist job board, strong industry/commercial coverage
- **jobs.ac.uk** - academic and research roles in UK universities and institutes. **Stale-ID issue (confirmed 2026-08-04):** individual `jobs.ac.uk/job/<ID>/...` URLs from WebSearch results go dead within days - WebFetch on an expired ID silently redirects to the generic search results page instead of erroring, so always check the fetched content isn't a "no longer being advertised" listing page before trusting it as the target job. LinkedIn and totaljobs individual postings have the same issue (redirect/404 on expired listings). Workaround: when a specific ID is stale, re-search or go to the employer's own vacancies page (e.g. `jobs.ac.uk/search/employer/<name>` or the institute's own `/vacancies` page) to get a currently-live URL for the same role.

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target organisations

Direct company career pages to check periodically (not reliably indexed by search engines):
- **Stantec** (environmental consultancy, target company): https://careers-uk-ireland.stantec.com/vacancies/vacancy-search-results.aspx — note: "Data Scientist"-titled roles here have leaned toward data coordination/QA (EQuIS, AGS, lab data management) rather than modelling/analysis; verify actual responsibilities against the job description, not just the title, before surfacing as high fit
- **BGS**: https://www.bgs.ac.uk/about-bgs/working-with-us/job-vacancies/ — confirmed zero vacancies as of 2026-07-26, re-check periodically
- **ECM Selection** (specialist recruiter for PhD-scientist/mathematical-software roles): https://www.ecmselection.co.uk/matlab-jobs — genuinely strong niche fit source (civilian engineering-simulation-software postings have matched Andrea's exact profile), but their Cambridge cluster skews heavily defence/RF/radar, and those roles frequently require **UK national status for security clearance eligibility** — a hard disqualifier for Andrea (Italian citizen) regardless of his UK right-to-work via Global Talent Visa. Filter for civilian/non-defence clients before evaluating.
- **University of Leeds** (local, current employer): https://jobs.leeds.ac.uk/Vacancies.aspx — check the "Research" (cat=205) and "Professional & Managerial" (cat=204) categories directly (site: search doesn't surface individual postings well here either). As of 2026-08-01 nothing matched Andrea's Python/RSE profile (roles found were domain-specific postdocs, Power Platform/enterprise-IT leadership, and admin/BI roles) - re-check periodically since it's Andrea's own institution and zero-relocation.

## Title-vs-Substance Warning (critical, read before every scrape)

**As of 2026-07-30: title keywords are unreliable signals on their own.** A run of postings this session had titles that sounded like strong matches but were substantively unrelated:
- "Data Scientist" (Stantec) → actually lab-data coordination/QA (EQuIS, AGS, no Python/modelling)
- "Data Manager" (Sword Group) → actually petroleum well-log/subsurface data administration
- "Software & Systems Engineer" (WorkNest Secure) → actually PHP/web dev + customer support, entry-level
- "Research Associate" modelling contrail formation (Cambridge) → actually an aerodynamics/CFD engineering role

**Always verify the actual responsibilities and essential criteria against the title before scoring a posting high.** Conversely, the roles that have scored genuinely well (Bristol Data Research Software Engineer, 65/100) had unglamorous titles but substance that matched directly: ETL pipelines, reproducible data engineering, HPC.

**Also flag seniority mismatches explicitly**: postings titled "Junior," "Entry-level," or "Early Careers" are a real concern for Andrea (PhD + 10 years experience) even when skills partially match — likely underpaid and a narrower ceiling than his experience warrants. Surface but flag clearly, don't score as a strong fit just because the skills line up.

## Query Categories

Queries are grouped by priority, reordered 2026-07-30 based on accumulated evidence of what actually scores well (see [[project-job-search]] memory / `upskill/report-2026-07-30.md` for the reasoning). Combine with location terms (Leeds, Yorkshire, West Yorkshire, UK) where the site supports it.

### Priority 1: Research Software Engineer / Scientific Software Engineer / Data Research Engineer

**This is Andrea's strongest and most consistent match category.** Every genuinely high-scoring posting found so far (Bristol Data Research Software Engineer - 65/100 Good Fit; CRUK Scotland RSE - high fit; University of Leeds Scientific Software Engineer in Earth System Modelling - noted "PERFECT FIT") sits in this category. Prioritize these searches above all others.

```
site:jobs.ac.uk "research software engineer" Python
site:jobs.ac.uk "data research software engineer" OR "research data engineer"
site:linkedin.com/jobs "research software engineer" OR "scientific software engineer" UK
site:linkedin.com/jobs "data engineer" "scientific" OR "research" Python UK
site:indeed.co.uk "research software engineer" Python UK
site:totaljobs.com "research software engineer" Python
```

### Priority 2: Sector-Agnostic Data/Pipeline Engineering (industry, not academia)

Same core skill set as Priority 1 (ETL, reproducible pipelines, large-scale data, HPC) but searching industry roles rather than university-employed ones — this is the actual "into industry" version of Andrea's strongest match.

```
site:linkedin.com/jobs "data engineer" Python "data pipeline" UK
site:linkedin.com/jobs "data engineer" ETL Python UK
site:indeed.co.uk "data engineer" Python "large-scale" OR "large scale" UK
site:totaljobs.com "data engineer" Python UK
site:linkedin.com/jobs "platform engineer" OR "data platform" Python scientific UK
```

### Priority 3: Computational Geoscience / Earth Sciences in Industry

Niche but rare-strong matches when they appear (e.g. Net-Zero Geosystems Computational Geoscientist roles — noted as an extremely close skills match for the energy transition / CO2 storage space). Worth searching regularly even though hit rate is low, and worth direct speculative outreach to companies in this space when a live posting can't be found.

```
site:linkedin.com/jobs "computational geoscientist" UK
site:linkedin.com/jobs "geoscientist" Python "energy transition" OR "CO2 storage" UK
site:linkedin.com/jobs "subsurface" Python "data integration" UK OR Norway
site:jobs.ac.uk "computational geoscience" OR "computational geodynamics"
```

### Priority 4: Environmental Modeller

Demoted from its original top spot — results here are mixed, since many "environmental modeller" postings require domain-specific GIS/hydraulic modelling software (InfoWorks ICM, HEC-RAS, TUFLOW) rather than Python, and have consistently scored low. Only worth running periodically, not as a primary hunting ground.

```
site:linkedin.com/jobs "environmental modeller" Python Leeds OR Yorkshire OR UK
site:jobs.ac.uk "environmental modelling" Python
```

### Priority 5: Generic "Data Scientist" (demoted — verify carefully before trusting the title)

**Caution:** generic "Data Scientist" postings frequently assume ML/AI frameworks, cloud ML platforms (AWS Sagemaker, Azure), or advanced statistical modelling — all weak-match or no-experience areas for Andrea (see `04-job-evaluation.md`). Several postings in this category scored well only because of adjacent factors (location, salary), not core skill match (e.g. Jet2 Senior Data Scientist required AWS Sagemaker; National Highways Principal Data Scientist required leadership seniority). Run these for breadth, but score conservatively and don't let title alone drive a high score.

```
site:linkedin.com/jobs "data scientist" Python UK
site:jobs.ac.uk "data scientist" Python
site:indeed.co.uk "data scientist" Python UK
```

## Location Filter

As of 2026-07-28, there is no commute/relocation radius restriction — any location in the UK is acceptable (see CLAUDE.md Identity note). Do not exclude or downrank a UK posting for being far from Leeds; commute distance is informational context to flag alongside an evaluation, not a filter.

- **UK-wide:** All UK locations PASS, including London. Note commute/relocation distance from Leeds for context (e.g. "Leeds-based, no relocation needed" vs. "London — would require relocation") but do not use it to exclude results.
- **Secondary relocation - Scotland:** Any city (Edinburgh, Glasgow, Aberdeen, etc.) — UK, no visa/relocation barrier
- **PRIMARY - Netherlands:** Any city (primary market from 2026-10-19; UK is now fallback)
- **Secondary relocation - Ireland:** Any city
- **Secondary relocation - Norway:** Any city
- **Secondary relocation - Germany:** any city (widened from Berlin-only 2026-10-16). Prefer English-speaking employers — Andrea's German is B1
- **Secondary relocation - Switzerland:** Any city (added 2026-07-30)
- **Secondary relocation - Canada:** Any city (added 2026-10-21) — work permit needed, flag sponsorship on every posting
- **Secondary relocation - Australia / New Zealand:** Any city (added 2026-10-21) — employer sponsorship needed, flag on every posting
- **Secondary relocation - Italy:** Any city (added 2026-10-15)
- **Excluded:** Relocation outside the UK, Scotland, Netherlands, Ireland, Norway, Switzerland, Italy, Germany, Canada, Australia, or New Zealand remains a deal-breaker (see CLAUDE.md)

Remote and hybrid roles anywhere in the UK are acceptable.

### Region: Scotland (part of the UK scrape)

```
site:jobs.ac.uk "research software engineer" Python Scotland
site:linkedin.com/jobs "research software engineer" OR "data engineer" Edinburgh OR Glasgow OR Aberdeen
site:indeed.co.uk "data scientist" OR "research software engineer" Edinburgh OR Glasgow OR Aberdeen
```

### Region: Netherlands (active)

```
site:linkedin.com/jobs "research software engineer" OR "scientific software engineer" Python Netherlands
site:linkedin.com/jobs "computational scientist" OR "data engineer" Netherlands
site:linkedin.com/jobs "modelling" OR "numerical" OR "simulation" Python Delft OR Utrecht OR Amsterdam OR Rotterdam OR Eindhoven
site:academictransfer.com "research software engineer" OR "scientific programmer" OR "scientific software"
"data scientist" OR "environmental modeller" vacature Netherlands Python
hydrodynamic OR groundwater OR subsurface OR geothermal Python modelling Netherlands vacancy English
```

### Secondary regions: Ireland — INACTIVE, not scraped since 2026-10-21

```
site:linkedin.com/jobs "research software engineer" OR "data engineer" Python Ireland
site:jobs.ac.uk "research software engineer" Ireland
```

### Secondary regions: Norway — INACTIVE, not scraped since 2026-10-21

Job bank: **jobbnorge.no** (Norway's main public/academic job portal, added 2026-07-30)

**Note (2026-08-01):** `site:jobbnorge.no` returned zero indexed results - the site doesn't appear to be well-indexed by search engines (same issue as Stantec/BGS career pages). Use jobbnorge.no's own search UI directly (`https://www.jobbnorge.no/search/en?q=...`) instead of `site:` queries.

```
site:linkedin.com/jobs "geoscientist" OR "subsurface" Python Norway
site:linkedin.com/jobs "research software engineer" OR "data engineer" Norway
site:jobbnorge.no "research software engineer" OR "data engineer" OR geoscientist
```

### Region: Switzerland (active)

Job banks: **jobs.ch** (leading commercial portal), **job-room.ch** (official Swiss public employment service)

**Note (2026-08-01):** `site:jobs.ch` queries only surface generic corporate Data Engineer listings, no research/scientific angle found yet. Try jobs.ch's own search/filter UI directly (e.g. `https://www.jobs.ch/en/vacancies/?term=research+software+engineer`) for better results, same fix as the jobs.ac.uk stale-ID issue below.

```
site:jobs.ch "research software engineer" OR "data engineer" Python
site:jobs.ch "computational geoscientist" OR "geoscientist" energy
site:job-room.ch "software engineer" OR "data engineer" Python
site:linkedin.com/jobs "research software engineer" OR "data engineer" Python Switzerland
```

### Secondary regions: Italy (added 2026-10-15) — INACTIVE, not scraped since 2026-10-21

**Market note (first scrape 2026-10-15):** "Research software engineer" is rare as a job title in Italy - zero live matches found. Relevant roles cluster in a few research centres, and many public-research posts (INGV, CNR, OGS) are filled via *concorsi pubblici* on InPA rather than job boards. Salaries mostly €35–55k, often fixed-term (e.g. CMCC co.co.co.). CMCC senior/mid-level researcher roles tend to require fundraising/proposal writing - check against the grant-writing deal-breaker.

Direct career pages to check each Italy scrape (poorly indexed by search engines):
- **CINECA** (Bologna, HPC): https://www.cineca.it ("Lavora con noi")
- **CMCC** (climate modelling): https://www.cmcc.it/work-with-us
- **INGV** (geophysics): https://www.ingv.it (Bandi e concorsi)
- **OGS** (Trieste, oceanography/geophysics, HPC): https://www.ogs.it ("Lavora con noi")
- **ECMWF Bologna**: https://jobs.ecmwf.int (filter duty station Bologna)
- **Human Technopole** (Milan, RSE roles but biomedical): https://careers.humantechnopole.it
- **InPA** (public competitions portal): https://www.inpa.gov.it

```
site:linkedin.com/jobs "research software engineer" OR "scientific software" OR "computational scientist" Python Italy
"sviluppatore software scientifico" OR "calcolo scientifico" OR "modellazione numerica" Python offerta lavoro
"tecnologo" OR "assegno di ricerca" software HPC Python INGV OR CNR OR OGS
site:academicpositions.com Italy "research software engineer" OR "scientific programmer"
```

### Secondary regions: Canada (added 2026-10-21) — INACTIVE, not scraped since 2026-10-21

**Work permit:** Andrea has no Canadian work rights (not covered by EU/UK status). He needs an employer-supported permit (LMIA, or the faster Global Talent Stream for tech roles) or Express Entry permanent residence. Check every posting for "must be legally eligible to work in Canada" (common, effectively excludes him unless the employer will sponsor) and flag it; favour postings that mention sponsorship/relocation support. Many federal government roles (NRCan, Environment and Climate Change Canada) give preference to Canadian citizens/PRs.

Sources: **linkedin.com/jobs** (location: Canada), **ca.indeed.com**, **jobbank.gc.ca** (Job Bank, shows LMIA-approved postings), university career pages (UBC, Toronto, McGill, Waterloo, Alberta, Calgary), **Digital Research Alliance of Canada** (RSE/HPC roles), **Mitacs** (industry-academic placements).

```
site:linkedin.com/jobs "research software engineer" OR "scientific software engineer" Python Canada
site:ca.indeed.com "research software engineer" OR "scientific computing" OR "simulation" Python
site:jobbank.gc.ca "software engineer" OR "data engineer" Python scientific
"research software engineer" OR "scientific programmer" Python Vancouver OR Toronto OR Montreal OR Calgary OR Ottawa visa sponsorship
```

### Secondary regions: Australia / New Zealand (added 2026-10-21) — INACTIVE, not scraped since 2026-10-21

**Work permit:** no work rights in either. Australia: employer-sponsored Skills in Demand (subclass 482) visa, or the National Innovation visa (talent-based). New Zealand: Accredited Employer Work Visa (employer must be accredited). Flag "must have Australian/NZ work rights" and "citizens or permanent residents only" lines (common in government and security-related roles, e.g. CSIRO, Geoscience Australia, Bureau of Meteorology often require citizenship) on every posting.

Sources: **seek.com.au** / **seek.co.nz** (main boards), **linkedin.com/jobs**, **apsjobs.gov.au** (Australian public service), university pages, **CSIRO** (https://jobs.csiro.au), **NCI Australia** and **Pawsey Supercomputing Centre** (HPC/RSE roles), **NIWA / Earth Sciences New Zealand** and **NeSI** (NZ HPC/RSE).

```
"research software engineer" OR "scientific software" Python Australia job
"research software engineer" OR "scientific software" Python "New Zealand" job
site:seek.com.au "research software engineer" OR "scientific programmer" OR "simulation" Python
Pawsey OR NCI OR NeSI OR CSIRO "research software engineer" OR "HPC" vacancy
```

### Region: Germany (active, any city)

```
site:linkedin.com/jobs "research software engineer" OR "scientific software engineer" Python Germany English
"data scientist" OR "wissenschaftlicher Mitarbeiter" Python Berlin Stellenangebot
"simulation engineer" OR "numerical" Python Munich OR Karlsruhe OR Hamburg OR Bremen English-speaking
geothermal OR Geothermie Python modelling Germany job (Eavor, Vulcan Energy, Fraunhofer IEG, GFZ, DLR)
```

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape environmental" → Priority 4 queries + custom focus-specific queries
- "/scrape BGS" → `site:bgs.ac.uk careers` + LinkedIn search for BGS roles
- "/scrape RSE" or "/scrape research software" → Priority 1 queries, run in full across all location tiers
