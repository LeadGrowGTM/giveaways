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
Create `{slug}/index.html` using the Extract Competitors page (`extract-competitors/index.html`) as the reference template.

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

Design system (MUST follow — LeadGrow Brand Kit):
- Font: `'Figtree', system-ui, -apple-system, sans-serif` (add Google Fonts link in head)
- Background: `#F4F3EF` (warm cream)
- Text headings: `#352922` (dark brown)
- Text body: `#57534D` (gray-brown)
- Text secondary: `#78716C` (stone-500)
- Text muted: `#A8A29E` (stone-400)
- Accent teal: `#6FAEC2` (dark: `#5A9AAD`)
- CTA buttons: `background: linear-gradient(135deg, #C2845B 0%, #FFAF1A 100%); border-radius: 75px;`
- CTA hover: `transform: scale(1.03)`
- CTA solid (links, accents): `#EB8B4B`
- Cards: white bg, `border: 1px solid #D6D3D1`, `border-radius: 12px`
- Form card: `border-radius: 16px`, `box-shadow: 0px 4px 15px rgba(53, 41, 34, 0.2)`
- Dark sections: `#352922`, Footer: `#1C1917`
- Input focus border: `#6FAEC2`
- Badge radius: `48px`
- Responsive: single column below 900px, stack stats below 600px
- Animation: `@keyframes fade-up` with `prefers-reduced-motion` guard
- Google Fonts link: `<link href="https://fonts.googleapis.com/css2?family=Figtree:wght@400;500;600;700;800&display=swap" rel="stylesheet">`

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
Edit `index.html` (the root hub) to add a new card inside the `.grid` div. Follow the existing card pattern:
- Use `<a href="{slug}/" class="card {color}">` where color is `teal`, `coral`, or `dark`
- Include: `.accent` strip, `.icon-area` with SVG icon + `.tag`, `.card-body` with h2 + p, `.card-stats` with 3 stats, `.card-cta` with button
- Reference existing cards in `index.html` for the exact HTML structure
- Ask the user which color theme to use for the card

### 6. Update Grid Layout (if needed)
If there are now more than 2 giveaways, update the `.grid` CSS from `repeat(2, 1fr)` to `repeat(3, 1fr)` or `repeat(auto-fit, minmax(300px, 1fr))` so it wraps nicely.

### 7. Summary
Show the user:
- Files created: `{slug}/index.html`, `{slug}/thank-you/index.html`
- Files modified: `index.html` (hub)
- Redirect URL: `https://giveaway.leadgrow.ai/{slug}/thank-you/`
- Remind them to configure the Kit form automation to send the actual download/asset email
- Ask if they want to commit and push

## Reference Pages
- Landing page template: `extract-competitors/index.html` (most complete, has redirect + ck.js)
- Thank-you template: `extract-competitors/thank-you/index.html` (has item checklist)
- Hub page: `index.html` (card grid with accent strips, SVG icons, stats, CTAs)

## Design System Quick Reference (LeadGrow Brand Kit)
| Element | Value |
|---------|-------|
| Font | `'Figtree', system-ui, -apple-system, sans-serif` |
| Background | `#F4F3EF` |
| Card bg | `white` |
| Text headings | `#352922` |
| Text body | `#57534D` |
| Text secondary | `#78716C` |
| Text muted | `#A8A29E` |
| Accent teal | `#6FAEC2` (dark: `#5A9AAD`) |
| CTA gradient | `linear-gradient(135deg, #C2845B 0%, #FFAF1A 100%)` |
| CTA solid | `#EB8B4B` |
| Border | `#D6D3D1` |
| Light border | `#E7E5E4` |
| Dark bg | `#352922` |
| Footer bg | `#1C1917` |
| Card radius | `12px` |
| Form card radius | `16px` |
| Button radius | `75px` (pill) |
| Badge radius | `48px` |
| Shadow | `0px 4px 15px rgba(53, 41, 34, 0.2)` |
| Section padding | `60px 0` |
| Hero padding | `80px 0 60px` |
| Max width | `1100px` |

## Kit Form Setup Reminder
After creating the pages, the user must:
1. Create or configure the Kit form at `app.kit.com`
2. Set up the email automation/sequence that delivers the actual giveaway asset
3. The redirect URL in the HTML handles the post-submission redirect to the thank-you page
