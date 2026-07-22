# Data Structure Skill

## Overview
This skill guides the agent in understanding, organizing, and working with Maplerun's internal data structures — including databases, spreadsheets, APIs, and document schemas.

## When to Use
- Interpreting raw data exports or database schemas
- Structuring outputs into consistent formats (JSON, CSV, tables)
- Transforming messy data into clean, normalized records
- Answering questions about how data is organized across systems

## Data Standards

### Naming Conventions
- Fields: `snake_case` (e.g., `customer_id`, `created_at`)
- Tables/collections: `plural_snake_case` (e.g., `sales_orders`, `user_profiles`)
- Files: `kebab-case` (e.g., `q2-revenue-report.csv`)

### Core Data Types
| Type | Format | Example |
|------|--------|---------|
| Date | ISO 8601 | `2026-07-22` |
| DateTime | ISO 8601 UTC | `2026-07-22T22:00:00Z` |
| Currency | Float, 2 decimals | `1299.99` |
| ID | String UUID | `"a3f2c1d4-..."` |
| Boolean | true/false | `true` |

### Approved Output Formats
- **Tabular data**: CSV or XLSX with headers in row 1
- **Structured records**: JSON with consistent key ordering
- **Reports**: Markdown tables or HTML for dashboards

## Data Quality Rules
1. No blank required fields — use `null` explicitly
2. Deduplicate records before aggregation
3. Always validate date ranges (start ≤ end)
4. Currency fields must always include a `currency_code` companion field
5. Personal data (PII) must never appear in logs or debug output

## Key Internal Schemas

### Customer Record
```json
{
  "customer_id": "uuid",
  "full_name": "string",
  "email": "string",
  "segment": "enterprise | smb | consumer",
  "created_at": "ISO8601",
  "region": "string",
  "currency_code": "USD | CAD | EUR"
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

## Notes
- Always confirm data source before transforming (Google Sheets, HubSpot, Salesforce, etc.)
- When in doubt, preserve the original values and add a `_transformed` suffix to modified fields
