# One Company: Build Roles and Prompts

MGIS 130, Week 7. Each person on your team builds one file. The files only work together if everyone builds from the same contract, so the repo owner writes the contract first and everyone else builds from it.

## How the next 25 minutes go

1. **Repo owner:** create the repo, add your teammates as collaborators, then write the contract (prompt below) and save it in the repo as `CONTRACT.md`. Commit it, and paste it in your team chat too.
2. **Everyone else, while you wait:** accept the invitation, open the repo in github.dev (press `.` on the repo page), find your role below, and open Gemini.
3. **Once `CONTRACT.md` is committed:** reload github.dev so you can see it. Copy the whole contract into your role's prompt where it says `[paste CONTRACT.md here]`.
4. **Make your file in github.dev:** in the Explorer, New File, use the exact file name, paste Gemini's answer, then Source Control, write a message that says what you added, and Commit & Push.
5. **Repo owner:** turn on Pages (Settings, Pages, Branch: main, Save).
6. **Everyone:** open the live page about a minute after the last commit. If something is missing or broken, check each file against the contract. That's usually where the problem is.

| Role | Your file | Team of 4 |
|---|---|---|
| Repo owner | `CONTRACT.md`, `README.md`, turns on Pages | also writes the data file |
| Data | the data file named in the contract | done by the owner |
| Page | `index.html` | |
| Look | `style.css` | |
| Logic | `script.js` | |

If Commit & Push fails because a teammate committed first: copy your file's text, reload github.dev, paste it back, and commit again.

## The page hooks (every department uses these)

These ids and classes are the same for every team. They're how the page, the look and the logic find each other.

| Hook | What it is |
|---|---|
| `#title` | the heading: your company and department |
| `#summary` | a row of 2 or 3 numbers (counts or totals) |
| `#list` | where the cards go, one card per row of data |
| `.card` | one row of data |
| `.tag` | a short label on a card, like a status or a type |
| `.alert` | added to a card that needs attention |

## Ideas for each department

| Department | Data file | Each row is | Alert when |
|---|---|---|---|
| Sales (CRM) | `customers.json` | a customer | we haven't talked to them in 30 days |
| Warehouse (SCM) | `inventory.json` | a product we stock | on hand is below the reorder point |
| Finance | `orders.json` | an order | it's unpaid after 14 days |
| Analytics (BI) | `sales.json` | a product's sales this week and last week | this week is lower than last week |
| Operations (workflow) | `requests.json` | a refund, discount or special-order request | it's been waiting more than 3 days |
| Front Counter | `menu.json` | a menu item | it's sold out |

---

## Repo owner: the contract

Fill in the brackets, then paste the whole prompt into Gemini.

```text
I'm the repo owner for the [Sales] department of [our company name], a [bagel bakery].
Our department's software is a [CRM]. It should show [our customers, when we last talked to them, and who is due for a call].

Fill in the contract template below for our team. Choose 6 to 8 fields. Every row must start with an id field.
Use simple field names with no spaces (like lastContact). Types can only be text, number, date (YYYY-MM-DD) or yes/no.
Do not write any code. Return only the filled-in template as Markdown.

# Contract: [company], [department]

Data file: [name].json
The file is a JSON array. Each object is one [customer / product / order / request].

| Field | Type | Example | Meaning |
|---|---|---|---|
| id | text | C001 | a unique id for this row |

Tag field: [the field shown as the .tag on each card]
Summary numbers: [2 or 3 numbers, and how each one is counted]
Alert rule: [when a card gets the .alert class]

Page hooks (the same for every department): #title, #summary, #list, .card, .tag, .alert
```

Read what comes back before you commit it. You're the one who decides what your department tracks. Change a field name or the alert rule if it doesn't fit.

## Data: the data file

```text
Here is our team's contract:

[paste CONTRACT.md here]

Write the data file named in the contract. It is a JSON array with 8 to 10 rows.
Use the field names exactly as written in the contract, in the same order, with the same types.
Dates are YYYY-MM-DD. Numbers have no $ signs or commas. Yes/no fields are true or false.
Make up realistic people and businesses. Nobody real.
At least two rows should meet the alert rule.
Return only the JSON.
```

## Page: index.html

```text
Here is our team's contract:

[paste CONTRACT.md here]

Write index.html for our page.
Use the page hooks from the contract exactly: an h1 with id="title", then an element with id="summary", then an element with id="list".
Put our company and department name in the title. Leave #summary and #list empty; script.js fills them in.
Link style.css in the head. Load script.js at the end of the body.
No inline styles, no inline scripts, no libraries.
Return only the HTML.
```

## Look: style.css

```text
Here is our team's contract:

[paste CONTRACT.md here]

Write style.css for our page.
Style only the page hooks in the contract: #title, #summary, #list, .card, .tag and .alert.
Show the cards in a grid that also works on a phone. Show the summary numbers large, in a row.
Use one accent color that fits [our company]. Make .alert cards easy to spot.
No frameworks and no imports.
Return only the CSS.
```

## Logic: script.js

```text
Here is our team's contract:

[paste CONTRACT.md here]

Write script.js for our page. Plain JavaScript, no libraries.
1. Fetch the data file named in the contract.
2. Use the field names exactly as written in the contract.
3. Fill #summary with the summary numbers from the contract.
4. For each row, add a div with the class "card" to #list. Show the main fields, and put the tag field in a span with the class "tag".
5. Add the class "alert" to cards that meet the alert rule.
6. If the file can't be loaded or read, show the error message inside #list so we can see what went wrong.
Return only the JavaScript.
```

## Repo owner: README.md

```text
Here is our team's contract:

[paste CONTRACT.md here]

Write README.md for our repo. Include our company and department, what our page shows,
who is on the team ([names]), and one line on what each file does
(CONTRACT.md, the data file, index.html, style.css, script.js).
Keep it under 150 words. Return only the Markdown.
```

---

## Before you leave

Open the **Issues** tab on your repo and add one New issue: the next thing your department's page should do. That's version 1.
