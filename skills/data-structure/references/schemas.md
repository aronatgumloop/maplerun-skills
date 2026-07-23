# Maplerun Data Schemas

Full annotated schemas for all core data objects. These are the canonical definitions — all integrations and exports must conform to these shapes.

## Customer

```json
{
  "customer_id":    "string (UUID) — primary key, immutable",
  "full_name":      "string — display name, max 120 chars",
  "email":          "string — lowercase, validated email format",
  "segment":        "enum: enterprise | smb | consumer",
  "region":         "string — ISO 3166-1 alpha-2 country code (e.g. US, CA, GB)",
  "currency_code":  "enum: USD | CAD | EUR | GBP",
  "hubspot_id":     "string | null — linked HubSpot contact ID",
  "salesforce_id":  "string | null — linked Salesforce contact ID",
  "created_at":     "ISO 8601 UTC datetime",
  "updated_at":     "ISO 8601 UTC datetime"
}
```

## Sales Order

```json
{
  "order_id":      "string (UUID) — primary key",
  "customer_id":   "string (UUID) — FK → Customer",
  "line_items": [
    {
      "sku":        "string — product code",
      "name":       "string — product display name",
      "qty":        "integer — must be > 0",
      "unit_price": "float — 2 decimal places",
      "discount":   "float | null — percentage 0–100"
    }
  ],
  "subtotal":      "float",
  "tax":           "float",
  "total":         "float",
  "currency_code": "enum: USD | CAD | EUR | GBP",
  "status":        "enum: draft | confirmed | shipped | cancelled | refunded",
  "created_at":    "ISO 8601 UTC datetime",
  "updated_at":    "ISO 8601 UTC datetime"
}
```

## Campaign

```json
{
  "campaign_id":   "string (UUID)",
  "name":          "string — max 80 chars",
  "type":          "enum: brand_awareness | lead_gen | product_launch | retention | event",
  "status":        "enum: draft | active | paused | completed",
  "start_date":    "ISO 8601 date",
  "end_date":      "ISO 8601 date",
  "budget_usd":    "float",
  "owner_email":   "string — Maplerun team member email",
  "channels":      "array of strings — e.g. [\"email\", \"instagram\", \"paid_search\"]",
  "created_at":    "ISO 8601 UTC datetime"
}
```

## User Profile (Internal)

```json
{
  "user_id":       "string (UUID)",
  "email":         "string",
  "role":          "enum: admin | editor | viewer",
  "team":          "string — e.g. marketing, sales, ops",
  "created_at":    "ISO 8601 UTC datetime",
  "last_login_at": "ISO 8601 UTC datetime | null"
}
```
