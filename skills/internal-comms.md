---
name: internal-comms
description: A set of resources to help me write all kinds of internal communications,
  using the formats that my company likes to use. Claude should use this skill whenever
  asked to write some sort of internal communications (status reports, leadership
  updates, 3P updates, company newsletters, FAQs, incident reports, project updates,
  etc.).
version: 1.0.0
author: Anthropic / disesfgewuAgent
tags:
- writing
- communications
- slack
- email
---

## When to use this skill
To write internal communications, use this skill for:
- 3P updates (Progress, Plans, Problems)
- Company newsletters
- FAQ responses
- Status reports
- Leadership updates
- Project updates
- Incident reports

## How to use this skill

To write any internal communication:

1. **Identify the communication type** from the request
2. **Follow the matching guideline below** for formatting, tone, and content gathering
3. If the communication type doesn't match any of the four below, use the "Other communications" guidance and ask for clarification or more context about the desired format

---

## 3P Updates (Progress, Plans, Problems)

You are being asked to write a 3P update. 3P updates stand for "Progress, Plans, Problems." The main audience is for executives, leadership, other teammates, etc. They're meant to be very succinct and to-the-point: think something you can read in 30-60sec or less. They're also for people with some, but not a lot of context on what the team does.

3Ps can cover a team of any size, ranging all the way up to the entire company. The bigger the team, the less granular the tasks should be. For example, "mobile team" might have "shipped feature" or "fixed bugs," whereas the company might have really meaty 3Ps, like "hired 20 new people" or "closed 10 new deals."

They represent the work of the team across a time period, almost always one week. They include three sections:
1) Progress: what the team has accomplished over the next time period. Focus mainly on things shipped, milestones achieved, tasks created, etc.
2) Plans: what the team plans to do over the next time period. Focus on what things are top-of-mind, really high priority, etc. for the team.
3) Problems: anything that is slowing the team down. This could be things like too few people, bugs or blockers that are preventing the team from moving forward, some deal that fell through, etc.

Before writing them, make sure that you know the team name. If it's not specified, you can ask explicitly what the team name you're writing for is.

**Tools/sources to pull from, if available**: Slack posts from team members with their updates (favor posts in large channels with lots of reactions), Google Drive docs from critical team members with lots of views, emails with lots of responses, non-recurring meetings that have a lot of importance (product reviews, etc.). Focus on things covering: Progress (a week ago to today), Plans (today to next week), Problems (a week ago to today). If you don't have access to these sources, ask the user for the things they want to cover.

**Workflow**: (1) Clarify the team name and time period (usually past week for Progress/Problems, next week for Plans). (2) Gather information from available sources or ask the user directly. (3) Draft the update following the strict formatting below. (4) Review for concision (30-60 seconds to read) and that it's data-driven.

**Formatting** (always the same, very strict — never use anything else). Pick an emoji that is fun and captures the vibe of the team and update:

```
[emoji] [Team Name] (Dates Covered, usually a week)
Progress: [1-3 sentences of content]
Plans: [1-3 sentences of content]
Problems: [1-3 sentences of content]
```

Each section should be no more than 1-3 sentences: clear, to the point, data-driven with metrics where possible. The tone should be very matter-of-fact, not super prose-heavy.

---

## Company Newsletter

You are being asked to write a company-wide newsletter update, summarizing the past week/month of a company for the entire company to read. It should be maybe ~20-25 bullet points long, sent via Slack and email, so make it consumable for that.

Ideally it includes: lots of links (relevant Google Drive docs, prominent Slack messages in announce channels and from executives, company-wide emails, significant company events); short and to-the-point bullets (~1-2 sentences each); the "we" tense throughout ("we did this", "we did that").

**Tools/sources to pull from, if available**: Slack messages in channels with lots of people/reactions/responses, executive emails about company-wide announcements, meetings with large attendee lists (All-Hands, big announcements) and any documents attached to them, new docs that got a lot of attention (company-wide vision docs, quarter/half plans, docs by critical executives), references to external press/articles. If you don't have access, ask the user for what they want to cover.

**Sections**: the company is often pretty big with a variety of teams and initiatives. Break the update into clusters of similar things, e.g. {product development, go to market, finance} or {recruiting, execution, vision} or {external news, internal news}, to keep different areas well represented.

**Prioritize**: company-wide impact (not team-specific detail), announcements from leadership, major milestones/achievements, information affecting most employees, external recognition or press.
**Avoid**: overly granular team updates (save those for 3Ps), information only relevant to small groups, duplicate information already communicated.

**Example format**:
```
:megaphone: Company Announcements
- Announcement 1
- Announcement 2

:dart: Progress on Priorities
- Area 1
    - Sub-area 1
    - Sub-area 2
- Area 2
    - Sub-area 1

:pillar: Leadership Updates
- Post 1
- Post 2

:thread: Social Updates
- Update 1
- Update 2
```

---

## FAQ Answers

You are an assistant for answering questions that are being asked across the company. Every week, there are lots of questions that get asked across the company, and your goal is to summarize what those questions are and give a nice summarized answer to minimize confusion. Interesting areas: recent corporate events (fundraising, new executives, etc.), upcoming launches, hiring progress, changes to vision or focus, etc.

**Tools/sources to pull from, if available**: Slack questions with lots of responses/reactions/thumbs-up (signals shared interest), FAQs written directly in emails, docs in Google Drive or linked on calendar events that answer common questions (directly or by inference).

**Formatting**:
```
- *Question*: [insert question - 1 sentence]
- *Answer*: [insert answer - 1-2 sentences]
```

**Guidance**: be holistic — capture the entire company's questions, not just one user's or team's. Read across all available sources.

**Answer guidelines**: base answers on official company communications when possible; if information is uncertain, indicate that clearly; link to authoritative sources (docs, announcements, emails); keep tone professional but approachable; flag if a question requires executive input or an official response.

---

## Other Communications

For internal company communication that doesn't fit 3P updates, newsletters, or FAQs:

Before proceeding: (1) ask the user about their target audience, (2) understand the communication's purpose, (3) clarify the desired tone (formal, casual, urgent, informational), (4) confirm any specific formatting requirements.

General principles: be clear and concise; use active voice; put the most important information first; include relevant links and references; match the company's communication style.

## Keywords
3P updates, company newsletter, company comms, weekly update, faqs, common questions, updates, internal comms
