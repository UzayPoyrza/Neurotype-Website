# SEO Action Plan: neurotypeapp.com

**Current Score: 34/100**
**Target Score: 70+ / 100**

---

## CRITICAL (Fix Immediately)

### 1. Create robots.txt
**Impact:** Crawlability | **Effort:** 5 min
```
Create /public/robots.txt:

User-agent: *
Allow: /
Disallow: /oauth-redirect

Sitemap: https://www.neurotypeapp.com/sitemap.xml
```

### 2. Create sitemap.xml
**Impact:** Crawlability | **Effort:** 10 min
```xml
Create /public/sitemap.xml:

<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://www.neurotypeapp.com/</loc>
    <lastmod>2026-02-25</lastmod>
  </url>
  <url>
    <loc>https://www.neurotypeapp.com/privacy-policy</loc>
    <lastmod>2026-02-25</lastmod>
  </url>
  <url>
    <loc>https://www.neurotypeapp.com/terms-of-service</loc>
    <lastmod>2026-02-25</lastmod>
  </url>
  <url>
    <loc>https://www.neurotypeapp.com/consumer-health-data-privacy-policy</loc>
    <lastmod>2026-02-25</lastmod>
  </url>
</urlset>
```

### 3. Add canonical tags to all pages
**Impact:** Indexability | **Effort:** 15 min

Add to `<head>` of each page:
- index.html: `<link rel="canonical" href="https://www.neurotypeapp.com/">`
- privacy-policy.html: `<link rel="canonical" href="https://www.neurotypeapp.com/privacy-policy">`
- terms-of-service.html: `<link rel="canonical" href="https://www.neurotypeapp.com/terms-of-service">`
- consumer-health-data-privacy-policy.html: `<link rel="canonical" href="https://www.neurotypeapp.com/consumer-health-data-privacy-policy">`

### 4. Fix OG URL domain mismatch
**Impact:** Social sharing / URL consistency | **Effort:** 5 min

In `index.html` line 16, change:
```html
<meta property="og:url" content="https://neurotype.app">
```
To:
```html
<meta property="og:url" content="https://www.neurotypeapp.com/">
```

### 5. Fix contact email in legal pages
**Impact:** Trust / Legal compliance | **Effort:** 10 min

Replace ALL instances of `contact@launchspace.org` with `contact@neurotypeapp.com` in:
- privacy-policy.html (lines 303, 304, 403, 430, 472)
- terms-of-service.html (lines 558, 559)
- consumer-health-data-privacy-policy.html (lines 374, 470, 486, 521)

### 6. Add noindex to OAuth redirect page
**Impact:** Indexability | **Effort:** 2 min

Add to `<head>` of oauth-redirect.html:
```html
<meta name="robots" content="noindex, nofollow">
```

---

## HIGH (Fix Within 1 Week)

### 7. Add JSON-LD structured data
**Impact:** Rich results eligibility | **Effort:** 30 min

Add the Organization + WebSite + SoftwareApplication JSON-LD block to the homepage `<head>` (see FULL-AUDIT-REPORT.md Section 4 for complete code).

Add WebPage + BreadcrumbList JSON-LD to each legal subpage.

### 8. Create and add OG image
**Impact:** Social sharing CTR | **Effort:** 1-2 hours

Create a branded 1200x630px image and add to all pages:
```html
<meta property="og:image" content="https://www.neurotypeapp.com/og-image.png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta name="twitter:image" content="https://www.neurotypeapp.com/og-image.png">
```

### 9. Add favicon and apple-touch-icon
**Impact:** Branding / UX | **Effort:** 30 min

Create favicon files and add to `<head>` of all pages:
```html
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
```

### 10. Add OG/Twitter tags to legal pages
**Impact:** Social sharing consistency | **Effort:** 15 min

Add basic `og:title`, `og:description`, `og:type`, `og:url` to each legal subpage.

### 11. Connect waitlist form to actual backend
**Impact:** Lead capture (business-critical) | **Effort:** 1-4 hours

The current form fakes submission with `setTimeout`. Connect to an actual API (e.g., Supabase, Airtable, Mailchimp, or custom endpoint).

---

## MEDIUM (Fix Within 1 Month)

### 12. Create an About/Team page
**Impact:** E-E-A-T for YMYL | **Effort:** 4-8 hours

For a health-related app, Google expects to see:
- Founder/team bios with credentials
- Medical advisory board (if applicable)
- Company mission and methodology
- Contact information

### 13. Add DOI links to clinical study citations
**Impact:** E-E-A-T / AI citability | **Effort:** 30 min

Update the evidence section to include actual DOI links:
- JAMA Psychiatry, 2023 -> link to actual paper
- Teasdale et al., JCCP -> link to actual paper
- Mitchell et al., J Atten Disord -> link to actual paper

### 14. Optimize Google Fonts loading
**Impact:** Performance (LCP, CLS) | **Effort:** 1-2 hours

Options (pick one):
- **Self-host fonts**: Download and serve from own domain (eliminates external request)
- **Preload critical font**: Add `<link rel="preload" as="font" type="font/woff2" href="..." crossorigin>`
- **Reduce weights**: Currently loading 7 weights (300-800). Audit actual usage and reduce to 3-4.

### 15. Enable cleanUrls in Vercel
**Impact:** URL consistency | **Effort:** 5 min

Add to vercel.json:
```json
"cleanUrls": true
```
Then update all internal links to remove `.html` extensions.

### 16. Improve meta descriptions on legal pages
**Impact:** CTR in search results | **Effort:** 15 min

Replace generic descriptions with more descriptive ones:
- Privacy Policy: "Learn how Neurotype collects, uses, and protects your personal and health data. Read our full privacy policy."
- Terms of Service: "Read the terms of service for Neurotype, the personalized meditation app. Covers account usage, health disclaimers, and your rights."
- Consumer Health Data: "Neurotype's consumer health data privacy policy. Learn how we handle health-related information under applicable state laws."

### 17. Add security headers to vercel.json
**Impact:** Security / Trust signals | **Effort:** 15 min

```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        { "key": "X-Content-Type-Options", "value": "nosniff" },
        { "key": "X-Frame-Options", "value": "DENY" },
        { "key": "Referrer-Policy", "value": "strict-origin-when-cross-origin" },
        { "key": "Permissions-Policy", "value": "camera=(), microphone=(), geolocation=()" }
      ]
    }
  ]
}
```

---

## LOW (Backlog)

### 18. Add llms.txt for AI crawler guidance
**Impact:** AI search visibility | **Effort:** 15 min

### 19. Create a blog/resources section
**Impact:** Content depth / Long-tail keywords | **Effort:** Ongoing

Topics to target:
- "Meditation for ADHD: what works and what doesn't"
- "How personalized meditation compares to generic apps"
- "Mindfulness techniques for anxiety: a research summary"
- "Movement-based meditation for neurodivergent minds"

### 20. Add user testimonials / social proof
**Impact:** E-E-A-T / Conversion | **Effort:** Depends on beta testers

### 21. Submit to Google Search Console and Bing Webmaster Tools
**Impact:** Crawl monitoring | **Effort:** 30 min

### 22. Consolidate duplicate-intent H2 headings
**Impact:** On-page SEO | **Effort:** 10 min

Merge:
- "How It Works" + "Three steps. Zero guesswork." -> Single H2
- "Backed by Research" + "Compare to clinical studies." -> Single H2

---

## Implementation Priority Matrix

```
                    HIGH IMPACT
                        |
    [1] robots.txt      |  [7] JSON-LD schema
    [2] sitemap.xml     |  [8] OG image
    [3] canonical tags  |  [12] About page
    [4] Fix OG URL      |
    [5] Fix emails      |  [11] Connect form
    [6] noindex oauth   |  [13] DOI links
                        |
LOW EFFORT ------------|-------------- HIGH EFFORT
                        |
    [15] cleanUrls      |  [14] Font optimization
    [16] meta descs     |  [19] Blog section
    [17] security hdrs  |  [20] Testimonials
    [10] OG legal pages |
    [22] Fix H2s        |
                        |
                    LOW IMPACT
```

**Estimated time for Critical + High items: ~4-6 hours**
**Expected score improvement: 34 -> 65-75 / 100**
