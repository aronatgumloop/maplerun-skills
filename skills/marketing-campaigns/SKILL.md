---
name: marketing-campaigns
description: Helps plan, execute, analyze, and report on Maplerun's marketing campaigns across all channels. Use when creating campaign briefs, drafting copy, building content calendars, analyzing performance metrics, or segmenting audiences.
icon: megaphone
color: Orange
---

# Marketing Campaigns

## When to Use

Activate this skill when the task involves:

- Creating or filling out a campaign brief
- Drafting ad copy, email sequences, or social posts
- Building a content calendar or campaign timeline
- Analyzing campaign KPIs or performance data
- Segmenting audiences for targeting
- Preparing campaign reports or retrospectives

## Campaign Types

| Type | Primary Channels | Primary Goal |
|------|-----------------|-------------|
| Brand Awareness | Instagram, TikTok, YouTube | Reach & Impressions |
| Lead Generation | Email, LinkedIn, Paid Search | MQLs / Sign-ups |
| Product Launch | All channels | Conversions & Revenue |
| Retention | Email, SMS | Churn Reduction |
| Event Promotion | Social, Email | RSVPs / Attendance |

## Campaign Brief

Every campaign must have a brief before execution. Use the template in `references/campaign-brief-template.md`. Required fields:

1. **Campaign Name** — clear, descriptive (e.g. `Q3 2026 SMB Lead Gen — Email`)
2. **Objective** — one primary KPI
3. **Target Audience** — segment, region, persona
4. **Key Message** — single core value proposition
5. **Channels** — list all with formats (e.g. Email 3-part sequence, Instagram Reels ×4)
6. **Timeline** — start date, end date, key milestones
7. **Budget** — total + per-channel breakdown
8. **Success Metrics** — minimum 2 measurable KPIs with targets

## Audience Segments

| Segment | Profile | Messaging Approach |
|---------|---------|-------------------|
| **Enterprise** | 500+ employees, B2B, long sales cycle | ROI-focused, case studies, executive tone |
| **SMB** | 10–499 employees, value-driven | Speed-to-value, pricing clarity, social proof |
| **Consumer** | Individual users, mobile-first | Emotion-led, benefit-first, visual storytelling |

## KPI Reference

- **Awareness**: Impressions, Reach, CPM, Share of Voice
- **Engagement**: CTR, Likes, Shares, Comments, Time-on-page
- **Conversion**: CVR, CPA, ROAS, MQLs, SQLs, Sign-ups
- **Retention**: Email open rate, Click rate, Churn rate, NPS

## Content Rules

- Headlines: ≤ 60 characters
- Email subject lines: ≤ 50 characters, no spam-trigger words (FREE, URGENT, !!!)
- One CTA per creative — never two competing actions
- Always prepare at least 2 headline variants for A/B testing before launch
- Image specs per channel are in `references/channel-specs.md`

## Reporting Cadence

| Frequency | Format | Audience |
|-----------|--------|----------|
| Weekly | Snapshot (channel metrics) | Slack #marketing |
| Monthly | Full report with insights | Marketing team |
| Post-campaign | Retrospective (wins, misses, next steps) | All stakeholders |

Use the retrospective template in `references/retro-template.md`.

## Tools & Integrations

| Tool | Server | Use |
|------|--------|-----|
| HubSpot | `hubspot` | Lead tracking, email sequences, contact segments |
| Salesforce | `salesforce` | Opportunity pipeline, closed-won attribution |
| Instagram | `instagram` | Organic social posts and stories |
| TikTok | `tiktok` | Short-form video campaigns |
| YouTube | `youtube` | Long-form and pre-roll campaigns |
| SEMrush | `semrush` | SEO, keyword tracking, competitor analysis |
| Google Slides | `gslides` | Campaign decks and presentations |
| Fal | `fal` | AI-generated ad creative images |

## Files

- `references/campaign-brief-template.md` — fillable brief template
- `references/channel-specs.md` — image sizes, character limits, and format specs per channel
- `references/retro-template.md` — post-campaign retrospective template
