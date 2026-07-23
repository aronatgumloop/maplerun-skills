---
name: data-structure
description: Guides the agent on Maplerun's internal data schemas, naming conventions, approved output formats, and data quality rules. Use when interpreting raw exports, structuring outputs into JSON/CSV/tables, transforming messy records, or answering questions about how data is organized across systems.
icon: database
color: Blue
---

# Data Structure

## When to Use

Activate this skill when the task involves:

- Reading or interpreting raw data exports (CSV, JSON, database schemas)
- Structuring outputs into a consistent format (JSON, CSV, Markdown tables)
- Transforming or normalizing records from HubSpot, Salesforce, Google Sheets, or internal DBs
- Answering questions about field names, data types, or how records relate to each other
- Validating data before it's stored or shared

## Naming Conventions

| Scope | Convention | Example |
|-------|------------|--------|
| Fields / columns | `snake_case` | `customer_id`, `created_at` |
| Tables / collections | `plural_snake_case` | `sales_orders`, `user_profiles` |
| File names | `kebab-case` | `q2-revenue-report.csv` |
| UUIDs | String, not integer | `"a3f2c1d4-..."` |

## Core Data Types

| Type | Format | Example |
|------|--------|--------|
| Date | ISO 8601 | `2026-07-22` |
| DateTime | ISO 8601 UTC | `2026-07-22T22:00:00Z` |
| Currency | Float, 2 dp | `1299.99` (always paired with `currency_code`) |
| ID | String UUID | `"a3f2c1d4-..."` |
| Boolean | `true` / `false` | `true` |
| Enum | lowercase string | `"enterprise"`, `"confirmed"` |

## Approved Output Formats

- **Tabular data** → CSV or XLSX, headers in row 1, `snake_case` column names
- **Structured records** → JSON with consistent key ordering (alphabetical within each object)
- **Reports / summaries** → Markdown tables or HTML for dashboards

## Data Quality Rules

1. No blank required fields — use `null` explicitly, never empty string `""`
2. Deduplicate records before aggregation (match on `id` fields, not names)
3. Always validate date ranges: `start_date` must be ≤ `end_date`
4. Every currency amount field must be accompanied by a `currency_code` field
5. PII (emails, names, phone numbers) must never appear in logs or debug output
6. When in doubt, preserve original values and add a `_normalized` suffix to modified fields

## Key Schemas

Full schema definitions live in `references/schemas.md`. Quick reference:

### Customer
```json
{
  "customer_id": "uuid",
  "full_name": "string",
  "email": "string",
  "segment": "enterprise | smb | consumer",
  "region": "string",
  "currency_code": "USD | CAD | EUR",
  "created_at": "ISO8601"
}
```

### Sales Order
```json
{
  "order_id": "uuid",
  "customer_id": "uuid",
  "line_items": [{"sku": "string", "qty": "int", "unit_price": "float"}],
  "total": "float",
  "currency_code": "string",
  "status": "draft | confirmed | shipped | cancelled",
  "created_at": "ISO8601"
}
```

## Workflow

1. **Identify the source** — confirm whether data is from Sheets, HubSpot, Salesforce, or a raw file
2. **Check schema match** — compare incoming field names against the approved schemas in `references/schemas.md`
3. **Transform** — rename fields, cast types, apply quality rules
4. **Output** — use the approved format for the task (CSV for downloads, JSON for APIs, table for chat)

## Files

- `references/schemas.md` — full annotated schemas for all core Maplerun data objects
- `references/field-glossary.md` — plain-English definitions for every field across systems
