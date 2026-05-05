# 🔍 LinkedIn Job Hunter & Profile Rater — Claude Skill

A powerful Claude AI skill that analyzes LinkedIn profiles, finds matching job opportunities, and provides a detailed profile strength rating with actionable improvement tips.

---

## ✨ What This Skill Does

Give Claude your LinkedIn profile URL and it will:

1. **🔎 Analyze Your Profile** — Web-searches your public LinkedIn data to extract skills, experience, education, and career history
2. **💼 Find Matching Jobs** — Searches 10+ job platforms (LinkedIn Jobs, Indeed, Glassdoor, RemoteOK, Rozee.pk, and more) for roles that match your background
3. **📊 Score Each Job** — Ranks jobs by match percentage based on your skills, experience level, location, and industry
4. **⭐ Rate Your Profile** — Gives you a score out of 100 across 6 dimensions
5. **🛠 Improvement Plan** — Tells you exactly what to fix, how to fix it, and how many points each fix adds to your score

---

## 📋 Sample Output

```
📊 LINKEDIN PROFILE ANALYSIS REPORT
Candidate: John Doe
Overall Profile Score: 62/100 — 🟡 Average

🎯 TOP JOB MATCHES
RANK | JOB TITLE           | COMPANY      | LOCATION    | MATCH % | APPLY LINK
1    | Senior AI Engineer   | TechCorp     | Remote      | 94%     | [link]
2    | ML Product Manager   | StartupXYZ   | Dubai, UAE  | 87%     | [link]
...

📈 PROFILE STRENGTH BREAKDOWN
Profile Completeness   → 14/20
Skills Relevance       → 16/20
Experience Quality     → 11/20
Visibility & SEO       → 9/15
Social Proof           → 7/15
Education & Creds      → 5/10
TOTAL                  → 62/100

🔧 TOP IMPROVEMENTS
🔴 HIGH IMPACT: No quantified achievements → Add numbers/% to job descriptions → +8 pts
🟡 MEDIUM IMPACT: Headline too generic → Use keyword formula → +5 pts
🟢 QUICK WIN: Add custom LinkedIn URL → 2 min fix → +3 pts
```

---

## 🚀 Installation

### Method 1: Install .skill File (Recommended)

1. Download `linkedin-job-hunter.skill` from the [Releases](../../releases) page
2. Open Claude.ai → Settings → Skills → Upload Skill
3. Done! Claude will now automatically use this skill when you share a LinkedIn URL

### Method 2: Manual Copy

1. Copy the contents of `SKILL.md`
2. In Claude.ai, go to Settings → Skills → Create New Skill
3. Paste the content and save

---

## 📁 File Structure

```
linkedin-job-hunter/
├── SKILL.md                        # Main skill instructions for Claude
├── references/
│   ├── job-platforms.md            # 40+ job platforms organized by region/type
│   └── profile-keywords.md         # High-value LinkedIn keywords by industry
├── README.md                       # This file
├── LICENSE                         # MIT License
└── .gitignore
```

---

## 🧠 How It Works

This skill follows a 6-step workflow:

| Step | Action |
|------|--------|
| 1 | Web search extracts public LinkedIn profile data |
| 2 | Builds a structured candidate summary |
| 3 | Runs 6-8 targeted job searches across multiple platforms |
| 4 | Scores each job against candidate profile (weighted algorithm) |
| 5 | Rates profile across 6 dimensions using a detailed rubric |
| 6 | Generates complete report with ranked jobs + improvement plan |

---

## 💡 Trigger Phrases

The skill activates when you:

- Share a LinkedIn URL (`linkedin.com/in/...`)
- Say "find me jobs based on my LinkedIn"
- Say "rate my LinkedIn profile"
- Say "check my LinkedIn and find jobs"
- Ask "how strong is my LinkedIn profile?"

---

## 🌍 Supported Regions

Job searches are tailored for:
- 🇵🇰 Pakistan (Rozee.pk, Mustakbil, remote roles)
- 🇺🇸 USA (Indeed, ZipRecruiter, Hired.com)
- 🇬🇧 UK (PeoplePerHour, Reed.co.uk)
- 🌐 Gulf / Middle East (Bayt.com, GulfTalent)
- 🌐 Remote Worldwide (RemoteOK, WeWorkRemotely, Himalayas)

---

## ⚡ Limitations

- LinkedIn profiles must be **public** for full analysis
- Private profiles will receive lower visibility scores (which is accurate feedback)
- Job listings are from web search results — always verify the listing is still open before applying
- Match scores are estimates based on available profile data

---

## 🤝 Contributing

Contributions welcome! You can:
- Add more job platforms to `references/job-platforms.md`
- Add keywords for more industries to `references/profile-keywords.md`
- Improve the scoring rubric in `SKILL.md`
- Translate the skill to other languages

Please open an issue or pull request.

---

## 📜 License

MIT License — see [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Sami Bajwa**  
AI Educator | Web Developer | Digital Entrepreneur  
📍 Sargodha, Pakistan

🌐 [samioutic.com](https://samioutic.com)  
📘 [Facebook](https://www.facebook.com/samibajwaisking)  
💬 [WhatsApp Channel](https://whatsapp.com/channel/0029VbCNzQeISTkQR04DvX3r)

---

*Built with ❤️ for the Claude AI Skills ecosystem*
