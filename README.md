# Rasa Nusantara - Indonesian Culinary UMKM Showcase & Management

![Project Banner](screenshots/banner.webp)

![Project Type](https://img.shields.io/badge/Project_Type-Full--Stack-blue)
![Primary Language](https://img.shields.io/badge/Primary_Language-TypeScript-blue)
![Framework](https://img.shields.io/badge/Framework-Next.js_%26_Express.js-orange)
![Runtime / Platform](https://img.shields.io/badge/Runtime_%2F_Platform-Node.js-green)
![Package Manager](https://img.shields.io/badge/Package_Manager-npm-red)
![Build Tool](https://img.shields.io/badge/Build_Tool-Turbopack_%26_tsc-purple)
![Database](https://img.shields.io/badge/Database-MySQL-informational)
![Project Status](https://img.shields.io/badge/Project_Status-Production--Ready-success)
![Project Year](https://img.shields.io/badge/Project_Year-2025-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)

## Project Overview

Rasa Nusantara is a full-stack Indonesian culinary UMKM (micro, small, and medium enterprise) showcase and operational management platform built with Next.js, Express.js, Prisma ORM, and MySQL. It connects regional Indonesian food producers—ranging from Malang tempeh chips and Manado smoked roa chili paste to Bukittinggi rendang and Palembang pempek—with nationwide buyers through an interactive catalog and WhatsApp-integrated order checkout. On the operational side, the platform provides role-based dashboards for Super Administrators and UMKM Partners to manage product catalogs, track customer shipments with courier receipts, curate incoming partner applications, and configure storefront settings.

## Key Features

- **Curated Culinary Showcase & Filtering**: Public storefront supporting free-text search (product name, description, producer, city), category filtering across six culinary groups, Best Seller and discount filters, and multiple sorting modes (`popular`, `rating`, `price-asc`, `price-desc`, `newest`).
- **Interactive Product Details, Cart & Wishlist**: Persistent client-side shopping cart and wishlist backed by `localStorage`, complete with ingredient lists, halal/P-IRT certification badges, spice-level indicators, weight calculations, and per-item order notes.
- **Database-Backed WhatsApp Checkout**: Creates structured order records (`RN-YYYYMMDD-XXX`) in MySQL via `POST /api/orders`, increments product `soldCount`, and opens a pre-formatted WhatsApp order summary for direct producer communication.
- **Role-Based Admin & Partner Portals**: Separate operational scopes for `ADMIN` (full catalog, all orders, partner verification, and store settings) and `PARTNER` (scoped view of their own brand products and orders).
- **Automated Partner Onboarding Workflow**: Public UMKM registration form (`POST /api/partners`) feeds an admin curation queue where approving (`APPROVED`) a submission automatically creates the `Producer`, `PARTNER` `User` account, and inaugural catalog `Product` in MySQL.
- **Order & Shipment Tracking**: End-to-end order lifecycle management (`PENDING`, `PROCESSING`, `SHIPPED`, `COMPLETED`, `CANCELLED`) with shipping courier, tracking number persistence, and one-click WhatsApp customer updates.
- **Production-Hardened REST API**: Express backend secured with Helmet HTTP headers, origin-restricted CORS, tiered Express rate limiting, `bcryptjs` password hashing, JWT authentication, and Zod schema validation.
- **Containerized Multi-Service Setup**: Multi-stage Dockerfiles for both frontend and backend orchestrated with MySQL 8.0 via `docker-compose.yml`, including automated `prisma db push` and database seeding on container startup.

## Tech Stack

| Category | Technology | Purpose |
|---|---|---|
| Frontend Framework | Next.js (App Router) | Server/client rendering, standalone production output, and `/api` reverse-proxy rewrites |
| UI Library | React & Lucide React | Component-driven storefront and dashboard interfaces with vector iconography |
| Styling | Tailwind CSS | Responsive utility-first styling via Turbopack loader |
| Language | TypeScript | End-to-end static typing across frontend components, API clients, and backend services |
| Backend Framework | Express.js | Modular REST API routing, middleware pipeline, and global error handling |
| ORM & Database | Prisma ORM & MySQL | Relational data modeling, parameterized queries, schema sync, and comprehensive seeding |
| Validation | Zod | Request body and query parameter validation middleware |
| Authentication & Security | JWT, bcryptjs, Helmet, CORS, express-rate-limit | Bearer token auth, RBAC guards, password hashing, HTTP headers, and abuse protection |
| Containerization | Docker & Docker Compose | Isolated multi-container orchestration for MySQL, Express API, and Next.js frontend |

## Application Architecture

The application follows a containerized three-tier architecture. Browser clients interact exclusively with the Next.js frontend on port `3000`, which proxies `/api/*` and `/health` calls internally to the Express.js backend on port `5000` (eliminating cross-origin exposure in production). The Express API enforces security middlewares, validates inputs with Zod, authenticates JWT tokens for protected routes, and reads/writes relational entities in MySQL through Prisma ORM.

```mermaid
flowchart LR
    Browser["Browser Client\n(Storefront / Admin / Partner UI)"] -->|"HTTP :3000 & /api/* Rewrite"| NextJS["Next.js Frontend\n(App Router + CartContext)"]
    Browser -->|"WhatsApp Deep Link (wa.me)"| WhatsApp["WhatsApp External Hand-off"]
    NextJS -->|"Internal Proxy (INTERNAL_API_URL:5000)"| Express["Express.js REST API\n(Helmet, CORS, Rate Limit, Zod, JWT)"]
    Express -->|"Prisma Client (Prepared Queries)"| MySQL[("MySQL 8.0 Database\nrasanusantara_db")]
```

## Screenshots / Preview

### 1. Storefront Hero Section & Platform Metrics
![Storefront Hero Section](screenshots/image1.webp)
The landing page header and hero section feature a promotional announcement bar, navigation links, live catalog search, wishlist and WhatsApp order drawer triggers, and a featured regional product card. Beneath the hero call-to-action buttons, summary cards highlight catalog scale (27+ products, 16+ curated UMKM producers, 100% Halal and P-IRT curation, and customer satisfaction ratings).

### 2. Interactive Culinary Product Catalog
![Interactive Culinary Product Catalog](screenshots/image2.webp)
The catalog module provides instant keyword search, six regional culinary category filters, Best Seller and Promo toggles, and sorting options. Each product card surfaces producer origin, spice level icons, discount badges, verified certifications, a detail modal trigger, cart addition, and direct WhatsApp ordering.

### 3. UMKM Mission & Value Proposition Section
![UMKM Mission Section](screenshots/image3.webp)
The storytelling section communicates Rasa Nusantara's direct-to-producer commitment, emphasizing zero listing fee deductions, heritage recipes, Halal and P-IRT/BPOM compliance, local artisan economic impact, and direct WhatsApp buyer-producer consultation.

### 4. Role-Based Management Portal Login
![Management Portal Login](screenshots/image4.webp)
The `/login` portal allows Super Administrators and UMKM Partners to switch role presets or enter registered credentials. Submitted credentials are verified against `bcryptjs` password hashes in MySQL, returning a signed JWT token stored for authenticated dashboard operations.

### 5. Super Admin Analytics & Operations Overview
![Super Admin Analytics Overview](screenshots/image5.webp)
Upon logging in as Super Admin, the `/admin` overview tab displays live backend API connectivity alongside platform-wide KPIs: estimated revenue, incoming order count, active menu items, and registered artisans. It also surfaces recent order activity with status badges and a ranked list of top-selling products.

### 6. Order & Shipment Tracking Management (Super Admin)
![Order and Shipment Management](screenshots/image6.webp)
The incoming orders view provides search by order code, customer name, or WhatsApp number and filters by status (`PENDING`, `PROCESSING`, `SHIPPED`, `COMPLETED`, `CANCELLED`). Administrators can inspect itemized weights and shipping addresses, assign courier names and tracking numbers, or trigger WhatsApp customer notifications.

### 7. UMKM Partner Application Verification (Super Admin)
![Partner Verification Queue](screenshots/image7.webp)
Exclusive to Super Administrators, the partner verification tab lists submitted UMKM applications along with city, product category, certification details, and applicant descriptions. Approving an application automatically creates the corresponding producer profile, partner login account, and inaugural catalog product.

### 8. Platform Store & Contact Settings (Super Admin)
![Store Settings Form](screenshots/image8.webp)
The store settings tab enables Super Administrators to update platform-wide metadata including showcase name, coordinator WhatsApp number, tagline, support email, cooperative bank account, promotional announcement banner, and distribution warehouse address.

### 9. UMKM Partner Analytics Dashboard
![UMKM Partner Analytics](screenshots/image9.webp)
When authenticated with the `PARTNER` role, the dashboard automatically scopes metrics and navigation tabs to the partner's brand (such as Dapur Bu Harti), hiding Super Admin verification and global settings views while displaying store-specific revenue, orders, menu count, and best-selling items.

### 10. UMKM Partner Product Catalog Management
![Partner Product Catalog Management](screenshots/image10.webp)
Partners manage their own culinary inventory through a dedicated table featuring search and category filters, pricing and packaging units, stock readiness badges (`Siap Kirim`), and actions to create, edit, or delete products.

### 11. UMKM Partner Incoming Orders View
![Partner Incoming Orders View](screenshots/image11.webp)
The partner orders tab displays only orders containing products from the signed-in UMKM producer, enabling partners to review buyer addresses, item quantities, total shipment weights, courier tracking codes, and direct WhatsApp customer follow-ups.

## Prerequisites

- **Node.js** `20.x` or higher and **npm**
- **MySQL** `8.0` (local instance such as Laragon/MySQL Server) or **Docker** & **Docker Compose**

## Installation & Setup

### Option A: Docker Compose (Recommended)

1. Clone the repository and navigate to the project root:
   ```bash
   git clone https://github.com/weztcy/Rasa-Nusantara-Indonesian-Culinary-UMKM-Showcase-Management.git
   cd "Rasa-Nusantara-Indonesian-Culinary-UMKM-Showcase-Management"
   ```

2. Create a root `.env` file from the provided template:
   ```bash
   cp .env.example .env
   ```

3. Build and start the MySQL, Express backend, and Next.js frontend containers:
   ```bash
   docker compose up --build
   ```
   The backend entrypoint automatically waits for MySQL readiness, runs `npx prisma db push`, and seeds initial categories, users, producers, products, orders, and partner submissions.

### Option B: Local Development Setup

1. Configure and start a local MySQL database named `rasanusantara_db`, then set up backend environment variables:
   ```bash
   cd backend
   cp .env.example .env
   ```
   Update `DATABASE_URL` in `backend/.env` with your local MySQL credentials.

2. Install backend dependencies, push the Prisma schema, and run the database seeder:
   ```bash
   npm install
   npx prisma generate
   npx prisma db push
   npx tsx prisma/seed.ts
   ```

3. Install frontend dependencies in a separate terminal:
   ```bash
   cd frontend
   npm install
   ```

## Usage

After setup completes, run both services locally or access the running Docker Compose stack.

1. Start the backend development server (port `5000`):
   ```bash
   cd backend
   npm run dev
   ```

2. Start the frontend development server (port `3000`):
   ```bash
   cd frontend
   npm run dev
   ```
   Note: When running outside Docker without `INTERNAL_API_URL`, set `INTERNAL_API_URL=http://localhost:5000` in the frontend environment so Next.js rewrites proxy `/api/*` and `/health` to the local Express server.

3. Open the storefront at `http://localhost:3000`, explore the culinary catalog, add items to the cart, or navigate to `http://localhost:3000/login` to access the management portal using the seeded credentials:
   - **Super Admin**: `admin@rasanusantara.id` / `admin123`
   - **UMKM Partner (Dapur Bu Harti)**: `buharti@malang.id` / `mitra123`
   - **UMKM Partner (Rendang Uni Nel)**: `uninel@bukittinggi.id` / `mitra123`
   - **UMKM Partner (Pempek Cek Mey)**: `cekmey@palembang.id` / `mitra123`

## Environment Variables

Environment configuration is separated between the root Docker Compose stack (`.env.example`) and standalone backend execution (`backend/.env.example`).

| Variable | Description | Example |
|---|---|---|
| `DB_ROOT_PASSWORD` | MySQL root password for Docker container | `rootpassword` |
| `DB_NAME` | Target MySQL database schema name | `rasanusantara_db` |
| `DB_USER` | Application MySQL username | `umkm_user` |
| `DB_PASSWORD` | Application MySQL password | `umkm_password` |
| `DB_PORT` | Host port exposed for MySQL | `3306` |
| `DATABASE_URL` | Prisma MySQL connection URI | `mysql://root:password@localhost:3306/rasanusantara_db` |
| `PORT` | Backend Express server listening port | `5000` |
| `NODE_ENV` | Runtime mode (`development` or `production`) | `production` |
| `JWT_SECRET` | Secret key used to sign and verify JWT tokens | `your_jwt_secret_key_change_in_production` |
| `JWT_EXPIRES_IN` | Expiration duration for issued JWT tokens | `7d` |
| `CORS_ORIGIN` | Allowed frontend origin for CORS requests | `http://localhost:3000` |
| `RATE_LIMIT_WINDOW_MS` | Rate-limiting sliding window in milliseconds | `900000` |
| `RATE_LIMIT_MAX_REQUESTS` | Max requests per IP within the rate-limit window | `1000` |
| `FRONTEND_PORT` | Host port exposed for the Next.js server | `3000` |
| `INTERNAL_API_URL` | Server-side proxy target URL for Next.js rewrites | `http://backend:5000` |
| `NEXT_PUBLIC_API_URL` | Client-side API base path used by browser requests | `/api` |

```env
# Root .env example (Docker Compose)
DB_ROOT_PASSWORD=rootpassword
DB_NAME=rasanusantara_db
DB_USER=umkm_user
DB_PASSWORD=umkm_password
DB_PORT=3306

PORT=5000
NODE_ENV=production
JWT_SECRET=your_jwt_secret_key_change_in_production
JWT_EXPIRES_IN=7d
CORS_ORIGIN=http://localhost:3000
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX_REQUESTS=1000

FRONTEND_PORT=3000
INTERNAL_API_URL=http://backend:5000
NEXT_PUBLIC_API_URL=/api
```

## API Documentation

The Express.js backend serves a RESTful JSON API under `/api` alongside root service and healthcheck endpoints. Protected routes require an `Authorization: Bearer <token>` header.

| Method | Endpoint | Description | Authentication |
|---|---|---|---|
| `GET` | `/` | Service metadata and API info | Public |
| `GET` | `/health` | Server uptime and status check | Public |
| `GET` | `/api/health` | API and database health status | Public |
| `POST` | `/api/auth/login` | Authenticate user and issue JWT | Public (Rate-limited) |
| `POST` | `/api/auth/register` | Register a new user account and issue JWT | Public (Rate-limited) |
| `GET` | `/api/auth/me` | Retrieve authenticated user profile | Bearer JWT |
| `GET` | `/api/categories` | List all culinary categories and counts | Public |
| `GET` | `/api/products` | Query products (`category`, `search`, `sortBy`, `bestSeller`, `discountOnly`, `page`, `limit`) | Public |
| `GET` | `/api/products/:id` | Retrieve product details by ID or slug | Public |
| `POST` | `/api/products` | Create a new product listing | `ADMIN` or `PARTNER` |
| `PUT` | `/api/products/:id` | Update an existing product | `ADMIN` or `PARTNER` |
| `DELETE` | `/api/products/:id` | Delete a product from catalog | `ADMIN` or `PARTNER` |
| `POST` | `/api/orders` | Create a customer order (`RN-YYYYMMDD-XXX`) | Public |
| `GET` | `/api/orders` | List orders with status/search filters | `ADMIN` or `PARTNER` |
| `GET` | `/api/orders/:id` | Get single order by ID or order number | `ADMIN` or `PARTNER` |
| `PATCH` | `/api/orders/:id/status` | Update order status, courier, and tracking number | `ADMIN` or `PARTNER` |
| `DELETE` | `/api/orders/:id` | Delete an order record | `ADMIN` |
| `POST` | `/api/partners` | Submit a new UMKM partnership application | Public |
| `GET` | `/api/partners` | List partner applications (`status` filter) | `ADMIN` |
| `PATCH` | `/api/partners/:id/status` | Approve (`APPROVED`) or reject (`REJECTED`) application | `ADMIN` |
| `GET` | `/api/settings` | Retrieve storefront configuration and contact settings | Public |
| `PUT` | `/api/settings` | Update storefront configuration | `ADMIN` |

Example login request and response:

```json
// POST /api/auth/login
{
  "email": "admin@rasanusantara.id",
  "password": "admin123"
}
```

```json
{
  "success": true,
  "message": "Login berhasil",
  "data": {
    "token": "<jwt_token>",
    "user": {
      "id": "<uuid>",
      "name": "Admin Pusat RasaNusantara",
      "email": "admin@rasanusantara.id",
      "role": "ADMIN",
      "brandName": "RasaNusantara Central"
    }
  }
}
```

## API Integration

The Next.js frontend integrates with both the internal Express REST API and external WhatsApp messaging links to support storefront browsing, authenticated management, and direct buyer-artisan communication.

| API / Service | Purpose | Usage |
|---|---|---|
| Backend REST API (`/api/*`) | Data persistence and authentication | Consumed by `frontend/src/lib/api.ts` through Next.js server rewrites to `INTERNAL_API_URL` |
| Health Check Endpoint (`/health`) | Backend availability monitoring | Polled by `healthApi.check()` in `CartContext` to display live API connectivity in the dashboard |
| WhatsApp Web (`https://wa.me/...`) | Direct order hand-off & customer support | Generated dynamically on cart checkout (`OrderDrawer`), floating support button, and dashboard order notifications |

## Database Configuration

Data persistence uses **MySQL 8.0** managed through **Prisma ORM** (`backend/prisma/schema.prisma`), defining eight relational tables: `users`, `producers`, `categories`, `products`, `orders`, `order_items`, `partner_submissions`, and `store_settings`.

1. Ensure your MySQL server is running and `DATABASE_URL` in `backend/.env` points to the target schema.
2. Generate the Prisma client and synchronize the schema:
   ```bash
   cd backend
   npx prisma generate
   npx prisma db push
   ```
3. Populate initial data (6 categories, 4 user accounts, 16 producers, 37 products, 8 orders, 8 partner submissions, and default store settings):
   ```bash
   npx tsx prisma/seed.ts
   ```

## Authentication & Authorization

Authentication and authorization are enforced across both the Express API (`backend/src/middlewares/auth.ts`) and Next.js dashboard routes (`frontend/src/app/admin/page.tsx`):

- **Password Hashing**: User passwords are salted and hashed with `bcryptjs` (10 salt rounds) before persistence in MySQL.
- **JWT Session Tokens**: Successful login or registration issues a Bearer JWT signed with `ENV.JWT_SECRET` (default 7-day expiration), stored in browser `localStorage` (`umkm_auth_token`) and verified against the `users` table on each protected request.
- **Role-Based Access Control (RBAC)**: `requireRole` middleware enforces `ADMIN`, `PARTNER`, and `USER` roles. Super Admins (`ADMIN`) access all endpoints including partner verification (`GET/PATCH /api/partners`), order deletion (`DELETE /api/orders/:id`), and store settings (`PUT /api/settings`). Partners (`PARTNER`) are restricted to product management and order fulfillment, with the frontend dashboard filtering products and orders to their assigned `brandName`.
- **Route Protection & Rate Limiting**: Unauthenticated visitors to `/admin` are redirected to `/login`, while `/api/auth/login` and `/api/auth/register` apply a stricter rate limiter (`authLimiter`).

## Build & Deployment

Both services include multi-stage Alpine Dockerfiles (`backend/Dockerfile` and `frontend/Dockerfile`) producing lightweight production images. The frontend builds with Next.js `output: "standalone"` and runs as a non-root `nextjs` user, while the backend compiles TypeScript to `dist/` and runs `docker-entrypoint.sh` before starting Node.js.

1. Build and run the full production stack with Docker Compose:
   ```bash
   docker compose up --build -d
   ```
2. Verify running containers and health checks:
   ```bash
   docker compose ps
   ```
3. For manual production builds without Docker:
   ```bash
   # Build and start backend
   cd backend
   npm run build
   npm start

   # Build and start frontend
   cd ../frontend
   npm run build
   npm start
   ```

## Contributing

Contributions are welcome to improve features, fix bugs, or expand documentation. Please follow these steps:

1. Fork the repository.
2. Create a feature or fix branch (`git checkout -b feature/your-feature`).
3. Make and test your changes locally.
4. Commit and push the branch to your fork.
5. Open a pull request with a clear explanation of your changes.

## License

This project is licensed under the MIT License.
See the [LICENSE](LICENSE) file for details.

## Author & Contact

**Yohanes Dimas Pratama**

- GitHub: [github.com/weztcy](https://github.com/weztcy)
- Portfolio: [yohanesdimas.com](https://yohanesdimas.com)
- LinkedIn: [linkedin.com/in/yohanes-dimas](https://www.linkedin.com/in/yohanes-dimas)
