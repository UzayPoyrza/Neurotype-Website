# Full SEO Audit Report: neurotypeapp.com

**Audit Date:** 2026-02-25
**Domain:** https://www.neurotypeapp.com
**Business Type:** SaaS / Health & Wellness App (Pre-launch, Waitlist Stage)
**Pages Audited:** 4 indexable pages + 1 utility page
**Hosted On:** Vercel (static HTML)

---

## SEO Health Score: 34 / 100

| Category | Weight | Score | Weighted |
|----------|--------|-------|----------|
| Technical SEO | 25% | 28/100 | 7.0 |
| Content Quality | 25% | 52/100 | 13.0 |
| On-Page SEO | 20% | 40/100 | 8.0 |
| Schema / Structured Data | 10% | 0/100 | 0.0 |
| Performance (CWV) | 10% | 55/100 | 5.5 |
| Images | 5% | 10/100 | 0.5 |
| AI Search Readiness | 5% | 15/100 | 0.75 |
| **Total** | **100%** | | **34.75** |

---

## Executive Summary

### Top 5 Critical Issues
1. **No robots.txt** -- Returns 404. Search engines have no crawl guidance.
2. **No sitemap.xml** -- Returns 404. Search engines must discover pages through links only.
3. **No canonical tags** -- None on any page. Risk of duplicate content across URL variants.
4. **No JSON-LD structured data** -- Zero schema markup. Missing rich result opportunities (Organization, SoftwareApplication, BreadcrumbList).
5. **OG URL domain mismatch** -- `og:url` points to `https://neurotype.app` but site is at `https://www.neurotypeapp.com`.

### Top 5 Quick Wins
1. Add `robots.txt` and `sitemap.xml` to `/public` (30 min)
2. Add canonical tags to all pages (15 min)
3. Fix OG URL to correct domain (5 min)
4. Fix legal page contact emails from `contact@launchspace.org` to `contact@neurotypeapp.com` (10 min)
5. Add JSON-LD Organization + SoftwareApplication schema to homepage (30 min)

---

## 1. Technical SEO

### 1.1 Crawlability

| Check | Status | Details |
|-------|--------|---------|
| robots.txt | FAIL | Returns 404 |
| sitemap.xml | FAIL | Returns 404 |
| HTML lang attribute | PASS | `<html lang="en">` on all pages |
| Mobile viewport | PASS | `<meta name="viewport" content="width=device-width, initial-scale=1.0">` |
| Responsive design | PASS | Media queries for 768px, 640px, 480px, 600px breakpoints |
| JavaScript rendering | PASS | Content in HTML, JS only handles UI interactions |
| Internal links | PARTIAL | Footer links use `.html` extension (e.g., `/terms-of-service.html`) |

### 1.2 Indexability

| Check | Status | Details |
|-------|--------|---------|
| Canonical tags | FAIL | Missing on ALL pages |
| Meta robots | ABSENT | No meta robots tags (defaults to index,follow -- OK) |
| noindex on utility pages | FAIL | `/oauth-redirect.html` should have `noindex` |
| X-Robots-Tag header | ABSENT | Not configured in vercel.json |

### 1.3 Security

| Check | Status | Details |
|-------|--------|---------|
| HTTPS | PASS | Site served over HTTPS via Vercel |
| Content-Security-Policy | FAIL | Not configured |
| X-Content-Type-Options | UNKNOWN | Not configured in vercel.json (Vercel may add defaults) |
| X-Frame-Options | UNKNOWN | Not configured in vercel.json |
| Strict-Transport-Security | UNKNOWN | Vercel may add HSTS by default |

### 1.4 URL Structure

| Page | URL | Issue |
|------|-----|-------|
| Homepage | `/` | OK |
| Privacy Policy | `/privacy-policy.html` | `.html` extension (minor; Vercel can serve without it) |
| Terms of Service | `/terms-of-service.html` | `.html` extension |
| Consumer Health Data | `/consumer-health-data-privacy-policy.html` | `.html` extension |
| OAuth Redirect | `/oauth-redirect` | Rewrite configured in vercel.json -- OK |

**Recommendation:** Configure Vercel `cleanUrls: true` in vercel.json to serve pages without `.html` extensions. Update internal links to match.

### 1.5 Domain Consistency

**Critical Issue:** The `og:url` meta tag uses `https://neurotype.app` while the live site is at `https://www.neurotypeapp.com`. This creates confusion for social platforms and could cause URL fragmentation.

**Action:** Update `og:url` to `https://www.neurotypeapp.com/` and add canonical tags pointing to the correct domain.

---

## 2. Content Quality

### 2.1 E-E-A-T Assessment (Your Money, Your Life)

This site is in the **YMYL (Your Money, Your Life)** category because it addresses mental health conditions (ADHD, anxiety, depression, PTSD). Google holds YMYL content to higher E-E-A-T standards.

| Signal | Status | Score | Notes |
|--------|--------|-------|-------|
| **Experience** | WEAK | 2/5 | No user testimonials, case studies, or first-person accounts |
| **Expertise** | WEAK | 2/5 | No team page, no author bios, no credentials listed, no advisory board |
| **Authoritativeness** | MODERATE | 3/5 | Clinical study citations present (JAMA Psychiatry, Teasdale et al., Mitchell et al.) |
| **Trustworthiness** | MODERATE | 3/5 | Medical disclaimer present, 988 crisis link, privacy policies, but no trust badges, no BBB, no app store presence |

**Key E-E-A-T Gaps:**
- No "About" or "Team" page -- critical for YMYL health content
- No named individuals (founder, medical advisor, researchers)
- No professional credentials displayed
- No third-party endorsements or partnerships
- No social media presence linked from site
- Clinical citations are good but need proper attribution with DOI links

### 2.2 Content Depth

| Page | Est. Word Count | Assessment |
|------|----------------|------------|
| Homepage | ~600 visible words | Light for YMYL -- adequate for landing page, thin for SEO |
| Privacy Policy | ~3,000 words | Adequate |
| Terms of Service | ~4,000 words | Adequate |
| Consumer Health Data | ~2,500 words | Adequate |

**Homepage Content Sections:**
- Hero: Strong hook, clear value proposition
- Comparison (vs generic apps): Good differentiator
- How It Works (3 steps): Clear, interactive demos
- Modules (11 listed): Good breadth coverage
- Evidence (3 study citations): Needs strengthening
- Waitlist CTA: Functional
- Medical disclaimer + crisis resources: Good

### 2.3 YMYL Compliance

| Check | Status |
|-------|--------|
| Medical disclaimer | PASS -- "not a medical device and is not a substitute for professional care" |
| Crisis resources | PASS -- 988 Suicide & Crisis Lifeline linked |
| Professional referral language | PASS -- "We encourage working with qualified professionals" |
| No diagnostic claims | PASS -- Carefully worded as "evidence-informed" not "clinically proven" |
| Terms of Service health disclaimers | PASS -- Extensive Section 5 covering health, safety, and medical disclaimer |

### 2.4 Readability

- Font: Plus Jakarta Sans (highly legible)
- Body text: 1rem / line-height 1.6 (good)
- Contrast: Primary text (#1C1C1E) on light background (#F2F2F7) -- good
- Evidence section: Light text on dark background -- adequate contrast
- Mobile: Responsive with appropriate font scaling via clamp()

---

## 3. On-Page SEO

### 3.1 Title Tags

| Page | Title | Length | Assessment |
|------|-------|--------|------------|
| Homepage | "Neurotype -- Meditation, Prescribed for Your Brain" | 52 chars | GOOD -- Under 60 chars, keyword-rich |
| Privacy Policy | "Neurotype Privacy Policy" | 24 chars | OK -- Basic but functional |
| Terms of Service | "Neurotype Terms of Service" | 26 chars | OK |
| Consumer Health Data | "Neurotype Consumer Health Data Privacy Policy" | 46 chars | OK |

### 3.2 Meta Descriptions

| Page | Description | Length | Assessment |
|------|-------------|--------|------------|
| Homepage | "Neurotype personalizes meditation by mental health profile..." | 159 chars | GOOD -- Keyword-rich, includes CTA |
| Privacy Policy | "Privacy Policy for Neurotype" | 28 chars | WEAK -- Too short, no value prop |
| Terms of Service | "Terms of Service for Neurotype" | 30 chars | WEAK -- Too short |
| Consumer Health Data | "Consumer Health Data Privacy Policy for Neurotype" | 49 chars | WEAK -- Too short |

### 3.3 Heading Structure (Homepage)

```
H1: "Meditation, prescribed for your brain." (1 -- correct, single H1)
  H2: "Stop browsing. Start a plan."
  H2: "How It Works"
  H2: "Three steps. Zero guesswork."  <-- duplicate intent with "How It Works"
    H3: "Tell us about your brain"
    H3: "Get matched techniques"
    H3: "Check in. Adapt. Improve."
  H2: "Backed by Research"
  H2: "Compare to clinical studies."  <-- duplicate intent with "Backed by Research"
    H3: "Anxiety Symptoms"
    H3: "Depression Relapse"
    H3: "ADHD & Focus"
  H2: "Get Early Access"
  H2: "Your brain isn't average. Your meditation shouldn't be either."
    H3: "You're on the list." (hidden success state)
```

**Issues:**
- Two pairs of H2s with overlapping intent ("How It Works" + "Three steps..." and "Backed by Research" + "Compare to clinical studies...")
- Consider consolidating to single H2 per section

### 3.4 Internal Linking

| From | To | Link Text | Issue |
|------|----|-----------|-------|
| Homepage nav | #how-it-works | "How It Works" | OK (anchor) |
| Homepage nav | #comparison | "Features" | OK (anchor) |
| Homepage nav | #modules | "Modules" | OK (anchor) |
| Homepage footer | /terms-of-service.html | "Terms of Service" | Uses .html extension |
| Homepage footer | /privacy-policy.html | "Privacy Policy" | Uses .html extension |
| Homepage footer | /consumer-health-data-privacy-policy.html | "Consumer Health Data Privacy Policy" | Uses .html extension |
| Legal pages | / | Logo | OK |
| Legal pages | Each other via footer | Same footer structure | OK |

**Missing cross-links:** Legal pages don't link back to the homepage in the body content (only via logo and footer). No "Back to home" CTA.

### 3.5 Open Graph & Social Sharing

| Tag | Homepage | Legal Pages |
|-----|----------|-------------|
| og:title | PRESENT | MISSING |
| og:description | PRESENT | MISSING |
| og:type | PRESENT ("website") | MISSING |
| og:url | PRESENT but WRONG domain | MISSING |
| og:image | MISSING | MISSING |
| og:site_name | PRESENT | MISSING |
| twitter:card | PRESENT | MISSING |
| twitter:title | PRESENT | MISSING |
| twitter:description | PRESENT | MISSING |
| twitter:image | MISSING | MISSING |

**Critical:** No `og:image` or `twitter:image` anywhere. Social shares will have no preview image.

---

## 4. Schema & Structured Data

### Current State: ZERO structured data

No JSON-LD, Microdata, or RDFa markup exists on any page.

### Recommended Schema Types

| Type | Page | Rich Result Eligible | Priority |
|------|------|---------------------|----------|
| Organization | Homepage | Yes (Knowledge Panel) | HIGH |
| WebSite | Homepage | Yes (Sitelinks) | HIGH |
| SoftwareApplication | Homepage | Yes (App details) | HIGH |
| WebPage | All pages | No (foundational) | MEDIUM |
| BreadcrumbList | Legal pages | Yes (Breadcrumb trails) | MEDIUM |

### Recommended Homepage JSON-LD

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://www.neurotypeapp.com/#organization",
      "name": "Neurotype",
      "url": "https://www.neurotypeapp.com",
      "email": "contact@neurotypeapp.com",
      "description": "Neurotype personalizes meditation by mental health profile with 198+ evidence-informed sessions across 11 modules.",
      "contactPoint": {
        "@type": "ContactPoint",
        "email": "contact@neurotypeapp.com",
        "contactType": "customer support"
      }
    },
    {
      "@type": "WebSite",
      "@id": "https://www.neurotypeapp.com/#website",
      "name": "Neurotype",
      "url": "https://www.neurotypeapp.com",
      "publisher": { "@id": "https://www.neurotypeapp.com/#organization" }
    },
    {
      "@type": "SoftwareApplication",
      "name": "Neurotype",
      "applicationCategory": "HealthApplication",
      "operatingSystem": "iOS, Android",
      "description": "The first meditation app that matches neuroscience-backed techniques to your mental health profile.",
      "offers": {
        "@type": "Offer",
        "availability": "https://schema.org/PreOrder",
        "price": "0",
        "priceCurrency": "USD"
      },
      "featureList": [
        "Personalized meditation by mental health profile",
        "198+ evidence-informed guided sessions",
        "11 mental health modules",
        "Adaptive technique matching",
        "Post-session check-ins and progress tracking"
      ]
    }
  ]
}
```

---

## 5. Performance

### 5.1 Page Size

| Page | Raw Size | Notes |
|------|----------|-------|
| index.html | 87,908 bytes (~86 KB) | All inline (CSS + HTML + JS + SVGs) |
| privacy-policy.html | 18,992 bytes (~19 KB) | |
| terms-of-service.html | 23,195 bytes (~19 KB) | |
| consumer-health-data.html | 16,974 bytes (~17 KB) | |

### 5.2 Resource Loading

| Resource | Type | Blocking? | Size |
|----------|------|-----------|------|
| Google Fonts CSS | External CSS | YES -- render-blocking | ~40 KB |
| Instrument Serif | Font file | Swapped (`display=swap`) | ~25 KB |
| Plus Jakarta Sans (7 weights) | Font file | Swapped | ~150 KB |
| Inline CSS | `<style>` block | No (inline) | ~28 KB |
| Inline JS | `<script>` | No (at bottom of body) | ~3 KB |

### 5.3 Estimated Core Web Vitals

| Metric | Estimate | Target | Status |
|--------|----------|--------|--------|
| **LCP** | ~1.5-2.5s | < 2.5s | LIKELY GOOD (depends on font load) |
| **INP** | < 100ms | < 200ms | GOOD (minimal JS interaction) |
| **CLS** | 0.05-0.15 | < 0.1 | AT RISK (font swap may cause layout shift) |

### 5.4 Performance Issues

1. **Google Fonts are render-blocking**: The CSS link tag blocks rendering. Use `font-display: optional` or self-host fonts.
2. **7 font weights loaded**: Plus Jakarta Sans loads weights 300-800. Consider reducing to 3-4 weights actually used.
3. **Large inline SVGs**: Multiple complex SVGs are inline in HTML, increasing document size.
4. **No resource compression configured**: vercel.json doesn't set compression headers (Vercel enables gzip/brotli by default, but explicit config is better).
5. **No preload for critical fonts**: Add `<link rel="preload">` for the most critical font files.

### 5.5 Performance Strengths

- No external JS libraries
- No images to load (all CSS/SVG)
- Minimal JavaScript (~3 KB, all vanilla)
- IntersectionObserver used efficiently (unobserves after trigger)
- Passive scroll listener
- `preconnect` hints for Google Fonts already present

---

## 6. Images

### Current State

**No raster images exist on the site.** All visual elements are CSS-based or inline SVGs.

| Check | Status |
|-------|--------|
| Images with alt text | N/A -- no `<img>` tags |
| Favicon | MISSING -- no `<link rel="icon">` |
| Apple touch icon | MISSING |
| OG image | MISSING -- no `og:image` tag |
| Twitter image | MISSING -- no `twitter:image` tag |

**Critical:** The site has no social sharing image (og:image). When shared on social media (Twitter, LinkedIn, Slack, iMessage), there will be no preview image -- significantly reducing click-through rates.

**Recommendation:** Create a branded OG image (1200x630px) and add:
```html
<meta property="og:image" content="https://www.neurotypeapp.com/og-image.png">
<meta name="twitter:image" content="https://www.neurotypeapp.com/og-image.png">
```

---

## 7. AI Search Readiness

### 7.1 Citability Score: LOW

| Factor | Status | Notes |
|--------|--------|-------|
| Clear factual claims | PARTIAL | Clinical study data present but could be more structured |
| Source attribution | WEAK | Studies cited by journal name only, no DOI links |
| Structured content | MODERATE | Clear sections, but no FAQ, no definition lists |
| Entity recognition | WEAK | No schema markup, no named entities (people, institutions) |
| Content freshness | UNKNOWN | No dates on content, no blog/news section |
| AI crawler accessibility | UNKNOWN | No robots.txt to check AI bot rules |
| llms.txt | MISSING | No llms.txt file for AI crawler guidance |

### 7.2 Recommendations for AI Visibility

1. **Add llms.txt** to guide AI crawlers on content structure
2. **Add DOI links** to all cited studies for verifiability
3. **Structure claims as attributable passages**: "According to JAMA Psychiatry (2023), mindfulness-based programs reduced anxiety severity by 78%"
4. **Add an About/Team page** with named experts -- AI models cite authoritative named sources
5. **Consider a blog/resources section** with deeper educational content on meditation for specific conditions

---

## 8. Additional Findings

### 8.1 CRITICAL: Wrong Contact Email in Legal Pages

The legal subpages reference `contact@launchspace.org` in multiple places instead of `contact@neurotypeapp.com`:

| File | Lines | Current Email |
|------|-------|---------------|
| terms-of-service.html | 558, 559 | contact@launchspace.org |
| privacy-policy.html | 303, 304, 403, 430, 472 | contact@launchspace.org |
| consumer-health-data-privacy-policy.html | 374, 470, 486, 521 | contact@launchspace.org |

**This must be fixed immediately** -- it creates a trust issue and may violate privacy law requirements to provide accurate contact information.

### 8.2 Waitlist Form Not Connected

The waitlist form submission (line 1500-1501 of index.html) uses a `setTimeout` to fake a submission:
```javascript
setTimeout(function() { fields.classList.add('hide'); success.classList.add('show'); }, 700);
```
No actual API call is made. Emails are not being collected.

### 8.3 Missing `noindex` on OAuth Redirect

`/oauth-redirect.html` is a utility page for app authentication. It should have `<meta name="robots" content="noindex, nofollow">` to prevent indexing.

### 8.4 No Favicon

No `<link rel="icon">` or `<link rel="apple-touch-icon">` tags exist. The browser tab and bookmarks will show a generic icon.

---

## Scoring Breakdown

### Technical SEO: 28/100
- (-20) No robots.txt
- (-20) No sitemap.xml
- (-15) No canonical tags
- (-10) OG URL mismatch
- (-5) No noindex on utility page
- (-2) .html extensions in URLs
- (+15) HTTPS
- (+10) Mobile viewport
- (+5) Responsive design
- (+5) HTML lang attribute
- (+5) Clean HTML, no render-blocking JS

### Content Quality: 52/100
- (+15) Strong value proposition and messaging
- (+12) Clinical study citations
- (+10) Medical disclaimer + crisis resources
- (+8) YMYL-compliant language
- (+7) Clear heading structure
- (-10) No About/Team page (critical for YMYL)
- (-8) No expert credentials
- (-5) Thin homepage content (~600 words)
- (-5) No user testimonials or social proof
- (-3) Study citations lack DOI links

### On-Page SEO: 40/100
- (+15) Good homepage title tag
- (+10) Good homepage meta description
- (+8) Single H1, logical heading hierarchy
- (+7) Internal linking via footer
- (-10) No OG/Twitter images
- (-8) Missing OG tags on subpages
- (-5) Weak meta descriptions on legal pages
- (-5) Duplicate-intent H2 pairs
- (-3) Footer links use .html extensions
- (-3) Wrong contact email in legal pages

### Schema / Structured Data: 0/100
- Zero markup of any kind

### Performance: 55/100
- (+20) No external JS libraries
- (+15) Small total page size
- (+10) Efficient IntersectionObserver usage
- (+5) Passive scroll listeners
- (+5) Font display swap
- (-15) Render-blocking Google Fonts CSS
- (-10) Too many font weights
- (-5) No preload for critical resources
- (-5) Large inline SVGs

### Images: 10/100
- (-40) No social sharing image (og:image)
- (-25) No favicon
- (-15) No apple-touch-icon
- (+10) No image performance issues (none to optimize)

### AI Search Readiness: 15/100
- (+5) Clinical studies referenced
- (+5) Clear factual claims
- (+5) YMYL disclaimers
- (-15) No llms.txt
- (-10) No schema markup
- (-10) No named experts/entities
- (-8) No DOI links on citations
- (-5) No robots.txt for AI crawler guidance
