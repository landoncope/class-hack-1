# Agent Training Academy - Teacher Solutions

## Overview
This is the **EASY** level security challenge. Students learn basic web inspection techniques.

**Estimated Time:** 15-20 minutes
**Skills Taught:** HTML inspection, browser DevTools, robots.txt

---

## Flag #1: Password in HTML Comments
**Location:** `index.html`

**Vulnerability:** Password is stored in an HTML comment

**Solution:**
1. Right-click on the page and select "Inspect" or "View Page Source"
2. Look for HTML comments (marked with `<!-- -->`)
3. Find the comment block containing:
   - Username: `shadow_agent`
   - Password: `supersecret123`

**Teaching Point:** Never store sensitive information in HTML comments. Anyone can view the source code!

---

## Flag #2: Secret Admin Panel via robots.txt
**Location:** `robots.txt` and `secret-admin-panel.html`

**Vulnerability:** Secret pages listed in robots.txt

**Solution:**
1. Navigate to `/robots.txt` in the browser
2. See the list of "disallowed" pages
3. Visit `/secret-admin-panel.html`

**Teaching Point:** robots.txt is PUBLIC. It tells search engines where NOT to go, but humans can still visit those pages. Never use it to hide sensitive content!

---

## Flag #3: Confidential Files
**Location:** `confidential-files.html`

**Vulnerability:** Another secret page listed in robots.txt

**Solution:**
1. Check robots.txt for all listed pages
2. Visit `/confidential-files.html`

**Teaching Point:** Security through obscurity doesn't work. If a page exists, assume someone will find it.

---

## Additional Learning Opportunities

### Console Logs
The login page has debug information in the browser console (F12 > Console):
```
DEBUG: Admin password backup: supersecret123
```

### Bonus Challenge
- The Konami code (Up, Up, Down, Down, Left, Right, Left, Right, B, A) triggers an Easter egg but isn't a vulnerability

---

## Common Student Questions

**Q: Why would developers leave passwords in comments?**
A: Sometimes during development, they add temporary notes and forget to remove them. Code review and security scanning tools help catch these.

**Q: Isn't robots.txt supposed to be secret?**
A: No! It's specifically designed to be public so search engine crawlers can read it.

**Q: Can I really just look at any website's source code?**
A: Yes! Everything sent to your browser (HTML, CSS, JavaScript) is visible to you.

---

## Security Concepts Covered
1. **Information Disclosure** - Accidentally exposing sensitive data
2. **Security Through Obscurity** - Hiding things is not security
3. **Client-Side Exposure** - Anything in the browser is visible
4. **robots.txt Misuse** - Using it to "hide" pages backfires
