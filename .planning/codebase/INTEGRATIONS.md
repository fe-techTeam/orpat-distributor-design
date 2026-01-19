# External Integrations

**Analysis Date:** 2026-01-19

## APIs & External Services

**Backend API (Planned):**
- Service: Custom ORPAT Distributor API
- Base URL: Configurable via `{{base_url}}` Postman variable
- Auth: Bearer token via `Authorization: Bearer {{token}}`
- Specification: `Distributor APP.postman_collection.json`

**Endpoints Documented:**

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/login` | POST | User authentication |
| `/new-arrival-products` | GET | New product listings |
| `/last-purchase-products` | GET | Previously bought items |
| `/people-also-bought-products` | GET | Recommendations |
| `/distributor-category-lists` | GET | Product categories |
| `/display-sub-category-lists-from-category` | GET | Subcategories |
| `/display-product-lists-from-sub-category` | GET | Products by category |
| `/display-parts-lists-from-products` | GET | Product parts |
| `/display-all-running-scheme-lists` | GET | Active promotions |
| `/display-scheme-sub-category-lists` | GET | Scheme categories |
| `/display-scheme-product-lists` | GET | Scheme products |
| `/company-scheme-order-preview` | POST | Preview scheme order |
| `/store-company-scheme-order` | POST | Submit scheme order |
| `/save-company-normal-order` | POST | Submit normal order |
| `/save-company-part-order` | POST | Submit parts order |
| `/orpat-pending-orders` | GET | Pending orders |
| `/orpat-approved-orders` | GET | Approved orders |
| `/orpat-dispatched-order` | GET | Dispatched orders |
| `/view-invoice-details` | GET | Invoice detail |
| `/view-orpat-order-details` | GET | Order detail |

## Data Storage

**Databases:**
- Not applicable (static prototype)
- Backend database referenced via API (table names in query params)
- Tables referenced: `invoice_order_lists`, `cnf_pending_part_order`

**File Storage:**
- Local: `images/` directory (27 product images)
- External: `orpatgroup.com` WordPress CDN

## Content Delivery

**Google Fonts:**
- Service: Google Fonts API
- Font: Inter (weights 400, 500, 600, 700)
- Integration: `<link>` tags in HTML head
- URLs:
  - `https://fonts.googleapis.com`
  - `https://fonts.gstatic.com`

**Product Images (External):**
- CDN: `https://orpatgroup.com/wp-content/uploads/`
- Usage: Some product images in UI mockups
- Examples:
  - `https://orpatgroup.com/wp-content/uploads/2020/12/Economy-Ceiling-Fans...`
  - `https://orpatgroup.com/wp-content/uploads/2024/09/Air-Legend-White...`

**Image CDN (API Response):**
- CDN: `https://orpat-image.orpatdistributors.com/app/products/`
- Usage: Product images returned by API
- Referenced in: `Distributor APP.postman_collection.json`

## Authentication & Identity

**Auth Pattern (Planned):**
- Type: Bearer token authentication
- Header: `Authorization: Bearer {{token}}`
- Endpoint: `POST /login`
- Credentials: email, password, pushtoken

**Login Request:**
```json
{
  "email": "user@example.com",
  "password": "********",
  "pushtoken": ""
}
```

## Push Notifications

**Push Token Support:**
- Parameter: `pushtoken` in login request
- Service: Not specified (likely Firebase FCM or similar)
- Purpose: Enable mobile push notifications

## CI/CD & Deployment

**Hosting:**
- Platform: GitHub Pages compatible (static files)
- Repository: `https://github.com/fe-techTeam/orpat-distributor-design.git`
- Deployment: Manual push to main branch

**CI Pipeline:**
- Not configured
- Manual development workflow

## Environment Configuration

**Development:**
- Required: Web browser only
- No environment variables needed
- Open `index.html` directly

**API Testing:**
- Tool: Postman
- Collection: `Distributor APP.postman_collection.json`
- Variables: `{{base_url}}`, `{{token}}`

**Production (Future):**
- Static hosting for prototype
- API server for backend services
- Environment-specific API base URLs

## Third-Party Tools

**Postman:**
- Purpose: API testing and documentation
- Collection ID: `08ba65ac-9542-432c-82b8-f5d06a3dd00e`
- Exporter ID: `4876775`

**GitHub:**
- Purpose: Version control
- Remote: `origin`
- URL: `https://github.com/fe-techTeam/orpat-distributor-design.git`

## Webhooks & Callbacks

**Incoming:**
- Not applicable (static prototype)

**Outgoing:**
- Not applicable (static prototype)

---

*Integration audit: 2026-01-19*
*Update when adding/removing external services*
