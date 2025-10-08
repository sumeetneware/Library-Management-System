================= Library Management System ===================
## Problem Statement – Library Management System
No central system to track books, loans, and borrowers.
Students struggle to find books and manage loan deadlines.
Librarians track loans manually, causing errors.
Overdue books are not properly monitored.
Guardians can't view their child’s loans or overdue books.
Reports on books and loans are missing or hard to create.
User roles and permissions are unclear.
Existing library software is costly or hard to use.



## Proposed Solution – Library Management System
Build a Salesforce solution using free Developer Edition tools.
Create objects for books, loans, students, and guardians.
Track book availability and manage loans easily.
Send automated reminders for due dates and overdue books.
Add rules to avoid errors in loans and returns.
Set up roles and permissions to protect data.
Provide reports and dashboards to track loans and usage.
Design simple interfaces for easy access and navigation.






## Phase 1: Problem Understanding & Industry Analysis

1. Requirement Gathering
Talk to Stakeholders
 Library Admin → Understand how books are managed, reports required, and user roles.
 Librarians → Learn how loans, returns, and notifications are handled.
 Students → Understand how they search for books and view loans.
 Guardians → Learn how they track their child’s loans and overdue alerts.

3. Collect Requirements
Allow students to borrow books.
Track books with availability status.
Prevent issuing the same book to multiple borrowers.
Notify borrowers about due dates and overdue loans.

4. Stakeholder Analysis
Admin(System setup): Manage users, reports, permissions
Librarian(Book management): Issue and return books, track overdue loans
Student(Borrower): View loans, request books
Guardian(Support role): Monitor student loans and receive notifications

5. Business Process Mapping
Example flow:
Student searches for a book → Librarian checks availability → Loan record is created → Due date is calculated → Notification sent before due date → Book is returned  → Report updated → Alerts sent for overdue books.

6. Industry-specific Use Case Analysis
Books need tracking because they are often lost or overdue.
Students need reminders to return books.
Guardians want access to their child’s loan history.
Reports help librarians understand which books are popular or underutilized.

7. AppExchange Exploration
Popular apps in this space include:
Handy Library: A book organizer that allows for ISBN scanning and tracks loaned books with reminders. It offers a free tier for up to 100 books and a paid premium version for unlimited use.
Librarika: A free integrated library system for up to 2,000 titles, with features like member management, overdue reminders, and barcode scanner support.
Book Tracker: An app for Apple devices that helps users organize their library, track reading progress, and has a dedicated "Loaned Out" feature to keep track of books lent to friends.
GO Library: A comprehensive solution for managing a library with features like member management, shift management, and automated SMS reminders.




## Phase 2: Org Setup & Configuration

Salesforce Edition: Developer Edition (free).
1. Company Profile Setup: Library information (time zone, currency INR, locale = India).
2. Business Hours & Holidays: Library open Mon–Sat, 9 AM – 6 PM, closed on national holidays.
3. Fiscal Year Settings: Aligned with academic year (June–May).
4. User Setup & Licenses: Users → Librarian, Student, Faculty, Admin.
5. Profiles & Roles:
Librarian Profile → Full control on books.
Student Profile → Limited to own borrowed records.
Faculty Profile → Same as student but extended borrowing privileges.
Permission Sets: “Overdue Manager” permission set for special access.
6. OWD (Org-Wide Defaults):
Books → Public Read Only.
Issued Books → Private (student sees only own records).
7. Sharing Rules: Librarians can see all issued books.
8. Login Access Policies: Restrict librarian login to library computers.
9. Sandbox Usage: For testing fine automation before going live.
10. Deployment Basics: Move tested automation flows to production org.






## Phase 3: Data Modeling & Relationships

1. Objects:
Book__c → (Title, Author, ISBN, Stock).
Library_Member__c → (Name, Member Type, Contact Info).
Issued_Book__c → (Issue Date, Return Date, Fine, Status).
2. Relationships:
Book – Issued_Book → Master-Detail (Book is parent).
Library_Member – Issued_Book → Master-Detail (Member is parent).
Issued_Book acts as a junction object between Books and Members.
3. Record Types: Books classified as Textbooks, Journals, Novels.
4. Page Layouts: Different layouts for Librarian vs Student.
5. Compact Layouts: Show key fields like Book Title, Status, Due Date.
6. Schema Builder: Used to design relationships visually.








## Phase 4: Process Automation (Admin)

Validation Rules:
Return Date must be after Issue Date.
Member cannot borrow more than 5 books at once.
Workflow Rules (Legacy) → Replaced with Flows.
Approval Process: If a student requests more than 3 books, librarian approval required.
Flows:
Record-Triggered Flow: When a book is overdue, send email alert.
Scheduled Flow: Check overdue books daily and update fines.
Screen Flow: Self-service portal for students to request books.
Email Alerts & Notifications:
Send reminders 2 days before due date.
Notify librarian when stock < 2 copies.






## Phase 5: Apex Programming (Developer)

Apex Classes: FineCalculator class to compute fines.
Triggers:
Before Insert on Issued_Book__c → Check if stock is available.
After Update → Reduce stock when book issued, increase stock when returned.
SOQL/SOSL: Query books by ISBN or title.
Batch Apex: Bulk fine calculation for overdue books.
Queueable Apex: Handle book request approval asynchronously.
Scheduled Apex: Run every night → update fines.
Future Methods: Send overdue SMS asynchronously.
Exception Handling: Custom error messages for unavailable books.
Test Classes: Cover all triggers (e.g., stock update, fine logic).







## Phase 6: User Interface Development

Lightning App Builder: Create “Library Management” app.
Record Pages:
Book Page → Details + Related Issued Records.
Member Page → Borrowing history.
Tabs: Books, Members, Issued Books.
Home Page: Dashboard with “Top 5 Borrowed Books.”
Utility Bar: Quick search for books.
LWC (Lightning Web Components):
Book Search Component → Search by Title/ISBN.
Issue Book Component → Issue directly from UI.
Apex with LWC: Display book availability in real-time.









## Phase 7: Integration & External Access

Named Credentials: Secure API keys for external eBook providers.
REST Integration: Connect with digital library API to fetch eBook availability.
Platform Events: Notify librarian when stock drops below threshold.
Salesforce Connect: Link external university database for member verification.
OAuth Authentication: Allow students to log in using college credentials.








## Phase 8: Data Management & Deployment

Data Import Wizard: Import student and faculty member details
Data Loader: Bulk upload thousands of book records.
Duplicate Rules: Prevent duplicate ISBNs.
Data Export & Backup: Weekly export of books and members.
Change Sets: Move automation from sandbox to production.
VS Code & SFDX: For developer-centric deployments








## Phase 9: Reporting, Dashboards & Security Review
Reports:
Tabular → List of overdue books.
Summary → Count of books issued per student.
Matrix → Book category vs number issued.
Joined → Compare issued vs returned books.
Dashboards:
“Most Borrowed Books.”
“Books Not Returned by Due Date.”
“Top Borrowing Members.”
Security Review:
Field Level Security → Hide fine details from students.
Login IP Ranges → Restrict admin access.
Audit Trail → Track librarian’s record edits.







## Phase 10: Final Presentation & Demo Day

Pitch Presentation: Problem (manual library records) → Solution (automated Salesforce app).
Demo Walkthrough:
Student requests a book → Librarian issues → Return after due date → Fine calculated automatically.
Handoff Documentation: User guide for librarians (steps to issue, return, and generate reports).
Portfolio Showcase: Add screenshots of app, dashboards, and flows to LinkedIn.
