---
name: report-bug
description: Create a new bug in the Notion "🐛 Bugs" database with the correct properties and a complete bug report body so the tech team can investigate quickly. Use for functional or visual defects (actual behavior differs from expected). Do not use for feature requests, improvements, or tech debt.
user-invocable: true
---

## When to use
Use when the user wants to report a functional or visual defect (actual behavior differs from expected behavior).
Do NOT use for feature requests, product improvements, tech debt, or general feedback.

## Incident guardrail
If the report suggests a widespread outage or production incident (many users blocked, system down, critical regression), do NOT file a normal bug.
Instead, tell the user to follow the incident process and stop.

## Notion target
- Data source: `collection://72bd13ba-42cf-487c-abf4-d97abf546745`
- Default template: https://www.notion.so/0db6444d96b348498175dc8d96425721
- Title property name: `Key`

---

## Inputs to collect

Ask only for what is missing. Minimum to create a useful bug:

1. Bug title (or generate from expected vs actual)
2. Expected behavior
3. Actual behavior
4. Reproduction steps
5. Environment: platform (Web / iOS / Android), version, browser (if web)
6. Impact: who is affected, frequency, workaround

Optional but helpful:
- Screenshots / video
- Error messages / logs
- Slack link / Zendesk ID

If the user wants to log now but info is missing, still create the bug and add a "Missing info" section with open questions.

---

## Properties to set

Use only these exact property names.

**Required / strongly recommended:**

| Property | Type | Notes |
|---|---|---|
| `Key` | title | Concise, specific bug title |
| `Status` | status | Default to `"Tech"`. Use `"Product"` or `"Need client input"` only when clearly needed. Other values: `"Done"`, `"Canceled"` |
| `Reporter` | person | Person reporting the bug. Default to current user if not specified. |
| `CFT` | select | Owning CFT when known |

**When relevant / available:**

| Property | Type | Values / notes |
|---|---|---|
| `Tech stack` | select | `"Back end"`, `"Web"`, `"iOS"`, `"Android"`, `"Low code"`, `"Data Eng"`, `"ML Eng"`, `"Security"` |
| `Product stack` | select | `"PM"`, `"Content Design"`, `"Design"` |
| `Slack link` | url | Link to the Slack thread/message that triggered the bug |
| `Zendesk ID` | text | Customer ticket ID if applicable |
| `Labels` | multi_select | Add only if a clear match exists in the existing options |
| `Ops team` | select | Fill only if bug originated from Ops |
| `Ops agent` | person | Fill only if bug originated from Ops |
| `Ops engineer` | person | Fill only if bug originated from Ops |
| `CS client updated` | checkbox | Set true only if the customer has already been updated |
| `Due` | date | Set only if explicitly requested |

**Never set manually:**
- `Resolved at` — auto-managed when Status moves to Done (unless user explicitly requests a correction)
- Formula / rollup / button fields: `SLA alert`, `SLA`, `Release - display`, `Add Tech Kanban`, `Mark as Done`

---

## Page body template

Fill each section with the information gathered. Leave a section blank or add a question under "Missing info" if information is unavailable.

```
### Summary
[What is broken and who is impacted.]

### Expected
- …

### Actual
- …

### Reproduction steps
1. …
2. …
3. …

### Environment
- Platform:
- App version / Browser:
- Org / account (if relevant):
- Locale (if relevant):

### Impact
- Severity:
- Frequency:
- Workaround:

### Evidence
- Screenshot / video:
- Error message / logs:
- Links (Slack / Zendesk / other):

### Missing info / questions
- …
```

---

## Execution steps

1. Gather the minimum inputs. If something is missing, ask for it — but don't block creation if the user wants to proceed.
2. Create a new page in `collection://72bd13ba-42cf-487c-abf4-d97abf546745` using template `https://www.notion.so/0db6444d96b348498175dc8d96425721`.
3. Set properties:
   - `Key` = generated or provided title
   - `Reporter` = current user unless specified
   - `Status` = `"Tech"` by default
   - `CFT` / `Tech stack` / `Product stack` = set when known, otherwise leave empty
   - `Slack link` / `Zendesk ID` / Ops fields / `Labels` = set when provided and valid
4. Write the page body using the template above.
5. Return the created Notion URL to the user.

---

## Quality bar

The created bug should be actionable for engineering without needing immediate follow-up. If key information is truly missing, add explicit questions in the "Missing info" section rather than leaving the report vague.
