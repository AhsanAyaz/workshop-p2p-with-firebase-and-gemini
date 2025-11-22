# Troubleshooting Guide

## Common Firebase Studio Issues & Solutions

This guide covers the most common issues you might encounter during the workshop and how to fix them.

---

## 🚫 Firebase Studio Issues

### Issue: "I can't access Firebase Studio"

**Symptoms:**
- Firebase Studio page won't load
- Getting 404 error
- Redirected to regular Firebase Console

**Solutions:**

1. **Check URL**: Make sure you're going to the correct URL:
   - `firebase.google.com/studio` (check for exact spelling)

2. **Check Access**: Firebase Studio might be in limited preview
   - Ensure your Google account has access
   - Try switching to a different Google account
   - Contact workshop instructor for access help

3. **Browser Issues**:
   - Try a different browser (Chrome, Edge, Firefox)
   - Clear browser cache and cookies
   - Disable browser extensions temporarily
   - Try incognito/private mode

4. **Check Status**: Firebase Studio might be experiencing issues
   - Check [Firebase Status Page](https://status.firebase.google.com/)
   - Check workshop chat for announcements

---

### Issue: "Firebase Studio is not generating code"

**Symptoms:**
- Paste prompt but nothing happens
- Chat shows "thinking..." forever
- Generated code is incomplete

**Solutions:**

1. **Check Prompt**:
   - Make sure your prompt is clear and complete
   - Include all required sections (ROLE, CONTEXT, TASK, etc.)
   - Remove any special characters that might break parsing
   - Try simplifying your prompt first, then add details

2. **Refresh & Retry**:
   - Refresh the Firebase Studio page
   - Start a new conversation
   - Try the prompt again

3. **Break It Down**:
   - Instead of one huge prompt, break into smaller steps
   - Generate basic app first
   - Add features one by one with follow-up prompts

4. **Check Limits**:
   - You might have hit rate limits
   - Wait 5-10 minutes and try again
   - Use shorter prompts

---

### Issue: "AI generated wrong code"

**Symptoms:**
- Code doesn't match what you asked for
- Missing features
- Wrong technology used

**Solutions:**

1. **Be More Specific**:
   - Review your prompt - was it clear enough?
   - Add more details and constraints
   - Include examples of what you want

2. **Use Follow-Up Prompts**:
   ```
   ISSUE: The code is missing [feature].

   TASK: Add [feature] with the following requirements:
   [List specific requirements]

   Acceptance criteria:
   - [Specific outcome 1]
   - [Specific outcome 2]
   ```

3. **Iterate**:
   - AI might not get it perfect first time
   - Keep refining with clearer prompts
   - This is normal - iteration is part of the process!

---

## 🔥 Genkit & AI Issues

### Issue: "AI features not working"

**Symptoms:**
- AI responses are empty
- Getting "API key invalid" errors
- AI requests timeout

**Solutions:**

1. **Check API Configuration**:
   - Ensure Genkit is properly initialized
   - Check Firebase project is set up correctly
   - Verify API quotas haven't been exceeded

2. **Check Prompts to AI**:
   - Look at the Genkit flow code
   - Is the prompt clear and well-structured?
   - Are you passing the right parameters?

3. **Add Error Handling**:
   Use this debug prompt:
   ```
   ISSUE: AI features are not working. I'm getting [error message].

   TASK: Add comprehensive error handling and logging to the Genkit flows:
   1. Log all inputs to the AI
   2. Log the AI response
   3. Catch and display specific error messages
   4. Add retry logic for transient failures

   Show me what's going wrong.
   ```

4. **Test with Simple Input**:
   - Try the simplest possible input first
   - If that works, gradually increase complexity
   - Helps identify what's causing the issue

---

### Issue: "AI responses are too slow"

**Symptoms:**
- AI takes > 10 seconds to respond
- Users getting impatient
- Timeout errors

**Solutions:**

1. **Add Loading States**:
   ```
   TASK: Improve the loading experience while waiting for AI:
   1. Show a progress spinner immediately
   2. Add estimated wait time: "This usually takes 3-5 seconds..."
   3. Add a "Still working..." message after 5 seconds
   4. Make the loading state visually engaging (animation)
   ```

2. **Optimize Prompts**:
   - Shorter, more focused prompts to AI = faster responses
   - Remove unnecessary context
   - Be specific about desired output length

3. **Check Model**:
   - Ensure you're using Gemini Flash (faster) not Pro (slower but more capable)
   - Adjust model in Genkit configuration if needed

4. **Set Realistic Expectations**:
   - AI responses take 2-5 seconds - this is normal
   - Use loading states to make it feel faster
   - Can't really make the AI itself faster

---

## 💾 Firestore Issues

### Issue: "Data not saving to Firestore"

**Symptoms:**
- Click save but nothing happens
- Data disappears after refresh
- Console shows Firestore errors

**Solutions:**

1. **Check Firestore Initialization**:
   ```
   ISSUE: Firestore operations are failing.

   TASK: Debug Firestore configuration:
   1. Verify Firestore is initialized correctly
   2. Check that the Firebase project ID is correct
   3. Add console.log statements before each Firestore operation
   4. Log success and error states
   5. Show me the error messages
   ```

2. **Check Security Rules**:
   - Go to Firebase Console > Firestore > Rules
   - For workshop, use permissive rules:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /{document=**} {
         allow read, write: if true;  // WARNING: Only for workshop!
       }
     }
   }
   ```
   - Click "Publish"

3. **Check Browser Console**:
   - Press F12 to open DevTools
   - Click "Console" tab
   - Look for red error messages
   - Share these with the instructor if stuck

4. **Check Data Format**:
   - Make sure you're passing valid JavaScript objects
   - No undefined values
   - Timestamps should use Firestore Timestamp type

---


### Issue: "Real-time listeners not working"

**Symptoms:**
- Data doesn't update automatically
- Need to refresh page to see changes
- No error messages

**Solutions:**

1. **Verify Listener Code**:
   ```
   TASK: Debug the real-time listener:
   1. Add console.log when listener attaches
   2. Add console.log when listener receives updates
   3. Verify we're using onSnapshot (not just get)
   4. Make sure listener isn't being unsubscribed immediately
   5. Check for errors in the listener callback
   ```

2. **Check Unsubscribe Logic**:
   - Make sure you're not accidentally unsubscribing
   - Listeners should stay active while page is open
   - Only unsubscribe when leaving the page

3. **Test Manually**:
   - Open Firebase Console > Firestore
   - Manually add/edit a document
   - Does your app update? If yes, listener works!

---

## 🌐 Deployment Issues

### Issue: "Deployment fails"

**Symptoms:**
- Deployment command fails
- "Permission denied" errors
- "Project not found" errors

**Solutions:**

1. **Check Firebase Project**:
   - Make sure you've created a Firebase project
   - Note the project ID
   - Ensure you have owner/editor permissions

2. **Check Firebase CLI (if used)**:
   - Run `firebase --version` to check it's installed
   - Run `firebase login` to authenticate
   - Run `firebase use --add` to select project

3. **Try Firebase Studio Deploy**:
   - Use the deployment prompt from README.md
   - Let Firebase Studio handle deployment
   - It should configure everything automatically

4. **Check Quotas**:
   - Free tier has limits
   - Check Firebase Console > Usage
   - Upgrade to Blaze plan if needed (pay-as-you-go)

---

### Issue: "Deployed app shows blank page"

**Symptoms:**
- Deployment succeeds but page is blank
- Getting 404 errors on deployed site
- CSS/JS not loading

**Solutions:**

1. **Check Browser Console**:
   - Open deployed URL
   - Press F12 for DevTools
   - Look for error messages
   - Common: 404 for missing files, CORS errors

2. **Check File Paths**:
   - Ensure all file references are relative (not absolute)
   - `./styles.css` ✅ not `/Users/you/project/styles.css` ❌
   - Check image paths, script paths, CSS paths

3. **Check Public Directory**:
   - Verify `firebase.json` points to correct public directory
   - Default is usually `public/` or root `/`
   - Make sure all files are in that directory

4. **Check index.html**:
   - Must be named exactly `index.html` (lowercase)
   - Must be in the public directory
   - Check for syntax errors (unclosed tags, etc.)

5. **Hard Refresh**:
   - Ctrl+Shift+R (Windows/Linux) or Cmd+Shift+R (Mac)
   - Clears cache and reloads
   - Browser might be caching old version

---

### Issue: "About page not accessible"

**Symptoms:**
- Main app works but about page gives 404
- Can't submit project because about URL fails

**Solutions:**

1. **Check File Name**:
   - Must be named `about.html` (lowercase)
   - Not `About.html` or `about.HTML`

2. **Check File Location**:
   - Should be in same directory as `index.html`
   - URL should be `https://your-app.web.app/about.html`

3. **Re-deploy**:
   - After adding about.html, you must deploy again
   - Changes don't appear until you deploy

4. **Check Firebase Hosting Configuration**:
   ```json
   {
     "hosting": {
       "public": ".",
       "ignore": [
         "firebase.json",
         "**/.*",
         "**/node_modules/**"
       ]
     }
   }
   ```

---

## 🎨 UI/UX Issues

### Issue: "App looks bad on mobile"

**Symptoms:**
- Text too small on phone
- Buttons cut off
- Have to scroll horizontally
- Elements overlapping

**Solutions:**

1. **Add Viewport Meta Tag**:
   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   ```
   Must be in `<head>` section!

2. **Use Responsive CSS Prompt**:
   ```
   TASK: Make this app fully responsive for mobile devices.

   REQUIREMENTS:
   1. Mobile breakpoint: screens < 768px
   2. Changes needed:
      - Stack elements vertically
      - Larger touch targets (min 44x44px)
      - Readable font size (min 16px)
      - No horizontal scrolling
      - Responsive images (max-width: 100%)

   3. Test on these screen sizes:
      - Mobile: 375px width
      - Tablet: 768px width
      - Desktop: 1200px width

   Use mobile-first CSS with media queries.
   ```

3. **Test on Actual Device**:
   - Don't just resize browser window
   - Test on real phone if possible
   - Or use browser DevTools device emulation (F12 > Toggle device toolbar)

---

### Issue: "Loading spinner never appears"

**Symptoms:**
- Click button but no feedback
- Not clear if app is working
- Users click multiple times

**Solutions:**

1. **Add Immediate Feedback**:
   ```
   TASK: Fix the loading state to appear immediately.

   CURRENT ISSUE: Users click the button but don't see any feedback.

   REQUIREMENTS:
   1. Show loading spinner within 100ms of click
   2. Disable the button during loading
   3. Change button text: "Submit" → "Submitting..."
   4. Add visual loading state (spinner icon)

   The loading state should appear BEFORE any async operations start.
   ```

2. **Check Event Listener**:
   - Make sure loading state is set synchronously
   - Not inside a Promise or async function
   - Set it before making API calls

---

## 🐛 JavaScript Errors

### Issue: "Uncaught ReferenceError: [function] is not defined"

**Symptoms:**
- Console shows "ReferenceError"
- Feature doesn't work when clicked
- Function is missing

**Solutions:**

1. **Check Function Is Defined**:
   - Search your JS files for the function name
   - Make sure it's spelled correctly
   - Case sensitive: `submitForm` ≠ `SubmitForm`

2. **Check Script Loading Order**:
   - If using multiple JS files, order matters
   - Functions must be defined before they're called
   - Put `<script>` tags in right order

3. **Debug Prompt**:
   ```
   ISSUE: Getting error "Uncaught ReferenceError: submitForm is not defined"

   The error occurs when I click [button].

   TASK:
   1. Find where submitForm should be defined
   2. Ensure it's defined before it's called
   3. Check for typos in function name
   4. Verify the script is loaded
   5. Fix the issue and explain what was wrong
   ```

---

### Issue: "App works locally but not when deployed"

**Symptoms:**
- Everything works in Firebase Studio preview
- Deployed version has errors
- Console shows different errors

**Solutions:**

1. **Check API Keys/Environment**:
   - Localhost and production might use different configs
   - Make sure Firebase config is correct for production

2. **Check HTTPS**:
   - Some features require HTTPS
   - Local uses HTTP, deployed uses HTTPS
   - Camera, geolocation, etc. need HTTPS

3. **Check File Paths**:
   - Relative vs absolute paths
   - Works locally: `/Users/me/project/file.js`
   - Breaks deployed: use `./file.js` instead

4. **Hard Refresh**:
   - Your browser might cache old version
   - Ctrl+Shift+R (Cmd+Shift+R on Mac)

---

## ⚡ Performance Issues

### Issue: "App is very slow"

**Symptoms:**
- Long loading times
- Laggy interactions
- Slow AI responses

**Solutions:**

1. **Optimize Images**:
   - Compress images before uploading
   - Use appropriate sizes (not 4K images for thumbnails)
   - Use modern formats (WebP)

2. **Minimize Firestore Reads**:
   - Don't fetch all data at once
   - Implement pagination
   - Cache data locally

3. **Debounce Inputs**:
   ```
   TASK: Optimize performance by debouncing the search input.

   CURRENT ISSUE: The app makes an API call on every keystroke, causing slowness.

   REQUIREMENTS:
   1. Add debouncing with 300ms delay
   2. Only make API call after user stops typing
   3. Show "typing..." indicator while debouncing
   4. Cancel pending requests if user types again
   ```

4. **Use Loading Skeletons**:
   - Instead of blank page, show skeleton loaders
   - Makes app feel faster
   - Better user experience

---

## 📋 Submission Troubleshooting

### Metadata Verification (Run Before Submitting)

Before submitting, open your live about page and run this in the browser console:

```javascript
// Open your about page in browser
// Press F12 (or Cmd+Option+I on Mac) to open DevTools
// Click "Console" tab
// Paste this code and press Enter:

console.log('=== METADATA CHECK ===');

const checks = {
  'Workshop Project Flag': document.querySelector('meta[name="workshop-project"]')?.content,
  'Project Name': document.querySelector('meta[name="project-name"]')?.content,
  'Project Description': document.querySelector('meta[name="project-description"]')?.content,
  'Demo URL': document.querySelector('meta[name="project-demo-url"]')?.content,
  'Author': document.querySelector('meta[name="project-author"]')?.content,
  'Date': document.querySelector('meta[name="project-date"]')?.content,
  'Technologies': document.querySelector('meta[name="project-technologies"]')?.content,
  'GitHub URL': document.querySelector('meta[name="project-github-url"]')?.content || '(optional)',
};

let allGood = true;

for (const [key, value] of Object.entries(checks)) {
  if (!value || value === '' || value.includes('[')) {
    console.error(`❌ MISSING: ${key}`);
    allGood = false;
  } else {
    console.log(`✅ ${key}: ${value}`);
  }
}

// Check JSON-LD
try {
  const jsonLd = JSON.parse(document.querySelector('script[type="application/ld+json"]').textContent);
  console.log('✅ JSON-LD is valid:', jsonLd);
} catch (e) {
  console.error('❌ JSON-LD is invalid or missing:', e);
  allGood = false;
}

if (allGood) {
  console.log('\n🎉 ALL CHECKS PASSED! You\'re ready to submit!');
} else {
  console.error('\n⚠️ FIX THE ISSUES ABOVE before submitting.');
}
```

### Common Submission Errors & Fixes

#### Error: "Unable to fetch your about page"

**Cause:** The URL is not accessible or doesn't exist.

**Fix:**
1. Copy the URL you're trying to submit
2. Paste it in an incognito browser window
3. Does the page load? If not:
   - Check that you deployed your app
   - Check that the URL is correct
   - Check that `/about.html` exists in your deployed app

#### Error: "This doesn't appear to be a workshop project"

**Cause:** Missing the `workshop-project` meta tag.

**Fix:**
1. Open your `about.html` file
2. In the `<head>` section, add:
   ```html
   <meta name="workshop-project" content="true">
   ```
3. Re-deploy your app
4. Try submitting again

#### Error: "Required field missing: [field name]"

**Cause:** One of the required metadata tags is missing or empty.

**Fix:**
1. Check which field is missing (the error will tell you)
2. Open your `about.html` file
3. Add the missing meta tag in the `<head>` section:
   ```html
   <meta name="project-name" content="Your Project Name">
   ```
4. Make sure there are NO placeholder brackets `[...]` in the content
5. Re-deploy your app
6. Try submitting again

#### Error: "This project has already been submitted"

**Cause:** You (or someone else) already submitted this project.

**Fix:**
- This is actually okay! Your project is in the gallery
- Click "View Gallery" to see it
- If you need to update information, contact the instructor

#### Error: "Invalid URL format"

**Cause:** The URL you entered is not a valid HTTPS URL.

**Fix:**
1. Make sure your URL starts with `https://`
2. Make sure it ends with `.html` or `/about`
3. Remove any spaces or special characters
4. Example correct format:
   ```
   https://my-app.web.app/about.html
   ```

#### Error: "CORS error" or "Cross-origin request blocked"

**Cause:** Your deployed app is blocking cross-origin requests.

**Fix:**
This is a complex issue. Contact the instructor for help. In the meantime:
1. Make sure your app is deployed on Firebase Hosting (not a custom domain)
2. Firebase Hosting usually handles CORS correctly
3. Double-check your deployment succeeded

---

## 🆘 Getting Help

### During Workshop:

1. **Check This Guide First** - Most issues are covered here
2. **Ask a Neighbor** - They might have solved the same issue
3. **Raise Your Hand** - Instructor is here to help
4. **Share Error Messages** - Screenshot console errors to show instructor

### Self-Help Steps:

1. **Read error messages carefully** - They usually tell you what's wrong
2. **Check browser console** (F12) - Errors show here
3. **Try incognito mode** - Rules out cache/extension issues
4. **Simplify and test** - Remove features until it works, then add back

### After Workshop:

- **Community Forum**: TensorFlow User Group Islamabad channels
- **GitHub Issues**: Post in this workshop repo
- **Email Instructor**: Contact info in workshop materials

---

## 💡 Prevention Tips

### Before You Start Coding:

- ✅ Read the prompt templates thoroughly
- ✅ Plan your app features (keep it simple!)
- ✅ Check examples in APP-IDEAS.md
- ✅ Have Firebase Studio open and ready

### While Building:

- ✅ Test frequently (after each feature)
- ✅ Save your work (Firebase Studio auto-saves, but check)
- ✅ Check browser console for errors
- ✅ Use the README.md templates
- ✅ Start simple, add complexity gradually

### Before Deploying:

- ✅ Test all features locally
- ✅ Check mobile responsiveness
- ✅ Clear any console errors
- ✅ Review about page metadata
- ✅ Verify API quotas

### Before Submitting:

- ✅ Test deployed app in incognito
- ✅ Run metadata validation script
- ✅ Check about page loads
- ✅ Screenshot gallery entry for portfolio

---

## 🎯 Quick Reference

### Most Common Fixes:

1. **Hard refresh**: Ctrl+Shift+R (Cmd+Shift+R)
2. **Clear cache**: Settings > Clear browsing data
3. **Check console**: F12 > Console tab
4. **Incognito mode**: Rules out cache/extension issues
5. **Re-deploy**: After any changes to files

### Essential DevTools Shortcuts:

- **F12**: Open DevTools
- **Ctrl+Shift+I**: Open DevTools (alternative)
- **Ctrl+Shift+C**: Inspect element
- **Ctrl+Shift+J**: Jump to console
- **Ctrl+Shift+R**: Hard refresh

### Key Firebase URLs:

- Firebase Console: console.firebase.google.com
- Firebase Studio: firebase.google.com/studio
- Firebase Status: status.firebase.google.com

---

**Remember**: Everyone encounters issues! Don't get frustrated. Debugging is part of learning. Ask for help! 💪

**Workshop**: TensorFlow User Group Islamabad - AI Study Jams Day 3