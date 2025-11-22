# Workshop Gallery Application Prompt

**ROLE:** Expert Full-Stack Developer (Firebase, Web Scraping, Modern UI).

**CONTEXT:**
For a Firebase Studio workshop, participants build "about pages" for their AI apps. I need a central **Gallery Application** to collect and showcase these projects in real-time.

**CORE WORKFLOW:**
1.  **Participant** scans a QR code to open the Submission Page.
2.  **Participant** enters their "About Page" URL.
3.  **App** validates and scrapes metadata from that URL.
4.  **App** saves the entry to Firestore.
5.  **Gallery** updates instantly to show the new project.

---

## 1. Submission Logic
*   **Input:** URL field (HTTPS only).
*   **Scraping:** Fetch the URL and extract specific metadata:
    *   `workshop-project` (must be "true")
    *   `project-name`
    *   `project-description`
    *   `project-author`
    *   `project-demo-url`
    *   `project-technologies`
    *   *Backup:* Parse JSON-LD if available.
*   **Validation:**
    *   Reject if `workshop-project` meta tag is missing.
    *   Reject if required fields (Name, Author, Demo URL) are empty.
    *   **Duplicate Check:** distinct on `projectDemoUrl`.
*   **Feedback:** Show loading spinner during scrape. specific error messages if validation fails (e.g., "Not a valid workshop project").

## 2. Gallery UI
*   **Layout:** Responsive Grid (Mobile: 1 col, Tablet: 2, Desktop: 3+).
*   **Cards:** Beautiful, modern cards displaying:
    *   Project Name & Author.
    *   Short description.
    *   Tech stack pills/badges.
    *   "Try Demo" and "View Code" buttons.
*   **Real-time:** Use Firestore `onSnapshot` to animate new submissions in without refreshing.
*   **Features:**
    *   Search/Filter by technology or author.
    *   Sort by Newest/Oldest.
    *   "Empty State" placeholder if no projects exist.

## 3. Project Details (Modal/View)
*   Clicking a card opens a detailed view with the full description, full metadata, and prominent links.

## 4. Admin & Utilities
*   **QR Code:** A page/section displaying a large QR code linking to the submission form (for the instructor to project).
*   **Firestore Schema:**
    *   Collection: `workshop_submissions`
    *   Fields: `aboutPageUrl`, `projectName`, `projectAuthor`, `projectDescription`, `projectDemoUrl`, `technologies`, `submittedAt` (timestamp), `status` (default 'approved').

---

## Technical Constraints
*   **Stack:** Standard Web Technologies (HTML5, CSS3, Vanilla JS) OR a lightweight framework if preferred.
*   **Firebase:** Firestore for data, Hosting for serving.
*   **Styling:** Modern, polished aesthetic. Flexible interpretation, but think "Developer Workshop" (Dark/Light mode compatible or Purple/Blue theme).
*   **CORS:** Handle cross-origin fetch issues gracefully (e.g., user instructions or proxy fallback).

## Deliverables
*   Fully functional source code.
*   `firestore.rules` configuration.
*   `README.md` with setup instructions.