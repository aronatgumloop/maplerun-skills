# Field Glossary

Plain-English definitions for every recurring field across Maplerun's data systems.

| Field | Type | Definition |
|-------|------|------------|
| `customer_id` | UUID string | Unique identifier for a customer. Never reused. Maps to HubSpot Contact ID and Salesforce Contact ID. |
| `order_id` | UUID string | Unique identifier for a sales order. |
| `segment` | enum | Customer tier: `enterprise` (500+ employees), `smb` (10–499), `consumer` (individual). |
| `region` | string | ISO 3166-1 alpha-2 country code. |
| `currency_code` | enum | Three-letter ISO 4217 currency code (USD, CAD, EUR, GBP). Always stored alongside monetary amounts. |
| `status` | enum | Lifecycle state of a record. Values vary by object — see schemas.md for allowed values per type. |
| `created_at` | ISO 8601 UTC | Timestamp when the record was first written to the database. Immutable. |
| `updated_at` | ISO 8601 UTC | Timestamp of the last modification. Updated automatically on every write. |
| `owner_email` | string | Email of the Maplerun team member responsible for a record. |
| `sku` | string | Internal product code. Format: `PROD-XXXX` (e.g. `PROD-0042`). |
| `hubspot_id` | string | Linked record ID in HubSpot CRM. May be null for pre-HubSpot records. |
| `salesforce_id` | string | Linked record ID in Salesforce. May be null if not synced. |
