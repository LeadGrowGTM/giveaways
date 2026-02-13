# Create New Giveaway Page

Scaffold a new giveaway landing page + thank-you page from existing templates, wire up the Kit form redirect, and add it to the hub page.

## Arguments
- `$ARGUMENTS` - The giveaway name and brief description (required, e.g., "sales-playbook - 50-page B2B sales playbook with email templates")

## Instructions

### 1. Parse Input
- Extract the giveaway slug from the name (lowercase, hyphens, e.g., "sales-playbook")
- Extract the description for use in page copy
- Confirm with the user: slug, title, description, what's included (checklist items for thank-you page)

### 2. Ask for Kit Form ID
Ask the user:
- "What's the Kit (ConvertKit) form ID for this giveaway? (Create one at app.kit.com/forms if needed)"
- If reusing an existing form, note that the redirect URL will differentiate pages

### 3. Create Landing Page
Create `{slug}/index.html` using the LinkedIn Monitoring page (`linkedin-monitoring/index.html`) as the reference template.

Key elements to customize:
- `<title>` tag and meta description
- Hero section: h1 title (with `<span>` for accent color), subtitle paragraph
- Hero stats: 2-3 key numbers/stats about the giveaway
- Form card: h2, subtext, Kit form action URL with the provided form ID
- Hidden redirect input: `<input type="hidden" name="options[redirect_url]" value="https://giveaway.leadgrow.ai/{slug}/thank-you/">`
- Items section: 2-3 cards describing what's included (with numbered badges and tags)
- "Who This Is For" or "What You Can Do" section: 3 use-case cards with emojis
- CTA section at bottom
- Footer linking to leadgrow.ai
- Include `<script src="https://f.convertkit.com/ckjs/ck.5.js"></script>` before closing body
- Use `data-sv-form="{formId}"` and `data-uid` attributes on the form if using ck.js

Design system (MUST follow):
- Background: `#f7f3ef`
- Text: `#2d2d2d`
- Accent teal: `#62b3ae`
- CTA orange: `#eb8b6a` (hover: `#d97a5a`)
- Cards: white bg, `border: 1px solid #e5e0db`, `border-radius: 12px`
- Font: `system-ui, -apple-system, sans-serif`
- Responsive: single column below 900px, stack stats below 600px

### 4. Create Thank-You Page
Create `{slug}/thank-you/index.html` using the Competitor Toolkit thank-you page (`competitor-toolkit/thank-you/index.html`) as the reference template.

Key elements:
- Title: "You're In." with teal accent span
- Subtitle: "Check your email. [Description] is on its way."
- Checklist: list of items they'll receive (with teal checkmarks)
- Spam folder notice
- Footer linking to leadgrow.ai
- NO gif by default (ask user if they want one)

### 5. Update Hub Page
Edit `index.html` (the root hub) to add a new card for this giveaway:
- Add a new `<a href="/{slug}" class="card">` inside the `.cards` div
- Include emoji, title, short description, and CTA button
- Ask the user what emoji to use for the card

### 6. Update Grid Layout (if needed)
If there are now more than 3 giveaways, consider switching the hub grid to `repeat(auto-fit, minmax(260px, 1fr))` instead of `repeat(3, 1fr)` so it wraps nicely.

### 7. Summary
Show the user:
- Files created: `{slug}/index.html`, `{slug}/thank-you/index.html`
- Files modified: `index.html` (hub)
- Redirect URL: `https://giveaway.leadgrow.ai/{slug}/thank-you/`
- Remind them to configure the Kit form automation to send the actual download/asset email
- Ask if they want to commit and push

## Reference Pages
- Landing page template: `linkedin-monitoring/index.html` (most complete, has redirect + ck.js)
- Thank-you template: `competitor-toolkit/thank-you/index.html` (has item checklist)
- Hub page: `index.html` (card grid layout)

## Design System Quick Reference
| Element | Value |
|---------|-------|
| Background | `#f7f3ef` |
| Card bg | `white` |
| Text primary | `#2d2d2d` |
| Text secondary | `#666` |
| Text muted | `#888` |
| Accent teal | `#62b3ae` |
| CTA orange | `#eb8b6a` |
| CTA hover | `#d97a5a` |
| Border | `#e5e0db` |
| Card radius | `12px` |
| Form card radius | `16px` |
| Section padding | `60px 0` |
| Hero padding | `80px 0 60px` |
| Max width | `1100px` |
| Font | `system-ui, -apple-system, sans-serif` |

## Kit Form Setup Reminder
After creating the pages, the user must:
1. Create or configure the Kit form at `app.kit.com`
2. Set up the email automation/sequence that delivers the actual giveaway asset
3. The redirect URL in the HTML handles the post-submission redirect to the thank-you page
