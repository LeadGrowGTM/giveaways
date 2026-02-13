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
| `extract-competitors` | `9067339` | Competitor customer targeting stack (3 scraping vectors) |
| `competitor-toolkit` | `9067339` | 3 competitor intelligence systems + playbook (legacy) |

## Form Redirects
Every Kit form MUST have a hidden redirect input:
```html
<input type="hidden" name="options[redirect_url]" value="https://giveaway.leadgrow.ai/{slug}/thank-you/">
```
Without this, Kit shows its default success page instead of our thank-you page.

Pages using ConvertKit JS (`ck.5.js`) intercept form submission via AJAX — the hidden input ensures the redirect still works.

## Design System (LeadGrow Brand Kit)
| Token | Value |
|-------|-------|
| Font | `'Figtree', system-ui, -apple-system, sans-serif` |
| Background | `#F4F3EF` (warm cream) |
| Card bg | `white` |
| Text primary | `#352922` (headings) / `#57534D` (body) |
| Text secondary | `#78716C` (stone-500) |
| Text muted | `#A8A29E` (stone-400) |
| Accent teal | `#6FAEC2` |
| Accent teal dark | `#5A9AAD` |
| CTA gradient | `linear-gradient(135deg, #C2845B 0%, #FFAF1A 100%)` |
| CTA solid | `#EB8B4B` (primary orange) |
| Border color | `#D6D3D1` (stone-300) |
| Light border | `#E7E5E4` (stone-200) |
| Dark bg | `#352922` (dark brown) |
| Footer bg | `#1C1917` (stone-900) |
| Card radius | `12px` |
| Form card radius | `16px` |
| Button radius | `75px` (pill) |
| Badge radius | `48px` |
| Shadow | `0px 4px 15px rgba(53, 41, 34, 0.2)` |

Brand kit source: `/home/del13s_ubuntu/MACH4_2/leadgrow-brand-kit/`

## Commands
- `/new-giveaway {name} - {description}` — Scaffold a new giveaway page

## Deployment
Push to `main` branch → GitHub Pages auto-deploys in ~1-2 min.

Both `master` and `main` should stay in sync. Pages deploys from `main`.
