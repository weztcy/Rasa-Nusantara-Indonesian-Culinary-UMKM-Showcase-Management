# Portfolio Project Data — Rasa Nusantara - Indonesian Culinary UMKM Showcase & Management

- **Category:** `web-development` (`Web Development`)
- **Accent Color:** `cyan`
- **Target Assets Folder:** `public/images/projects/rasa_nusantara_indonesian_culinary/`
- **Required Local Images:** `banner.webp`, `image01.webp` .. `image11.webp`

## TypeScript Data (`ProjectCaseStudy`)

```typescript
{
  "id": "rasa-nusantara-indonesian-culinary-umkm-showcase-management",
  "code": "PRO-56 // WEB-08",
  "title": "Rasa Nusantara - Indonesian Culinary UMKM Showcase & Management",
  "category": "web-development",
  "categoryLabel": "Website",
  "year": "2025",
  "status": "Completed",
  "accentColor": "cyan",
  "repoUrl": "https://github.com/weztcy/Rasa-Nusantara-Indonesian-Culinary-UMKM-Showcase-Management",
  "license": "MIT License",
  "banner": "/images/projects/rasa_nusantara_indonesian_culinary/banner.webp",
  "summary": "Full-stack Indonesian culinary UMKM showcase and management platform with Next.js, Express, Prisma, MySQL, RBAC, and WhatsApp checkout.",
  "projectDescription": "Rasa Nusantara is a full-stack Indonesian culinary UMKM showcase and management platform connecting local food artisans with buyers. Built with Next.js, Express, Prisma, and MySQL, it supports catalog filtering, WhatsApp checkout, and role-based admin and partner portals.",
  "architectureSummary": "Next.js App Router storefront proxies requests to an Express TypeScript REST API backed by Prisma ORM and MySQL.",
  "techStack": [
    "Next.js",
    "React",
    "TypeScript",
    "Tailwind CSS",
    "Express.js",
    "Prisma",
    "MySQL",
    "Zod",
    "JWT",
    "bcryptjs",
    "Helmet",
    "Docker",
    "Lucide React"
  ],
  "telemetryMatrix": {
    "projectType": "Full-Stack Web Platform",
    "targetPlatform": "Web Browser & Docker Containers",
    "primaryDomain": "Culinary UMKM E-Commerce & Ops",
    "architecturePipeline": "Next.js -> Express API -> Prisma -> MySQL",
    "testingAndAudit": "Passed",
    "projectStatus": "Completed",
    "projectYear": "2025"
  },
  "projectInfo": {
    "projectType": "Full-Stack Web Application",
    "developmentStatus": "Completed",
    "developmentYear": "2025",
    "platform": "Web & Docker Compose",
    "projectCategory": "Web Development"
  },
  "projectBackground": "Regional Indonesian culinary MSMEs often lack centralized digital storefronts and structured order tracking, relying on fragmented manual chats. Rasa Nusantara bridges this gap by combining a halal-curated product showcase with a persistent MySQL order, partner, and catalog operations portal.",
  "problemStatements": [
    {
      "title": "Fragmented Regional UMKM Visibility",
      "description": "Local food artisans across Indonesian regions struggle to showcase certified products, origin stories, and packaging details in a unified digital marketplace.",
      "issueCode": "ISSUE_01"
    },
    {
      "title": "Unstructured Manual Chat Ordering",
      "description": "Direct WhatsApp transactions without centralized database logging lead to lost order histories, manual weight calculations, and inconsistent courier tracking.",
      "issueCode": "ISSUE_02"
    },
    {
      "title": "Manual Partner Onboarding Bottlenecks",
      "description": "Verifying halal or P-IRT certifications and provisioning store accounts and initial catalog listings for newly approved MSMEs requires excessive manual administration.",
      "issueCode": "ISSUE_03"
    }
  ],
  "projectObjectives": [
    {
      "title": "Unified Curated Culinary Storefront",
      "description": "Deliver a searchable, filterable storefront showcasing regional MSME products with halal/P-IRT badges, spice levels, and producer stories.",
      "targetTag": "TARGET_01"
    },
    {
      "title": "Persistent WhatsApp-Integrated Checkout",
      "description": "Record structured customer orders with calculated totals and parcel weights in MySQL prior to launching pre-formatted WhatsApp messages.",
      "targetTag": "TARGET_02"
    },
    {
      "title": "Role-Scoped Operations & Auto-Provisioning",
      "description": "Provide separate Super Admin and UMKM Partner dashboards while automating producer, user account, and first product creation upon approval.",
      "targetTag": "TARGET_03"
    }
  ],
  "coreFeatures": [
    {
      "title": "Multi-Criteria Culinary Catalog",
      "description": "Supports free-text search across product names, descriptions, producers, and cities, alongside category tabs, best-seller and discount toggles, and sorting.",
      "badge": "Storefront"
    },
    {
      "title": "Cart, Wishlist & WhatsApp Checkout",
      "description": "Persists shopping cart and wishlist items in browser storage, computes total order weight in grams, creates RN-prefixed orders in MySQL, and opens WhatsApp.",
      "badge": "Commerce"
    },
    {
      "title": "Role-Based Admin & Partner Dashboards",
      "description": "Separates Super Admin national oversight from brand-scoped UMKM Partner views for product CRUD operations and order fulfillment.",
      "badge": "RBAC Portal"
    },
    {
      "title": "Automated UMKM Partner Curation",
      "description": "Approving a pending partner submission automatically provisions a Producer record, a PARTNER User account, and an inaugural catalog Product.",
      "badge": "Automation"
    },
    {
      "title": "Shipment & Courier Tracking Workflow",
      "description": "Tracks orders across PENDING, PROCESSING, SHIPPED, COMPLETED, and CANCELLED states with courier assignment, tracking numbers, and WhatsApp alerts.",
      "badge": "Fulfillment"
    }
  ],
  "interfaceShowcase": [
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image01.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image02.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image03.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image04.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image05.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image06.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image07.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image08.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image09.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image10.webp"
    },
    {
      "imageUrl": "/images/projects/rasa_nusantara_indonesian_culinary/image11.webp"
    }
  ],
  "userFlow": {
    "summary": "Shoppers browse curated regional categories, filter items, manage a local cart or wishlist, and submit orders that persist in MySQL while launching formatted WhatsApp messages. Meanwhile, partners and administrators authenticate via JWT to fulfill orders, update tracking, and curate new MSMEs.",
    "steps": [
      {
        "step": "01",
        "title": "Catalog Discovery & Filtering",
        "description": "Visitors browse the storefront, search by food name or city, filter across six regional categories, and inspect product certifications and spice levels.",
        "actorOrNode": "Buyer / Next.js Storefront"
      },
      {
        "step": "02",
        "title": "Cart Checkout & Order Persistence",
        "description": "Buyers enter shipping details in the Order Drawer; the frontend submits POST /api/orders to persist totals and weights before opening WhatsApp.",
        "actorOrNode": "OrderDrawer / Express API"
      },
      {
        "step": "03",
        "title": "JWT Portal Authentication",
        "description": "Super Admins and UMKM Partners log in at /login, receiving a 7-day Bearer JWT verified against bcryptjs hashes in MySQL.",
        "actorOrNode": "Admin or Partner / Auth API"
      },
      {
        "step": "04",
        "title": "Fulfillment & Partner Onboarding",
        "description": "Authenticated users update order statuses and courier tracking numbers, while Super Admins approve partner submissions to publish new MSMEs.",
        "actorOrNode": "Dashboard / Prisma ORM"
      }
    ]
  },
  "systemArchitecture": {
    "summary": "A containerized three-tier architecture pairs a Next.js App Router frontend with an Express TypeScript REST API and MySQL database via Prisma ORM. Next.js rewrites proxy browser requests to the backend service over an isolated Docker bridge network with Helmet, CORS, rate limiting, and Zod validation.",
    "layers": [
      {
        "name": "Presentation & Proxy Layer",
        "role": "Renders storefront and RBAC dashboards while proxying /api/* and /health requests internally to the backend container.",
        "components": [
          "Next.js App Router",
          "CartContext",
          "Next.js Rewrites"
        ]
      },
      {
        "name": "API & Security Middleware Layer",
        "role": "Handles HTTP security headers, origin-checked CORS, general and auth rate limits, Zod input validation, and JWT authentication.",
        "components": [
          "Express.js",
          "Helmet & CORS",
          "Zod Validators",
          "JWT & RBAC Middleware"
        ]
      },
      {
        "name": "Business Logic & Data Access Layer",
        "role": "Executes catalog filtering, order total calculation, partner auto-provisioning, and parameterized database queries.",
        "components": [
          "Express Controllers",
          "Prisma Client",
          "Seed Script"
        ]
      },
      {
        "name": "Persistence & Container Layer",
        "role": "Stores relational domain entities in MySQL 8.0 with persistent Docker volumes and automated entrypoint schema initialization.",
        "components": [
          "MySQL",
          "Docker Compose",
          "docker-entrypoint.sh"
        ]
      }
    ]
  },
  "databaseDataFlow": {
    "type": "Database Schema / ERD",
    "summary": "Normalized MySQL relational schema managed via Prisma ORM with eight tables linking users, producer profiles, culinary categories, products, multi-item orders, partner submissions, and global storefront settings.",
    "entitiesOrPipelines": [
      {
        "name": "users",
        "type": "Table",
        "fields": [
          "id",
          "email",
          "password",
          "name",
          "role",
          "phone",
          "brandName"
        ]
      },
      {
        "name": "producers",
        "type": "Table",
        "fields": [
          "id",
          "name",
          "owner",
          "city",
          "province",
          "waNumber",
          "establishedYear",
          "userId"
        ]
      },
      {
        "name": "categories",
        "type": "Table",
        "fields": [
          "id",
          "name",
          "icon",
          "description"
        ]
      },
      {
        "name": "products",
        "type": "Table",
        "fields": [
          "id",
          "name",
          "slug",
          "categoryId",
          "price",
          "weightGram",
          "spicyLevel",
          "producerId",
          "stockStatus"
        ]
      },
      {
        "name": "orders",
        "type": "Table",
        "fields": [
          "id",
          "orderNumber",
          "customerName",
          "customerPhone",
          "totalPrice",
          "totalWeightGram",
          "status",
          "shippingCourier",
          "trackingNumber"
        ]
      },
      {
        "name": "order_items",
        "type": "Table",
        "fields": [
          "id",
          "orderId",
          "productId",
          "quantity",
          "priceAtPurchase",
          "note"
        ]
      },
      {
        "name": "partner_submissions",
        "type": "Table",
        "fields": [
          "id",
          "brandName",
          "ownerName",
          "city",
          "waNumber",
          "category",
          "certification",
          "status"
        ]
      },
      {
        "name": "store_settings",
        "type": "Table",
        "fields": [
          "id",
          "storeName",
          "tagline",
          "primaryPhone",
          "email",
          "bankAccount",
          "announcement"
        ]
      }
    ]
  },
  "technicalImplementation": [
    {
      "category": "Security & Auth",
      "title": "Defense-in-Depth Middleware & RBAC Guards",
      "description": "Combines Helmet headers, CORS origin validation, tiered general and login rate limiters, 10-round bcryptjs hashing, and JWT Bearer verification via authenticate and requireRole middlewares.",
      "badge": "RBAC Security"
    },
    {
      "category": "Validation",
      "title": "Zod Request & Query Schema Enforcement",
      "description": "Validates incoming JSON payloads and query parameters against strict Zod schemas prior to controller execution, returning structured 400 field-level errors on malformed requests.",
      "badge": "Zod Schemas"
    },
    {
      "category": "Workflow Automation",
      "title": "Atomic Partner Approval Provisioning",
      "description": "Updating a partner submission to APPROVED in partner.controller.ts automatically creates the Producer profile, hashes a default PARTNER user account, and publishes an inaugural catalog Product.",
      "badge": "Auto-Provision"
    },
    {
      "category": "Infrastructure",
      "title": "Internal Next.js API Rewrites & Docker Healthchecks",
      "description": "Configures next.config.ts standalone output to proxy /api/* and /health to INTERNAL_API_URL while docker-entrypoint.sh waits for MySQL health, pushes Prisma schema, and seeds 37 initial products.",
      "badge": "Dockerized"
    }
  ],
  "primaryTechSpecs": {
    "programmingLanguage": "TypeScript",
    "framework": "Next.js & Express.js",
    "database": "MySQL"
  },
  "architectureQuality": {
    "badges": [
      "Role Based Access",
      "Type Safe Validation",
      "Multi Stage Docker",
      "Parameterized ORM Queries"
    ]
  }
}
```
