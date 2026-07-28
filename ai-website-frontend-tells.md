# AI Website Frontend Cleanup Rules

You are reviewing a website that was built using an AI code generation tool (Cursor, Lovable, Bolt, v0, or similar). Your job is to identify and fix common patterns that make AI-built websites look unpolished or generic.

Apply these rules when reviewing or editing website code and copy.

## Copy Patterns to Fix

### Em dashes
Find em dashes (—) used for emphasis or as breaks between thoughts. Replace them with commas, periods, or parentheses.

**Find:** "We build websites — fast, beautiful, and functional."
**Replace with:** "We build websites that are fast, beautiful, and functional."

### Staccato sentence bursts
Find sequences of three or more short sentences used for dramatic effect. Combine them into natural flowing sentences.

**Find:** "No fluff. No jargon. No wasted time."
**Replace with:** "No fluff, jargon, or wasted time."

**Find:** "We listen. We plan. We execute."
**Replace with:** "We listen, plan, and execute."

### Rule-of-three groupings
AI tends to group things in threes. If you see this pattern repeated throughout the site, vary it. Two items or four items are fine.

**Find:** "Fast. Reliable. Affordable."
**Replace with:** "Fast and reliable." (if affordable is implied or less important)

### Contrast framing
Find phrases that use "not X, but Y" or "it's not about X, it's about Y" structures. Rewrite to state the point directly.

**Find:** "It's not about working harder, it's about working smarter."
**Replace with:** "Work smarter, not longer."

**Find:** "This isn't just a product. It's a solution."
**Replace with:** "This product solves [specific problem]."

### Eyebrow/kicker text
AI builders add small uppercase labels above almost every heading. Remove unnecessary ones that don't add information.

**Keep if:** The eyebrow adds real context (e.g., "CASE STUDY" above a case study title)
**Remove if:** The eyebrow just repeats what's obvious (e.g., "OUR SERVICES" above a "Services" heading)

### Placeholder text
Search the codebase for these common placeholders and replace or remove them:
- `[TO FILL]`
- `[INSERT]`
- `[PLACEHOLDER]`
- `Lorem ipsum`
- `Your tagline here`
- `Company Name`
- `john@example.com`
- `123-456-7890`
- `123 Main Street`

### Generic button text
Replace vague button labels with specific actions.

**Find:** "Learn More", "Get Started", "Click Here", "Submit"
**Replace with:** Specific actions like "See pricing", "Book a call", "Send message", "Download guide"

## Design Patterns to Fix in Code

### Responsive breakpoints
AI builders often test at one width. Check the site at these widths and fix any issues:
- 1440px (desktop)
- 1280px (laptop)
- 768px (tablet)
- 390px (mobile)

Common issues to look for:
- Horizontal scrollbar appearing (overflow)
- Text overlapping images
- Buttons or cards stacking incorrectly
- Navigation breaking or overlapping
- Images stretching or cropping badly

### Typography inconsistencies
Check that these are consistent across all pages:
- Heading font family and weights
- Body text size and line height
- Link colors and hover states
- Button text styling

### Uppercase pill/badge overuse
AI builders add small uppercase badges or pills above sections. If every section has one, remove most of them. Keep only where they add real value.

### Inline styles
Search for `style=` attributes in JSX/HTML. Move these to proper CSS classes for maintainability.

### Hardcoded values
Search for hardcoded pixel values that should be responsive or use CSS variables. Common offenders:
- `width: 1440px` (should be max-width or percentage)
- `height: 800px` (should be min-height or auto)
- `margin-left: 200px` (should be responsive)

## Form Issues to Check

AI-built forms often look functional but don't actually work. Check these:

### Form submission
- Does the form have an actual `action` or `onSubmit` handler?
- Does it connect to an email service, database, or API?
- Or does it just `console.log` the data and do nothing?

### Validation
- Are required fields actually validated?
- Do error states display properly?
- Does the submit button disable during submission?

### Success/error states
- What happens after submission?
- Is there a success message?
- Is there error handling if submission fails?

## Code Quality Checks

### Console errors
Open browser dev tools and check for:
- JavaScript errors
- Failed network requests
- Missing images or assets
- Hydration errors (React/Next.js)

### Image optimization
Check that images:
- Use Next.js `<Image>` component (if Next.js project) or proper lazy loading
- Have appropriate `alt` text
- Are reasonably sized (not 5MB hero images)
- Have correct aspect ratios set

### Meta tags
Check that each page has:
- Unique `<title>` tag
- Meta description
- Open Graph tags for social sharing
- Favicon

## What to Flag for Human Review

Some issues require human judgment or professional help. Flag these rather than attempting to fix:

### Messaging and positioning
- Is the copy saying the right things for the target audience?
- Does the value proposition make sense?
- Is the brand voice consistent?
- These require strategy, not just editing.

### Security concerns
- Authentication/login systems
- Payment processing
- User data handling
- API key exposure in client code
- These require a security review.

### Backend integrations
- Database connections
- Email service setup
- Third-party API integrations
- These require developer implementation.

### Legal content
- Privacy policy
- Terms of service
- Cookie consent
- These require legal review, not AI generation.
