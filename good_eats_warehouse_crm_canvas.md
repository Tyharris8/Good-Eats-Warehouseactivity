{
  "nodes": [
    {
      "id": "c100000000000001",
      "type": "text",
      "x": 0,
      "y": 0,
      "width": 420,
      "height": 220,
      "color": "5",
      "text": "# Contract: Good Eats, Warehouse\n\n- **Data File:** `customers.json`\n- **Entity Type:** Customer\n- **Department:** Warehouse\n- **System Purpose:** CRM for tracking client communication and call schedules."
    },
    {
      "id": "c100000000000002",
      "type": "text",
      "x": 480,
      "y": -220,
      "width": 560,
      "height": 440,
      "color": "4",
      "text": "## Fields Schema\n\n| Field | Type | Example | Meaning |\n|---|---|---|---|\n| `id` | text | C001 | a unique id for this row |\n| `customerName` | text | Bistro On Main | the name of the customer or client business |\n| `contactPerson` | text | Sarah Jenkins | the primary point of contact |\n| `lastContactDate` | date (YYYY-MM-DD) | 2026-09-15 | the date we last spoke with the customer |\n| `daysSinceContact` | number | 20 | number of days elapsed since last contact |\n| `followUpDue` | yes/no | yes | whether the customer is due for a call |\n| `orderFrequencyDays` | number | 14 | expected number of days between customer orders |"
    },
    {
      "id": "c100000000000003",
      "type": "text",
      "x": 480,
      "y": 260,
      "width": 420,
      "height": 220,
      "color": "1",
      "text": "## Tag & Alert Rules\n\n- **Tag Field:** `followUpDue` *(displayed on `.tag`)*\n- **Alert Rule:** `followUpDue is yes` *(triggers `.alert` class on card)*"
    },
    {
      "id": "c100000000000004",
      "type": "text",
      "x": -500,
      "y": -180,
      "width": 420,
      "height": 240,
      "color": "3",
      "text": "## Summary Numbers (`#summary`)\n\n1. **Total Customers**\n   - *Calculation:* Count of all objects\n2. **Follow-ups Overdue**\n   - *Calculation:* Count where `followUpDue` is `yes`\n3. **Recent Contacts**\n   - *Calculation:* Count where `daysSinceContact <= 7`"
    },
    {
      "id": "c100000000000005",
      "type": "text",
      "x": -500,
      "y": 100,
      "width": 420,
      "height": 260,
      "color": "6",
      "text": "## Page Hooks\n\n- `#title` — Main header / title slot\n- `#summary` — Summary metric cards\n- `#list` — Container element for cards\n- `.card` — Individual customer card component\n- `.tag` — Element displaying the tag field\n- `.alert` — Class applied when alert rule matches"
    }
  ],
  "edges": [
    {
      "id": "e100000000000001",
      "fromNode": "c100000000000001",
      "fromSide": "right",
      "toNode": "c100000000000002",
      "toSide": "left",
      "label": "defines schema"
    },
    {
      "id": "e100000000000002",
      "fromNode": "c100000000000001",
      "fromSide": "right",
      "toNode": "c100000000000003",
      "toSide": "left",
      "label": "defines highlight behavior"
    },
    {
      "id": "e100000000000003",
      "fromNode": "c100000000000001",
      "fromSide": "left",
      "toNode": "c100000000000004",
      "toSide": "right",
      "label": "calculates"
    },
    {
      "id": "e100000000000004",
      "fromNode": "c100000000000001",
      "fromSide": "left",
      "toNode": "c100000000000005",
      "toSide": "right",
      "label": "binds to DOM"
    }
  ]
}