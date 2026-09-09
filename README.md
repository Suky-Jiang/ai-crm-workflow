# AI-Assisted Lead Capture & Classification Workflow

An automated lead capture, AI classification, and routing system built with **Tally → Make → Google Sheets**.

## 🎯 Overview

This workflow automatically:
1. **Captures** marketing enquiries from Tally
2. **Classifies** leads using AI (Hot/Warm/Cold)
3. **Summarizes** each lead with AI
4. **Saves** everything to Google Sheets
5. **Triggers** follow-up actions for hot leads

## 🔄 Workflow Architecture

```
Tally (Lead Submission)
       ↓
Someone submits a marketing enquiry
       ↓
Make detects the new response
       ↓
AI categorizes the lead
       ↓
AI writes a short summary
       ↓
Google Sheets saves everything
       ↓
   ┌───────────────┐
   ↓               ↓
 HOT            WARM/COLD
   ↓               ↓
Trigger         Keep for
Follow-up       nurturing
```

## 📋 Tally Form

Create a form called: **Marketing Enquiry Form**

Add these 5 questions:

1. **Name** — Short answer
2. **Email address** — Email
3. **Company** — Short answer
4. **What are you interested in?** — Multiple choice
   - Marketing automation
   - Lead generation
   - CRM
   - Content marketing
   - Analytics
5. **When are you looking to work on this?** — Multiple choice
   - Immediately
   - Within 1–3 months
   - Later / Just researching

✅ Free Tally accounts have Make integration built-in via webhooks.

## 📊 Google Sheets Structure

Create a sheet called: **AI Marketing Leads**

Column headings in Row 1:

| A | B | C | D | E | F | G |
|---|---|---|---|---|---|---|
| Name | Email | Company | Interest | Timeline | AI Lead Type | AI Summary |

**Example populated data:**

| Name | Email | Company | Interest | Timeline | AI Lead Type | AI Summary |
|------|-------|---------|----------|----------|--------------|-----------|
| Sarah | sarah@company.com | Acme | Marketing automation | Immediately | Hot | Looking for automation solution for immediate implementation |
| James | james@tech.io | TechCorp | CRM | 1–3 months | Warm | Exploring CRM options for team expansion |
| Amy | amy@startup.co | StartupXYZ | Content marketing | Researching | Cold | Early-stage research, no timeline set |

## 🤖 AI Classification Rules

### HOT ✅
- Clear business need identified
- Ready to solve immediately or within 1–3 months
- High purchase intent

**Example:** "Sarah is looking for a marketing automation solution and wants to implement immediately."

### WARM 🟡
- Relevant business need
- Not ready for immediate action
- Planning within 3+ months or exploring options

**Example:** "James is exploring CRM solutions and plans to decide within 1–3 months."

### COLD ❄️
- Early-stage research
- No clear timeline or urgency
- Low purchase intent

**Example:** "Amy is researching content marketing tools but has no concrete timeline."

## 🚀 Make Workflow Setup

### Step 1: Create the Scenario

1. Go to **Make.com** (free account)
2. Click **Scenarios → Create a new scenario**
3. Click the **+** button and search for **Tally**
4. Select **Watch New Responses**
5. Authorize Tally and select your form

This is your **trigger**: When someone submits Tally → Make starts automatically

### Step 2: Extract Form Data

Add a **Text Aggregator** or **Parse JSON** module to extract:
- Name
- Email
- Company
- Interest (choice)
- Timeline (choice)

### Step 3: AI Classification

Add **Make AI Toolkit** (or OpenAI) module:

**Prompt:**
```
Classify this lead as HOT, WARM, or COLD based on their answers:
- Interest: {Interest}
- Timeline: {Timeline}

Rules:
HOT: Clear business need + Immediately or 1–3 months
WARM: Relevant need but 3+ months or exploring
COLD: Researching or no timeline

Return ONLY the classification (Hot/Warm/Cold).
```

### Step 4: AI Summary

Add another **AI Toolkit** module:

**Prompt:**
```
Write a one-sentence summary of this lead's needs:
Name: {Name}
Interest: {Interest}
Timeline: {Timeline}

Be concise and action-oriented.
```

### Step 5: Save to Google Sheets

Add **Google Sheets** module:
- Select your **AI Marketing Leads** sheet
- Action: **Add a row**
- Map the fields:
  - A (Name) → {Name}
  - B (Email) → {Email}
  - C (Company) → {Company}
  - D (Interest) → {Interest}
  - E (Timeline) → {Timeline}
  - F (AI Lead Type) → {AI Classification}
  - G (AI Summary) → {AI Summary}

### Step 6: Hot Lead Trigger (Optional)

Add an **IF** router after classification:
- **IF** AI Lead Type = "Hot"
  - **THEN:** Send email notification / Slack message / Create calendar event
  - Trigger your follow-up action

## 🔧 Setup Checklist

- [ ] Create Tally form with 5 questions
- [ ] Create Google Sheet **AI Marketing Leads** with 7 columns
- [ ] Create Make account and authorize Tally + Google Sheets
- [ ] Set up Make scenario:
  - [ ] Tally trigger (Watch New Responses)
  - [ ] AI classification module
  - [ ] AI summary module
  - [ ] Google Sheets add row action
  - [ ] (Optional) Hot lead follow-up trigger
- [ ] Test end-to-end with sample Tally submission
- [ ] Turn on scenario automation

## 📊 Key Metrics

Track the effectiveness of this workflow:
- **Lead capture rate** — Tally submissions → Google Sheets rows
- **Classification accuracy** — Manual review of AI categorizations
- **Hot lead ratio** — % of leads classified as Hot
- **Response time** — Time from submission to sheet entry (should be <1 minute)
- **Follow-up completion** — Hot leads → Actual follow-up actions taken

## 💡 Example Lead Flow

**Input (Tally Submission):**
```
Name: Sarah Chen
Email: sarah@company.com
Company: Acme Corp
Interest: Marketing automation
Timeline: Immediately
```

**Automatic Processing:**
```
AI Classification: Hot
AI Summary: Looking for marketing automation solution with immediate implementation timeline
```

**Output (Google Sheets):**
```
Name: Sarah Chen
Email: sarah@company.com
Company: Acme Corp
Interest: Marketing automation
Timeline: Immediately
AI Lead Type: Hot
AI Summary: Marketing manager seeking automation solution for immediate implementation
```

**Trigger:** Create follow-up task / Send welcome email / Add to sales pipeline

## 🎓 What This Demonstrates

✓ **Form Automation** — Tally form collection
✓ **Workflow Orchestration** — Make scenario with multiple steps
✓ **AI Classification** — Smart lead scoring using Make AI Toolkit
✓ **Data Pipeline** — Automatic sheet population
✓ **Conditional Logic** — Different actions based on lead hotness
✓ **Real-time Processing** — Instant responses from submission to sheet

## 🛠️ Tech Stack

- **Tally** — Free form builder with webhook support
- **Make** — Workflow automation platform
- **Make AI Toolkit** — AI classification & summarization
- **Google Sheets** — Cloud spreadsheet storage

All free tier options available for small-scale testing.

---

**Built with:** Tally • Make • Google Sheets • AI Toolkit • Workflow Automation
