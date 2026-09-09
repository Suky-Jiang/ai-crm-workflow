# AI-Assisted CRM Workflow

An automated lead capture, classification, and routing system built with **Typeform → Attio → AI**.

## 🎯 Overview

This workflow automatically:
1. **Captures** marketing enquiries from Typeform
2. **Stores** contact data in Attio
3. **Classifies** leads using AI (Hot/Warm/Cold)
4. **Routes** hot leads for immediate follow-up

## 🔄 Workflow Architecture

```
Typeform (Lead Submission)
       ↓
Someone submits a marketing enquiry
       ↓
Attio automatically creates/updates the contact
       ↓
AI reads their answers
       ↓
AI classifies them: HOT / WARM / COLD
       ↓
   ┌───┴───┐
   ↓       ↓
 HOT    WARM/COLD
   ↓       ↓
Create  Keep in Attio
Task    for later
```

## 📋 Typeform Questions

The form collects 5 essential fields:

1. **Name** — Contact's full name
2. **Work Email** — Professional email address
3. **Company** — Organization name
4. **What are you interested in?** — Business need/solution type
5. **When are you looking to solve this?** — Timeline
   - Immediately
   - Within 1–3 months
   - Later / Just researching

## 🗂️ Attio Fields

Each lead creates a contact record with these fields:

| Field | Example | Description |
|-------|---------|-------------|
| Name | Sarah Chen | Contact's full name |
| Email | sarah@company.com | Work email address |
| Company | Acme | Organization name |
| Interest | Marketing automation | Business need/solution type |
| Timeline | Immediately | Urgency level |
| AI Lead Type | Hot | Classification: Hot/Warm/Cold |
| AI Summary | Looking for automation solution soon | One-sentence classification reason |
| Status | New | Lead status in pipeline |

## 🤖 AI Classification Rules

### HOT ✅
- Clear business need identified
- Ready to solve immediately or within 1–3 months
- High purchase intent

**Example:** "Sarah Chen is a marketing manager looking for a marketing automation solution within the next month."

### WARM 🟡
- Relevant business need
- Not ready for immediate action
- Planning ahead or exploring options

**Example:** "John is researching CRM solutions for his sales team but isn't planning to implement until Q4."

### COLD ❄️
- Early-stage research
- No clear timeline or urgency
- Low purchase intent

**Example:** "Alice is exploring automation tools but has no concrete timeline or current business problem."

## 🚀 Automation Logic

### If Lead is HOT
- ✓ Classify as "Hot" in Attio
- ✓ Create a follow-up task (auto-assigned or manually)
- ✓ Set Status to "New"
- ✓ Flag for immediate sales outreach

### If Lead is WARM or COLD
- ✓ Classify accordingly in Attio
- ✓ Keep in pipeline for nurture
- ✓ Set Status to "New"
- ✓ Schedule for later follow-up

## 🔧 Setup Checklist

- [ ] Create Typeform with 5 questions
- [ ] Set up Attio webhook to receive form submissions
- [ ] Create Attio contact fields:
  - Name, Email, Company, Interest, Timeline
  - AI Lead Type, AI Summary, Status
- [ ] Connect AI classification tool (e.g., OpenAI, Claude via Zapier/Make)
- [ ] Configure conditional routing:
  - Hot → Create follow-up task
  - Warm/Cold → Add to nurture list
- [ ] Test end-to-end with sample submissions

## 📊 Key Metrics

Track the effectiveness of this workflow:
- **Lead capture rate** — Typeform submissions → Attio contacts
- **Classification accuracy** — Manual review of AI classifications
- **Hot lead conversion** — HOT leads → Booked calls/deals
- **Response time** — Follow-up task creation time

## 💡 Example Lead Flow

**Input (Typeform):**
```
Name: Sarah Chen
Email: sarah@company.com
Company: Acme Corp
Interest: Marketing automation
Timeline: Immediately
```

**Output (Attio):**
```
Name: Sarah Chen
Email: sarah@company.com
Company: Acme Corp
Interest: Marketing automation
Timeline: Immediately
AI Lead Type: Hot
AI Summary: Marketing manager seeking automation solution for immediate implementation
Status: New

Action: Create follow-up task for sales team
```

## 🎓 What This Demonstrates

✓ **CRM Integration** — Automated contact management
✓ **AI Classification** — Smart lead scoring without manual input
✓ **Automation** — Workflow execution at scale
✓ **Conditional Logic** — Different actions based on lead type
✓ **Lead Qualification** — Prioritize hot opportunities

---

**Built with:** Typeform • Attio • AI Classification • Workflow Automation
