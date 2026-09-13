# Student Debtors 360 — live web module

This module moves the student-debtors workflow from Excel into a multi-user web application. GitHub Pages hosts the frontend; Supabase provides Authentication and PostgreSQL. Individual staff accounts use email/password login, roles are stored in `profiles`, and database Row Level Security limits write/review/admin operations.

## Capacity and matching

Payment CSVs are streamed in chunks of 1,500 records from the browser, then unresolved payments are matched server-side in batches of 5,000. The database is not limited to the 500,000-row Excel design. The matching engine uses normalized index numbers, exact names and PostgreSQL `pg_trgm` similarity. Scores >= 0.92 auto-post; 0.75–0.9199 goes to review; lower-confidence records become unidentified.

## Modules

- Executive debtors dashboard
- Student master / opening debtor upload
- Large payment upload with batch ID
- Automated similarity matching
- Review queue
- Overpaid list
- Unpaid list
- Unidentified payments
- Editable revenue-line master
- Individual staff login
- Staff role control
- Staff last-seen monitoring
- Batch and record audit trail

## Roles

`admin`, `finance_manager`, `data_entry`, `reviewer`, `viewer`.

## Deployment

1. Create a Supabase project.
2. Run `supabase_schema.sql` in the Supabase SQL Editor.
3. Create staff accounts in Supabase Authentication. The application creates a `viewer` profile; an administrator/finance manager can then assign `staff_code`, `full_name` and role in `profiles`.
4. Copy `config.example.js` to `config.js` and set the Supabase project URL and browser-safe publishable/anon key. Never use a `service_role` key in the browser.
5. Enable GitHub Pages using the repository's existing Actions workflow.
6. Open: `https://kingojoe2000cyber.github.io/techiman-krobo-financial-management-system/student-debtors/`

## CSV templates

Students: `index_number,student_name,opening_balance,programme,level,cohort,revenue_line_code`

Payments: `payment_date,payer_name,index_number,amount,bank_reference,revenue_line_code`

## Important production note

Do not store live student records, passwords or service-role secrets in GitHub. GitHub Pages is only the frontend. The Supabase database and RLS are the security boundary. Before operational go-live, configure backups, MFA if required by the institution, approved data-retention rules, and a formal maker/checker/approver policy.