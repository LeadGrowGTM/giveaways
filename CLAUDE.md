# CLAUDE.md — Giveaways

LeadGrow giveaway landing pages. Static HTML deployed via GitHub Pages.

## Site
- **Domain:** `giveaway.leadgrow.ai`
- **Hosting:** GitHub Pages from `main` branch
- **Repo:** `LeadGrowGTM/giveaways`

## Structure
```
index.html                          # Hub page linking all giveaways
{slug}/index.html                   # Landing page with Kit form
{slug}/thank-you/index.html         # Post-submission thank-you page
CNAME                               # Custom domain config
```

## Giveaways
| Slug | Kit Form ID | Description |
|------|-------------|-------------|
| `b2b-database` | `9029460` | 8.5M segmented B2B records |
| `competitor-toolkit` | `9067339` | 3 competitor intelligence systems + playbook |
| `linkedin-monitoring` | `9067339` | LinkedIn engagement monitor app |

## Form Redirects
Every Kit form MUST have a hidden redirect input:
```html
<input type="hidden" name="options[redirect_url]" value="https://giveaway.leadgrow.ai/{slug}/thank-you/">
```
Without this, Kit shows its default success page instead of our thank-you page.

Pages using ConvertKit JS (`ck.5.js`) intercept form submission via AJAX — the hidden input ensures the redirect still works.

## Design System
| Token | Value |
|-------|-------|
| Background | `#f7f3ef` |
| Card bg | `white` |
| Text primary | `#2d2d2d` |
| Text secondary | `#666` |
| Text muted | `#888` |
| Accent teal | `#62b3ae` |
| CTA orange | `#eb8b6a` |
| CTA hover | `#d97a5a` |
| Border color | `#e5e0db` |
| Card radius | `12px` |
| Form card radius | `16px` |
| Font | `system-ui, -apple-system, sans-serif` |

## Commands
- `/new-giveaway {name} - {description}` — Scaffold a new giveaway page

## Deployment
Push to `main` branch → GitHub Pages auto-deploys in ~1-2 min.

Both `master` and `main` should stay in sync. Pages deploys from `main`.
