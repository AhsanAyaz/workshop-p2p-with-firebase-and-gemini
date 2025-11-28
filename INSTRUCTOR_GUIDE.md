# Instructor Guide: From Prompt to Production

**Duration:** ~60 Minutes
**Goal:** Guide participants to build and deploy an AI-powered web app using Firebase Studio.

## 📋 Preparation Checklist

- [ ] Ensure you have access to Firebase Studio
- [ ] Have the [Workshop Gallery App](https://audiencemeter.pro/s/T5i6U) ready to show
- [ ] Have the `PROMPTS.md` file link ready to share with participants
- [ ] Verify you have Google Cloud credits codes (if applicable)

## 🕒 Timeline Overview

| Time | Section                  | Activity                                           |
| ---- | ------------------------ | -------------------------------------------------- |
| 0:00 | **Intro & Setup**        | Welcome, credits, access check                     |
| 0:05 | **Part 1: Generation**   | Prompt engineering demo, participants generate app |
| 0:15 | **Part 2: Enhancements** | Adding features (Firestore/AI/UX)                  |
| 0:30 | **Part 3: About Page**   | Creating the portfolio page for the gallery        |
| 0:37 | **Part 4: Deployment**   | Deploying to Firebase App Hosting                  |
| 0:52 | **Part 5: Submission**   | Submitting to the live gallery                     |
| 0:57 | **Wrap Up**              | Q&A, Resources                                     |

---

## 🎤 Script & Flow

### 0:00 - Intro & Setup (5 mins)

**Say:** "Welcome! Today we're not just coding; we're architecting with AI. You're going to build a full-stack, AI-powered app and deploy it to the internet in under an hour. No local environment setup, no config hell. Just you, your idea, and Firebase Studio."

**Action:**

1.  Share the link to `PROMPTS.md`.
2.  Direct everyone to [studio.firebase.google.com](https://studio.firebase.google.com/).
3.  (Optional) Distribute credit codes.
4.  Ask everyone to open the **Chat** panel in Studio.

### 0:05 - Part 1: From Prompt to App (10 mins)

**Say:** "The most important step is the first prompt. Garbage in, garbage out. We need to give the AI a clear role, context, and constraints."

**Demo:**

1.  Show `PROMPTS.md` -> **1. Initial App Generation**.
2.  Briefly explain the structure (Context, Task, Constraints).
3.  Pick an example idea (e.g., "Smart Recipe Finder") and fill in the template live.
4.  Hit enter and watch the code generate.

**Task:**
"Now it's your turn. Go to `PROMPTS.md`, copy the template, fill in your idea (or use the Recipe Finder example), and hit enter. You have 5 minutes to get a working preview."

**Troubleshooting:**

- If generation stalls, tell them to refresh and try again.
- If the preview is blank, check the console for errors.

### 0:15 - Part 2: Enhance with Conversational Prompts (15 mins)

**Say:** "You have a base app. Now let's make it real. A real app needs to remember things (Database) and be smart (AI)."

**Action:**

1.  Direct them to `PROMPTS.md` -> **2. Feature Enhancements**.
2.  Explain the 3 options:
    - **Option A (Essential):** Add Firestore to save data.
    - **Option B:** Make the AI smarter.
    - **Option C:** Polish the UX.
3.  Recommend starting with **Option A** if they want their app to be useful.

**Task:**
"Pick one enhancement. Copy the prompt, customize it for your app, and paste it into the chat. Verify that it works in the preview."

### 0:30 - Part 3: Create Your About Page (7 mins)

**Say:** "We're building a gallery of everyone's work today. To get into the gallery, your app needs an 'About' page that our scraper can read."

**Action:**

1.  Show `PROMPTS.md` -> **3. Create About Page**.
2.  Explain that this page contains hidden metadata tags.
3.  **CRITICAL:** Remind them to fill in their names and project details in the prompt _before_ sending it.

**Task:**
"Create your About page now. Don't worry about the 'Deployment URL' placeholder yet; we'll fix that in the next step."

### 0:37 - Part 4: Deploy to Production (15 mins)

**Say:** "It works on your machine (well, in the cloud IDE). Now let's share it with the world."

**Action:**

1.  Show `PROMPTS.md` -> **4. Deployment**.
2.  Explain that this prompt tells Firebase to set up hosting, build the app, and give us a public URL.

**Task:**
"Run the deployment prompt. This will take about 5-8 minutes. While it builds, let's talk about what's happening under the hood (Next.js build, containerization, Cloud Run)."

**Once Deployed:**

1.  **Say:** "Grab that URL! Now we need to update your About page so the gallery links work."
2.  Show `PROMPTS.md` -> **5. Update About Page**.
3.  Have them run that prompt, then **6. Final Deploy** to push the change.

### 0:52 - Part 5: Submit Your Project (5 mins)

**Say:** "Your app is live. Let's put it in the Hall of Fame."

**Action:**

1.  Display the Workshop Feedback/Gallery QR Code (from `workshop-feedback.png`).
2.  Tell them to enter their `/about` URL (e.g., `https://my-app.web.app/about`).

**Task:**
"Scan the code, submit your URL. Watch the screen to see your app appear!"

### 0:57 - Wrap Up

**Say:** "You just built and deployed a full-stack AI app in an hour. This is the future of development. Go forth and build!"

**Resources:**

- Share links to Firebase docs, Genkit docs, and the repo.
