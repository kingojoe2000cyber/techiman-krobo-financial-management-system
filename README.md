# Techiman Krobo NMTC Financial Management System — MVP

A GitHub Pages-ready financial management dashboard for a public nursing and midwifery training college.

## Core MVP modules

- Executive financial dashboard
- Receipts and payments cashbook
- Payment voucher and payment reconciliation register
- Bank reconciliation statement and clearance tracking
- Payroll management
- Configurable employee/employer SSNIT calculations
- PAYE, withholding tax and social security remittance tracking
- Budget and commitment control
- Management financial snapshot
- CSV exports and JSON backup/restore

## Important security note

This MVP uses browser `localStorage` so it can run as a static GitHub Pages application. It is for demonstration, workflow design and testing only. Do **not** store live payroll, bank account, tax, staff or student personal data in this version.

A production version should add a secure backend database, authenticated users, role-based access, audit logs, encrypted secrets, server-side validation, backups and approved hosting.

## Run locally

Open `index.html` directly in a browser, or run a simple local web server.

## GitHub Pages deployment

1. Create a new GitHub repository, recommended name: `techiman-krobo-financial-management-system`
2. Push all project files to the `main` branch.
3. Go to **Settings → Pages → Build and deployment** and select **GitHub Actions**.
4. The included workflow `.github/workflows/deploy-pages.yml` will deploy the site.

Expected URL format:

`https://YOUR-USERNAME.github.io/techiman-krobo-financial-management-system/`

## Suggested production upgrade (Version 2)

- FastAPI or Django backend
- PostgreSQL database
- Multi-user login and RBAC
- Maker/checker/approver workflow
- Immutable audit trail
- Supplier and commitment ledgers
- Asset and inventory registers
- Payroll import and approval workflow
- GRA/SSNIT statutory schedules
- Bank statement CSV import and automated matching
- API integration with ERP/banking platforms where permitted
- Encrypted document/evidence storage
