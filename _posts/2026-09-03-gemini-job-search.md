---
title: "The Search for Jobs: Gemini Edition"
categories:
  - Blog
tags:
  - AI
  - Gemini
  - Job Search
header:
  overlay_image: /assets/images/AI_Career_Path.jpg
  teaser: /assets/images/AI_Career_Path.jpg
published: true
---

Gemini Spark is surprisingly helpful...Kinda

<!--more-->

The ***hardest*** part of looking for a job, to me, is...well, the *looking* part.
It doesn't take particularly long for me to get discouraged while scrolling through job listings, so I decided to at least try to cut that particular part out of the daily grind.

## Enter Gemini Spark, Stage Right

Spark is Gemini's "Background Agent"—you can tell it to do something at a specific time or on a specific day, then just wait for it to tell you it's completed the task—no manual intervention necessary.
When given permission, it can read & write to files in your Google Drive, read or send emails, and even scan job-posting websites.

### Job Search Bot Description

```text
Task Goal: Monitor major Capital District employers for relevant job openings.

Data Sources: Scan the career pages for St. Peter's Health Partners, Albany Med Health System, Ellis Medicine, GlobalFoundries, Regeneron, General Electric, Bechtel Marine Propulsion, Golub Corporation, Stewart's Shops, and New York State.

Filtering Criteria: Apply my joshua-profile skill. Only select roles that strongly match the job titles, technical competencies, and framework preferences defined in that skill.

Output & Action: Compile the matching roles into a Google Sheet named "Capital District Job Tracker." Include columns for Job Title, Company, Location, Date Posted, and the Application Link.

Schedule: Run this search every day at 8:00 AM.

Notification: Draft an email to my inbox summarizing the strongest matches for the day.
```

### `joshua-profile` Skill Description

```text
---
name: joshua-profile
description: Personalized context and operational preferences for Joshua Pelton-Stroud.
---

# User Profile & Operational Preferences

- **Role & Technical Depth:** Treat the user as an experienced Full Stack Developer and Senior Data Analyst. Provide direct, clean code snippets and architectural insights for Python, SQL, Angular, and TypeScript.
- **Job Search Support:** When drafting cover letters, resumes, or application materials, target Business Intelligence, Data Engineering, Technical Support, and Full Stack Software Development/Engineering positions.
- **Communication Style:** Maintain a neutral, precise, and concise output without unnecessary fluff. Focus on actionable summaries and execution plans.
- **Family & Task Context:** Keep track of family calendar commitments (e.g., Kade's schedules) and pending benefit/household reminders when organizing schedules.
```

## The Results

Results on the above are *pretty* good, actually.
Every morning I get an email with a handful of job postings for which I can apply.
Sometimes Spark does get a little too confident in my skills and send me a "Lead Data Scientist" or "Principle Systems Architect" role, but for the most part I do actually get postings for jobs I could reasonably land, so I can spend more time researching the role and tailoring my resume, and less time scrolling endlessly through positions I have no excuse even looking at.

Overall, I'd say 'Solid B+'.