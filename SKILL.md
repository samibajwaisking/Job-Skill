---
name: linkedin-job-hunter
description: >
  Activate this skill whenever a user shares a LinkedIn profile URL or asks to find jobs based on their LinkedIn profile. This skill performs a complete LinkedIn profile analysis: web-searches for the person's public profile data, extracts their skills/experience/education, searches for matching job opportunities across multiple platforms (LinkedIn Jobs, Indeed, Glassdoor, RemoteOK, etc.), scores and ranks the jobs by fit, then gives the user a detailed profile strength rating (0-100) with actionable improvement tips. Trigger whenever you see a LinkedIn URL (linkedin.com/in/...), or phrases like "find me jobs", "check my LinkedIn", "rate my profile", "job search LinkedIn", "LinkedIn profile review", "jobs for my profile", even if they don't use the exact word "skill". Always use this skill — don't try to handle LinkedIn job searches without it.
---

# LinkedIn Job Hunter & Profile Rater

A skill that takes a LinkedIn profile URL, analyzes the person's background through web search, finds the best matching job opportunities, and gives a detailed profile strength rating with improvement recommendations.

---

## Workflow Overview

1. **Extract Profile Data** — Web search the LinkedIn URL to gather public profile info
2. **Build Candidate Summary** — Parse skills, experience, education, location, title
3. **Search for Jobs** — Run multiple targeted job searches across platforms
4. **Score & Rank Jobs** — Match jobs against candidate profile, rank by fit %
5. **Rate the Profile** — Score 0-100 across multiple dimensions
6. **Generate Report** — Present jobs + profile rating + improvement tips

---

## Step 1: Extract Profile Data

When user provides a LinkedIn URL like `https://www.linkedin.com/in/username`:

Run these web searches in sequence:

```
Search 1: site:linkedin.com/in/ "[username]" OR "[full name from URL]"
Search 2: "[person name]" LinkedIn profile skills experience
Search 3: "[person name]" "[current company or title if visible]" professional background
```

Also try fetching the URL directly — LinkedIn may return some public data.

**Extract these fields (fill what you can find, mark others as "Not found"):**
- Full Name
- Current Title / Role
- Current Company
- Location (City, Country)
- Years of Experience (estimate from career history)
- Skills (list all mentioned)
- Education (degree, university, year)
- Previous Companies / Roles
- Languages
- Certifications / Courses
- Portfolio / Website links
- Summary / About section

**If profile is private or data is limited:** Tell the user clearly:
> "Your LinkedIn profile appears to be private or limited in public visibility — this itself reduces your profile strength score. I found [X] data points. Here's what I can work with..."
> Then proceed with available data.

---

## Step 2: Build Candidate Summary

From extracted data, create a structured internal summary:

```
CANDIDATE PROFILE SUMMARY
==========================
Name: [name]
Current Role: [title] at [company]
Location: [city, country]
Experience Level: [Junior / Mid / Senior / Lead / Executive]
Core Skills: [top 5-8 skills]
Industry: [primary industry]
Education: [degree + field]
Certifications: [list]
Remote Eligible: [Yes/No/Unknown based on location + profile signals]
```

Use this summary for all job searches.

---

## Step 3: Search for Jobs

Run **at least 6-8 web searches** targeting different platforms and angles:

### Search Templates

```
1. site:linkedin.com/jobs "[job title]" "[location OR remote]" 2024 OR 2025
2. site:indeed.com "[job title]" "[primary skill]" "[location]"
3. site:glassdoor.com "[job title]" hiring "[industry]"
4. "[job title]" "[top skill]" remote job opening 2025
5. "[job title]" "[secondary skill]" "[city OR country]" apply now
6. site:remoteok.io OR site:weworkremotely.com "[job title]" "[skill]"
7. "[industry]" companies hiring "[role]" "[skill]" 2025
8. "[job title]" freelance OR contract "[primary skill]" opportunities
```

**Adapt searches based on profile:**
- If location is Pakistan/South Asia → also search for remote-friendly + Asian time zone jobs
- If profile shows freelance work → also search Upwork, Fiverr, Toptal demand
- If profile shows education only (student/fresh grad) → add "entry level", "fresh graduate", "trainee"
- If profile shows 5+ years → add "senior", "lead", "manager" variants

---

## Step 4: Score & Rank Jobs

For each job found, calculate a **Match Score (0-100%)** based on:

| Factor | Weight |
|--------|--------|
| Title/Role match | 25% |
| Required skills match | 30% |
| Experience level match | 20% |
| Location / Remote fit | 15% |
| Industry match | 10% |

Present top **8-12 jobs** in a ranked table:

```
RANK | JOB TITLE | COMPANY | LOCATION | MATCH % | APPLY LINK | WHY IT FITS
```

Add a short 1-line reason for each job explaining the fit.

---

## Step 5: Rate the Profile (0-100)

Score the LinkedIn profile across **6 dimensions**:

### Scoring Rubric

#### 1. Profile Completeness (20 pts)
- Photo: 3 pts
- Headline: 3 pts
- About/Summary: 4 pts
- Experience (detailed): 4 pts
- Education: 2 pts
- Contact info: 2 pts
- Skills section: 2 pts

#### 2. Skills Relevance & Depth (20 pts)
- 10+ relevant skills listed: 5 pts
- Skills endorsed by others: 5 pts
- Skills match current market demand: 10 pts

#### 3. Experience Quality (20 pts)
- Quantified achievements (numbers, %, revenue): 8 pts
- Clear role descriptions: 6 pts
- Career progression visible: 6 pts

#### 4. Visibility & SEO (15 pts)
- Custom LinkedIn URL: 3 pts
- Keywords in headline/about: 5 pts
- Profile appears in public search: 7 pts

#### 5. Social Proof & Activity (15 pts)
- Recommendations received: 5 pts
- Posts / Articles published: 4 pts
- Connections 500+: 3 pts
- Engagement visible: 3 pts

#### 6. Education & Credentials (10 pts)
- Degree relevance: 4 pts
- Certifications listed: 4 pts
- Courses/training: 2 pts

**Total: /100**

### Rating Levels
- **85-100**: 🟢 Excellent — Top 10% profiles
- **70-84**: 🔵 Strong — Above average, minor tweaks needed
- **50-69**: 🟡 Average — Needs improvement in key areas
- **30-49**: 🟠 Weak — Significant gaps, recruiters may skip
- **0-29**: 🔴 Very Weak — Major overhaul needed

---

## Step 6: Generate the Full Report

Present output in this structure:

---

### 📊 LINKEDIN PROFILE ANALYSIS REPORT

**Candidate:** [Name]  
**Analyzed:** [Date]  
**Overall Profile Score: [X]/100 — [Rating Level]**

---

### 🎯 TOP JOB MATCHES

[Ranked table of 8-12 jobs]

---

### 📈 PROFILE STRENGTH BREAKDOWN

| Dimension | Score | Max |
|-----------|-------|-----|
| Profile Completeness | X | 20 |
| Skills Relevance | X | 20 |
| Experience Quality | X | 20 |
| Visibility & SEO | X | 15 |
| Social Proof | X | 15 |
| Education & Credentials | X | 10 |
| **TOTAL** | **X** | **100** |

---

### 🔧 HOW TO IMPROVE YOUR PROFILE

List **5-10 specific, actionable improvements** ranked by impact:

Format each as:
```
🔴 HIGH IMPACT: [What to fix] → [Exactly how to fix it] → [Expected score boost: +X pts]
🟡 MEDIUM IMPACT: [What to fix] → [How] → [+X pts]
🟢 QUICK WIN: [Easy fix] → [How] → [+X pts]
```

---

### 💡 PRO TIPS FOR THIS PROFILE

Add 3-5 profile-specific strategic tips based on their industry/role. Examples:
- "For AI educators: post weekly content about AI tools — LinkedIn algorithm favors educators"
- "For developers: pin your GitHub link prominently in Featured section"
- "For freelancers: add 'Open to Work' badge + list services in About section"

---

## Edge Cases

### If LinkedIn URL is broken / 404
> "This LinkedIn URL doesn't seem to be working. Please check if the profile is public and the URL is correct. You can also paste your profile details (name, title, skills, experience) directly and I'll work with that."

### If user gives name instead of URL
> "I can search better with your LinkedIn URL (linkedin.com/in/yourname). But I'll search with your name for now..."
> Then proceed with name-based searches.

### If user only wants jobs (no rating)
> Still do a quick profile scan, mention: "I noticed a few things about your profile worth knowing..." and give brief tips.

### If user only wants profile rating (no jobs)
> Skip job search section, focus entirely on detailed rating + improvement plan.

---

## Quality Standards

- Always find **real, currently open** job listings (not expired)
- Always give **specific actionable advice** — never vague ("improve your headline" → always say *how*)
- Match score must be **justified** — explain why each job fits
- Profile score must be **evidence-based** — explain what you found (or didn't find) for each dimension
- If data is limited, **be transparent** and tell user what you couldn't access

---

## Read Also

- `references/job-platforms.md` — List of job platforms to search by region/type
- `references/profile-keywords.md` — High-value LinkedIn keywords by industry
