# Web GUI Desktop-Parity Handoff

## Purpose

Build the browser interface as a modern, responsive version of the existing desktop application. The desktop application is the functional source of truth. Do not remove a module, field, action, validation, permission, report, receipt, or export option because it is not visible in the first viewport.

The browser interface and desktop interface must use the same API, PostgreSQL database, authentication, permissions, business rules, receipts, reports, backups, and audit history. Neither interface should access PostgreSQL directly.

## Reference Screenshots

The complete capture set is in `../backup/ui_review_20260911/modules/`.

- Contact sheet: `../backup/ui_review_20260911/module_contact_sheet.png`
- Dashboard: `../backup/ui_review_20260911/modules/dashboard.png`
- Students: `../backup/ui_review_20260911/modules/students.png`
- Fees: `../backup/ui_review_20260911/modules/fees.png`
- Late fees: `../backup/ui_review_20260911/modules/late_fees_list.png`
- Staff and salaries: `../backup/ui_review_20260911/modules/staff.png`
- Expenses: `../backup/ui_review_20260911/modules/expenses.png`
- Donations: `../backup/ui_review_20260911/modules/donations.png`
- ID cards: `../backup/ui_review_20260911/modules/id_cards.png`
- Financial analytics: `../backup/ui_review_20260911/modules/financial_analytics.png`
- Alerts: `../backup/ui_review_20260911/modules/alerts.png`
- Automation: `../backup/ui_review_20260911/modules/automation.png`
- Reports: `../backup/ui_review_20260911/modules/reports.png`
- Activity logs: `../backup/ui_review_20260911/modules/activity_logs.png`
- Settings: `../backup/ui_review_20260911/modules/settings.png`
- Backup: `../backup/ui_review_20260911/modules/backup.png`
- Historical records: `../backup/ui_review_20260911/modules/historical_records.png`
- Exams and results: `../backup/ui_review_20260911/modules/exams_results.png`
- Timetable: `../backup/ui_review_20260911/modules/timetable.png`
- Transport: `../backup/ui_review_20260911/modules/transport.png`
- Monthly fee and salary status: `../backup/ui_review_20260911/modules/monthly_fee_salary_status.png`
- Trash bin: `../backup/ui_review_20260911/modules/trash_bin.png`
- Dynamic information: `../backup/ui_review_20260911/modules/dynamic_information.png`
- Developer information: `../backup/ui_review_20260911/modules/developer_info.png`

## Application Shell

Keep these global elements available on desktop and mobile layouts:

- School branding area with logo, school name, tagline, current user, breadcrumb, and active session.
- Live date and time clock.
- Global search with suggestions across students, staff, phone numbers, receipts, and IDs.
- Undo action.
- Alerts count, database alerts count, and worker/background activity status.
- Current-user menu, Logout, Exit, Refresh, Graph, and Palette/theme controls.
- Main navigation with permission-based visibility.
- Toasts, validation messages, confirmation dialogs, loading states, and error states.
- Persistent status bar with CPU, RAM, database size, thread/task information, and developer footer.

The current master account is `developer`. The password is supplied separately and must not be hard-coded into frontend source, screenshots, or documentation.

## Main Navigation

The current configured navigation order is:

1. Dashboard
2. Dynamic Information
3. Students
4. Family Management
5. Exams & Results
6. Timetable
7. ID Cards
8. Fees
9. Late Fees List
10. Monthly Fee & Salary Status Tracker
11. Staff
12. Expenses
13. Donations
14. Transport
15. Financial Analytics
16. Alerts
17. Automation
18. Reports
19. Activity Logs
20. Developer Info
21. Trash Bin
22. Settings
23. Backup
24. Historical Records

Family Management is part of the configured module system even if it is not visible in the captured navigation row for the current window width. It must still be implemented and permission-controlled.

## Module Requirements

### Dashboard

Reference: `modules/dashboard.png`

- Show school logo, school name, tagline, and current user.
- KPI cards: total students, total staff, total vehicles, remaining transport capacity, current-month fees collected, donations received, POS fees received, pending fees, salaries paid, expenses, net balance/profit, expected fees, received fees, pending fees, and late-fee count.
- Show monthly collection graph, calendar/date selection, daily summary, staff breakdown, alert rows, and system health monitor.
- Refresh data automatically after mutations and on demand.
- Theme/palette switching must affect the complete application, not just the dashboard.

### Dynamic Information

Reference: `modules/dynamic_information.png`

- Provide entity switching for operational records such as students, staff, expenses, donations, and fee/payment data.
- Provide search, paginated results, selectable rows, detail panel, photo preview where applicable, raw field detail, and record history.
- Keep this as a fast inspection workspace; record changes continue through the appropriate domain module.

### Students

Reference: `modules/students.png`

- Provide class settings and class list before or alongside the student list.
- Class actions: add class, edit class, delete class, open class, show class students, and rebuild class statistics.
- Student table actions: add, edit, delete/archive, select all, clear selection, bulk actions, view history, export CSV, and export PDF.
- Student form fields include roll number, admission number, name, father/mother name, date of birth, gender, blood group, nationality, religion, guardian and phone contacts, CNIC, email, address, photo, class/section, session, tuition fee, stationery fee, miscellaneous fee, transport fee, discount, admission date, previous school, enrollment status, medical information, transport route, remarks, family assignment, and custom fields.
- Auto-format dates, generate roll/admission numbers, suggest existing classes/sections, apply class fee defaults, and support “guardian contact same as contact”.
- Table features: search, class/status filters, sorting, pagination, horizontal scrolling, bulk selection, and protected edit/delete behavior.
- Lifecycle actions: promote to next class, mark alumni, add discipline/behavior log, generate transfer certificate, and view historical versions.
- Import students from Excel and preserve validation/duplicate checks.

### Family Management

Reference: no visible capture in the current navigation row; the module is configured in the application.

- Add/edit families, archive/unarchive families, filter/search families, show family members, show payment history, and show family-level fee balances.
- Generate and print family receipts and export family reports as PDF/CSV.

### Exams & Results

Reference: `modules/exams_results.png`

Use internal sections/tabs:

- Exam Manager: create exam sessions, choose exam type and dates, assign classes, configure subjects, set total marks, update subjects, delete subjects, and delete sessions.
- Fast Marks Entry: search students, edit subject/attendance/remarks cells, save selected row, save all rows, and finalize an exam.
- Result Cards: filter students, preview result cards, print/download one card, and bulk-print a class.
- Result Templates: import, open, activate, delete, and open the template folder.
- Export result CSV/PDF, print result cards, generate result cards, tabulation sheets, positions, final aggregates, and class reports.

### Timetable

Reference: `modules/timetable.png`

- Show class list, subject list, weekly timetable grid, teacher matrix, and teacher weekly view.
- Add/edit/delete timetable entries, configure subjects, configure day periods, copy one day to other days, detect conflicts, auto-generate timetable, and export/print class, teacher, and master timetable views as CSV/PDF.

### ID Cards

Reference: `modules/id_cards.png`

- Student/staff selector and populated identity fields.
- Fixed card canvas using the configured physical size and aspect ratio, not a receipt layout.
- Render the configured PNG/HTML template, logo, photo, school fields, student/staff fields, signature, QR, and barcode placeholders at their saved coordinates.
- Support template selection, placeholder mapping, visibility settings, per-field font size and style, rotation of zero degrees by default, QR/barcode content settings, print preview, print, PNG export, and PDF export.
- Preserve the exact template dimensions and prevent text from escaping its placeholder box.

### Fees

Reference: `modules/fees.png`

- Add/edit fee payment records with searchable student autocomplete.
- Selecting a student must populate class, family, fee components, outstanding balance, and related payment context.
- Fields/actions include payment month, payment date, amount paid, late fee, remaining balance, payment method, received by, family payment mode, late-fee toggle, and remarks.
- Include tuition, stationery/books, lab/miscellaneous, transport/bus, discount, and late-fee components in totals, receipts, reports, and balance calculations.
- Table actions: filter, reset, sort, page navigation, add, edit, delete/archive, select multiple, bulk actions, view history, refresh, export CSV/PDF, generate receipt, print receipt, duplicate receipt copy, send/resend reminder, and owner update logging.
- Highlight overdue, partial, paid, and locked records.

### Late Fees List

Reference: `modules/late_fees_list.png`

- Filter by month, class, and overdue-day range.
- Show late/defaulter rows, select rows, generate one notice or all notices, print notices, and print the late-fee table.

### Monthly Fee & Salary Status Tracker

Reference: `modules/monthly_fee_salary_status.png`

- Search students/staff with instant suggestions.
- Switch tracking mode, choose year/month, inspect paid and unpaid months, open paid details and unpaid details, reload the selected entity, and export the status report.

### Staff

Reference: `modules/staff.png`

- Staff table: add, edit, delete/archive, search, filter, sort, page navigation, bulk selection/actions, view staff history, and export.
- Staff form fields include staff ID, name, role, salary, CNIC, phone, email, address, joining date, photo, subjects/classes for teachers, and custom fields.
- Salary section: searchable staff selection, month, base salary, salary paid, advance, deductions, payment date, paid by, status, edit/delete, reversal, salary history, receipt PDF/print, duplicate receipt, and salary CSV/PDF export.
- Tracking actions: leave entry, performance note, salary timeline, advance ledger, and history.

### Expenses

Reference: `modules/expenses.png`

- Fields: title/description, category, amount, date, payment method, approved by, and notes.
- Filter by month, category, and title; sort and paginate the table.
- Add/edit/delete/archive, multi-select, bulk actions, view history, generate/print expense receipt, export CSV/PDF, and refresh.

### Donations

Reference: `modules/donations.png`

- Fields: donor name, amount, purpose, date, payment method, received by, status, and remarks.
- Filter, sort, paginate, select multiple, add/edit/delete/archive, bulk actions, history, donation receipt PDF/print, duplicate receipt, and CSV/PDF export.

### Transport

Reference: `modules/transport.png`

- Separate vehicle, route, and student-assignment panels.
- Add/edit/delete vehicles and routes, assign/remove students, show vehicle and route capacity/usage, show capacity report, and run route optimization.
- Respect campus, role, session, and transport-fee settings.

### Financial Analytics

Reference: `modules/financial_analytics.png`

- Date/month/year filters and date-range filtering.
- Show total fees, other income/donations, salaries, expenses, earnings, expenses, and net profit/loss.
- Green profit and red loss indicators.
- Monthly income/expense bar chart, expense category pie chart, monthly summary, yearly summary, export PDF, and print.

### Alerts

Reference: `modules/alerts.png`

- Show automated alerts for unpaid fees, pending salaries, unusual expenses, and missing backups.
- Filter and refresh alerts; export CSV/PDF.

### Automation

Reference: `modules/automation.png`

- Rule table with enabled/disabled state.
- Rule builder with conditions such as unpaid-fee days, absence count, salary state, or record creation.
- Actions such as mark defaulter, generate receipt, show alert, or create notice.
- Add, edit, delete, enable/disable, refresh, and run rules immediately.

### Reports

Reference: `modules/reports.png`

- Report type selector with student list, fees, salaries, expenses, defaulters, profit/loss, class-wise income, teacher-wise salary, expense trends, top defaulters, highest-paying students, staff performance, and student progress reports.
- Filters for class, month, staff, category, and date range.
- Generate, reset, paginate, view chart, export CSV/PDF, and print.

### Activity Logs

Reference: `modules/activity_logs.png`

- Log columns include username, action, module, record/entity, timestamp, system/session information, severity, and details.
- Filter by date, user, module, and search text; reset, inspect details, and clear logs when permitted.

### Developer Info

Reference: `modules/developer_info.png`

- Read-only developer/application information, build/version information, support/contact information, and system identity details.

### Trash Bin

Reference: `modules/trash_bin.png`

- Show archived/deleted records with module, record ID, deleted by, deleted date, and original data context.
- View selected record and restore selected record. Restore must respect audit mode and permissions.

### Settings

Reference: `modules/settings.png`

Settings is the administrative control center and must be permission-gated. Use compact section navigation rather than forcing the administrator to scroll through every section at once.

Required sections:

- School Info: school name, address, phone numbers, email, logo, receipt/report branding, and contact details.
- System Preferences: theme, audit mode, date/time behavior, and application preferences.
- Developer Info and branding.
- Fee Settings and default class fees.
- POS Fee settings and POS fee withdrawal history.
- Academic Session Management: create, switch, and close sessions.
- Receipt Settings: footer per receipt type, receipt serial behavior, stamp overlay, logo, and print settings.
- ID Card Settings: template, card dimensions, background, logo, signature PNG, placeholder editor, field visibility, groupings, font family, per-placeholder font size in points, positions, QR fields, barcode fields, and instruction text.
- Timetable Templates.
- WhatsApp/email API settings, sender configuration, owner fee notifications, reminder template, do-not-disturb option, and reminder log settings.
- Database/network settings: runtime mode, API URL, server host/port, and timeout.
- Backup Settings and Backup & Migration.
- Card Authentication: enroll, revoke, delete, and inspect card bindings.
- Custom Fields Builder: field type, module assignment, options, add/edit/delete.
- User Permissions: add user, edit user/password, choose allowed tabs/settings sections, activate/deactivate, and delete user.
- UI settings, startup screen, edition control, and shortcuts.

### Backup

Reference: `modules/backup.png`

- Configure backup directory.
- Create manual backup, run daily backup, restore backup, create full system backup, restore full system backup, verify backup bundle, export portable bundle, and show backup history/logs.
- Display progress and errors without freezing the rest of the application.

### Historical Records

Reference: `modules/historical_records.png`

- Browse historical/archived period records, select a record, inspect details, and use available historical recovery/export actions.

## Interaction and Data Rules

- Use server-side pagination and filtering for large datasets.
- Every table needs vertical and horizontal scrolling, sortable columns, empty states, loading states, and error states.
- Every destructive action requires confirmation. Audit mode changes delete into archive and stores previous values for history.
- Old/locked months and protected receipts cannot be edited or deleted.
- Duplicate checks must cover CNIC, phone, email, roll number, and other configured identity keys.
- All mutations must refresh related KPIs, tables, reports, receipts, logs, notifications, and portal data without a manual browser refresh.
- Preserve PostgreSQL data and existing business calculations. Do not replace real records with frontend demo data.
- Use the API response schema and permission responses already provided by the backend. Add an endpoint when a required screen action has no backend route; do not silently remove the action.

## Portal and Future Extensibility

Keep the same API boundary so student/parent portals and future attendance modules can be added without redesigning the data layer. Future attendance may use QR, image verification, NFC, or another device integration, but the web UI should receive those events through authenticated API endpoints and shared audit logging.

## Acceptance Checklist

- Login/logout and permission-based navigation work for master and restricted users.
- Dashboard values match PostgreSQL records.
- Add/edit/archive/restore actions work in each CRUD module.
- Search, filters, sorting, pagination, bulk actions, and history work.
- Receipts, reports, charts, CSV/PDF export, and print actions use real records.
- Settings changes immediately affect branding, templates, permissions, and calculations.
- Backup/restore and trash recovery are tested without data loss.
- Desktop and web views show the same newly created student, payment, salary, expense, donation, exam, transport, and ID-card records.
- Test with large datasets and verify that table rendering remains paginated and responsive.
