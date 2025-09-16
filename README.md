=============================================== Library Management System =================================================
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

2. Collect Requirements
Allow students to borrow books.
Track books with availability status.
Prevent issuing the same book to multiple borrowers.
Notify borrowers about due dates and overdue loans.

3. Stakeholder Analysis
Admin(System setup): Manage users, reports, permissions
Librarian(Book management): Issue and return books, track overdue loans
Student(Borrower): View loans, request books
Guardian(Support role): Monitor student loans and receive notifications

4. Business Process Mapping
Example flow:
Student searches for a book → Librarian checks availability → Loan record is created → Due date is calculated → Notification sent before due date → Book is returned  → Report updated → Alerts sent for overdue books.

5. Industry-specific Use Case Analysis
Books need tracking because they are often lost or overdue.
Students need reminders to return books.
Guardians want access to their child’s loan history.
Reports help librarians understand which books are popular or underutilized.

6. AppExchange Exploration
Popular apps in this space include:
Handy Library: A book organizer that allows for ISBN scanning and tracks loaned books with reminders. It offers a free tier for up to 100 books and a paid premium version for unlimited use.
Librarika: A free integrated library system for up to 2,000 titles, with features like member management, overdue reminders, and barcode scanner support.
Book Tracker: An app for Apple devices that helps users organize their library, track reading progress, and has a dedicated "Loaned Out" feature to keep track of books lent to friends.
GO Library: A comprehensive solution for managing a library with features like member management, shift management, and automated SMS reminders.


