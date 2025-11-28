# Workshop Prompts

Copy and paste these prompts into Firebase Studio when instructed by the workshop lead.

## 1. Initial App Generation

**Template:**

```markdown
You are an expert full-stack developer specializing in modern web applications with AI integration.

CONTEXT:
I want to build a web application called "[YOUR APP NAME]" that helps users [PRIMARY PURPOSE]. The target users are [TARGET AUDIENCE].

TASK:
Create a complete, production-ready web application with the following features:

CORE FEATURES:

1. [Feature 1 - be specific]
2. [Feature 2 - be specific]
3. [Feature 3 - be specific]
4. AI-powered [specific AI functionality using Genkit]
5. Data persistence using Firestore

UI REQUIREMENTS:

- Clean, modern interface with responsive design
- Mobile-friendly layout
- Intuitive navigation
- Professional color scheme ([mention preferences if any])

TECHNICAL REQUIREMENTS:

- Use Firebase Genkit for AI features
- Use Firestore for database
- Include proper error handling
- Add loading states for AI operations
- Make it accessible (ARIA labels, semantic HTML)

CONSTRAINTS:

- Keep the code clean and well-commented
- Use vanilla JavaScript (or specify framework if preferred)
- Ensure the app works offline where possible
- Optimize for performance

OUTPUT:
Provide the complete application structure with:

- Next.js project structure (App Router)
- app/page.tsx (main page)
- components/ (reusable UI components)
- lib/ (firebase config, genkit flows)
- app/globals.css (Tailwind CSS styling)
- Clear comments explaining key sections
```

**Example (Smart Recipe Finder):**

```markdown
You are an expert full-stack developer specializing in modern web applications with AI integration.

CONTEXT:
I want to build a web application called "Smart Recipe Finder" that helps users discover recipes based on ingredients they already have. The target users are home cooks who want to reduce food waste and get creative with available ingredients.

TASK:
Create a complete, production-ready web application with the following features:

CORE FEATURES:

1. Input field where users can enter available ingredients (comma-separated)
2. AI-powered recipe suggestion engine using Genkit that generates 3-5 recipe options
3. Each recipe should include: name, ingredients list, cooking steps, estimated time, difficulty level
4. "Save to favorites" functionality that stores recipes in Firestore
5. "My Favorites" page showing all saved recipes with ability to delete

UI REQUIREMENTS:

- Clean, modern interface with card-based layout for recipes
- Mobile-friendly responsive design
- Smooth animations when recipes appear
- Professional color scheme with green accents (sustainability theme)
- Clear call-to-action buttons

TECHNICAL REQUIREMENTS:

- Use Firebase Genkit for AI recipe generation
- Use Firestore for storing favorite recipes
- Include proper error handling with user-friendly messages
- Add loading spinner during AI recipe generation
- Make it accessible (ARIA labels, semantic HTML)
- Add timestamps to saved recipes

CONSTRAINTS:

- Keep the code clean and well-commented
- Use vanilla JavaScript and modern CSS (no frameworks)
- Ensure graceful degradation if AI is unavailable
- Optimize for performance (lazy load images, minimize API calls)

OUTPUT:
Provide the complete application structure with:

- app/page.tsx (main page with ingredient input)
- app/favorites/page.tsx (saved recipes page)
- components/RecipeCard.tsx (reusable component)
- app/globals.css (modern, responsive styling)
- lib/genkit.ts (AI recipe generation flow)
- lib/firebase.ts (database setup and operations)
- Clear comments explaining key sections and functions
```

## 2. Feature Enhancements

### Option A: Add Firestore Data Persistence

```markdown
TASK: Add comprehensive Firestore data persistence to the application.

REQUIREMENTS:

1. Create a Firestore collection called "[collection_name]"
2. Store the following data fields: [list specific fields]
3. Implement CRUD operations:

   - CREATE: Save new [items] with auto-generated IDs and timestamps
   - READ: Fetch all [items] for display, ordered by [field]
   - UPDATE: Allow editing [specific fields]
   - DELETE: Remove [items] with confirmation dialog

4. Add real-time listeners to update UI when data changes
5. Include proper error handling for network failures
6. Show loading states during database operations

ACCEPTANCE CRITERIA:

- Data persists after page refresh
- UI updates immediately when data changes
- Clear error messages if save/load fails
- Timestamps are stored in ISO format
```

### Option B: Enhance AI Capabilities

```markdown
TASK: Enhance the AI functionality with [specific improvement].

CONTEXT:
The current AI [describe current behavior]. I want to improve it by [desired enhancement].

REQUIREMENTS:

1. Modify the Genkit flow to [specific change]
2. Add [new AI capability] with the following parameters:

   - Input: [describe input format]
   - Processing: [describe AI processing logic]
   - Output: [describe expected output format]

3. Implement prompt engineering best practices:

   - Add system role: [specify role]
   - Include context: [specify context]
   - Use few-shot examples: [provide examples]
   - Add output format specification

4. Handle edge cases:
   - Empty/invalid inputs
   - API rate limits
   - Unexpected AI responses

ACCEPTANCE CRITERIA:

- AI responses are more [specific quality improvement]
- Response time under [X] seconds
- Proper error handling for API failures
- AI output follows consistent format
```

### Option C: Improve User Experience

```markdown
TASK: Improve the user experience by adding [specific UX enhancement].

CURRENT ISSUE:
Users currently [describe pain point or missing feature].

DESIRED IMPROVEMENT:
Add [specific feature] that allows users to [desired action/outcome].

IMPLEMENTATION DETAILS:

1. UI Component: [describe what to add/modify]
2. Interaction Pattern: [describe user flow]
3. Visual Feedback: [loading states, animations, messages]
4. Accessibility: [ARIA labels, keyboard navigation]

ACCEPTANCE CRITERIA:

- Feature works on mobile and desktop
- Provides clear feedback for user actions
- Follows accessibility best practices (WCAG 2.1 AA)
- Smooth animations (no janky scrolling)
```

## 3. Create About Page

**Fill in the placeholders before sending:**

````markdown
TASK: Create a professional "About" page for this project with structured metadata for discoverability.

PAGE REQUIREMENTS:

1. Create a new Next.js page at `/about` (e.g., `app/about/page.tsx`) with the following sections:

   HEADER SECTION:

   - Project title: "[YOUR PROJECT NAME]"
   - Tagline: "[One-sentence description]"
   - Hero image or logo (optional, can use placeholder)

   PROJECT OVERVIEW SECTION:

   - Description: [2-3 paragraphs explaining what the app does and why it's useful]
   - Key Features: Bullet list of main features
   - Technologies Used: Firebase Studio, Genkit, Firestore, [others]

   TEAM SECTION:

   - Team member(s): [List your name(s)]
   - Role(s): [e.g., "Developer", "Designer & Developer"]

   LINKS SECTION:

   - Demo URL: [Will be filled after deployment - leave placeholder]
   - GitHub Repository: [Optional - add if you plan to push to GitHub]
   - Built during: "AI Workshop: Firebase & Gemini Code Assist"
   - Date: [Today's date]

2. CRITICAL - Ensure the following metadata is rendered in the <head> of the page (or via Next.js metadata export):

   ```html
   <!-- Meta tags for workshop gallery scraper -->
   <meta name="workshop-project" content="true" />
   <meta name="project-name" content="[PROJECT NAME]" />
   <meta name="project-description" content="[SHORT DESCRIPTION]" />
   <meta name="project-demo-url" content="[DEPLOYMENT_URL]" />
   <meta name="project-github-url" content="[GITHUB_URL or empty]" />
   <meta name="project-author" content="[YOUR NAME(S)]" />
   <meta name="project-date" content="[YYYY-MM-DD]" />
   <meta
     name="project-technologies"
     content="Firebase Studio, Genkit, Firestore, JavaScript"
   />

   <!-- Structured data for better scraping -->
   <script type="application/ld+json">
     {
       "@context": "https://schema.org",
       "@type": "SoftwareApplication",
       "name": "[PROJECT NAME]",
       "description": "[DESCRIPTION]",
       "applicationCategory": "WebApplication",
       "url": "[DEPLOYMENT_URL]",
       "author": [
         {
           "@type": "Person",
           "name": "[TEAM MEMBER 1]"
         }
       ],
       "dateCreated": "[YYYY-MM-DD]",
       "keywords": "Firebase, Genkit, AI, [your keywords]",
       "programmingLanguage": ["JavaScript", "HTML", "CSS"],
       "codeRepository": "[GITHUB_URL]",
       "softwareRequirements": "Web Browser",
       "offers": {
         "@type": "Offer",
         "price": "0",
         "priceCurrency": "USD"
       }
     }
   </script>
   ```

3. STYLING:

   - Match the design language of the main app
   - Mobile-responsive layout
   - Professional typography
   - Include back-to-home navigation link

4. ACCESSIBILITY:
   - Semantic HTML (header, main, section, footer tags)
   - Alt text for images
   - Proper heading hierarchy (h1 → h2 → h3)

OUTPUT:
Create the complete Next.js page component (`app/about/page.tsx`) with all metadata properly configured. Leave [DEPLOYMENT_URL] as a placeholder - we'll update it after deployment.
````

## 4. Deployment

```markdown
TASK: Deploy this application to production using Firebase App Hosting.

PREPARATION STEPS:

1. Review the current project structure and ensure all files are properly organized
2. Check that all environment variables and API keys are configured correctly
3. Verify that Firestore security rules are set up (default rules are fine for this workshop)

DEPLOYMENT REQUIREMENTS:

1. Configure Firebase App Hosting for a Next.js application:

   - Set up the project for App Hosting deployment

   - Configure build settings (Next.js default)

   - Enable Firestore and Storage if not already enabled

2. Environment Configuration:

   - Ensure Genkit AI flows are configured for production
   - Set up proper API endpoint configurations
   - Configure CORS settings if needed

3. Build Process:

   - Optimize assets (minify CSS/JS, compress images)
   - Generate production build
   - Verify all dependencies are included

4. Deploy:

   - Execute the deployment to Firebase App Hosting
   - Provide the deployment URL once complete
   - Verify the app is accessible and functioning

5. Post-Deployment Verification:
   - Test critical functionality (AI features, database operations)
   - Verify mobile responsiveness
   - Check console for any errors

EXPECTED OUTPUT:

- Deployment success message
- Live application URL (https://[project-name].web.app or https://[project-name].firebaseapp.com)
- Deployment summary with any warnings or notes

IMPORTANT:
After deployment completes, provide the live URL so I can update the about page with the actual demo link.
```

## 5. Update About Page with Live URL

**Replace `[paste your URL here]` with your actual URL:**

```markdown
TASK: Update the `/about` page code with the deployment URL.

REQUIREMENTS:

1. Find all placeholder references to [DEPLOYMENT_URL] in the about page code

2. Replace with the actual deployment URL: [paste your URL here]
3. Update both:
   - The meta tag: <meta name="project-demo-url" content="[YOUR_URL]">
   - The JSON-LD structured data: "url": "[YOUR_URL]"
   - Any visible demo links in the HTML

Verify all URLs are updated correctly.
```

## 6. Final Deploy

```markdown
TASK: Deploy the updated `/about` page to production.

This is a quick update deployment to include the live demo URL in the about page.
```
