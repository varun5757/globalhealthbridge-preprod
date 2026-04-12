# Global Health Bridge — Project Context for Claude Code

## What this project is
Global Health Bridge (globalhealthbridge.co.in) is a medical tourism facilitation 
website that connects international patients from Central Asia and Africa with 
JCI/NABH accredited hospitals in India. The company helps patients with end-to-end 
support — medical facilitation, visa assistance, travel coordination, and 
post-treatment follow-up.

**Tagline:** Across Borders. Besides You.

## Repository structure
This is the PRE-PRODUCTION repository. 
- Production repo: https://github.com/varun5757/globalhealthbridge
- Preprod repo: https://github.com/varun5757/globalhealthbridge-preprod
- Live production site: https://globalhealthbridge.co.in
- Preprod staging site: https://varun5757.github.io/globalhealthbridge-preprod/

## Files in this repo
- `index.html` — the entire website (single-page app with JS routing between pages)
- `ghb_lead_dashboard.html` — private lead management dashboard (password protected)
- `sitemap.xml` — SEO sitemap
- `robots.txt` — search engine crawler instructions

## Website architecture
The entire website is a SINGLE HTML FILE (index.html) with JavaScript-based 
page routing. There is no build process, no framework, no npm dependencies. 
Pure HTML, CSS, and vanilla JavaScript. This is intentional for simplicity 
and fast deployment.

Pages inside index.html (shown/hidden via JS):
- Home (page-home)
- Specialties overview (page-specialties)  
- Individual specialty pages (page-specialty-detail) — dynamic, data-driven
- Patient Journey (page-patientjourney)
- Partner Hospitals (page-hospitals)
- About Us (page-about)
- FAQs (page-faqs)
- Contact (page-contact)

## Lead capture system
- Form on contact page → sends to Google Apps Script → stored in Google Sheets
- Apps Script URL (hardcoded in index.html): 
  https://script.google.com/macros/s/AKfycby86Tv5fb8mszx0uKeMD8INmH5apCo9kEiZM5qxw2DocYAFgWSKuegeqvKb67sNXMVR4Q/exec
- Email notifications via EmailJS (keys hardcoded in index.html):
  - Service ID: service_4sxxdu5
  - Template ID: template_365sl2b
  - Public Key: g-BsBIZbEcAIGtzBa
- Dashboard password: GHB@Admin2025
- Apps Script lives on Google's servers — NOT in this repo — never touch it

## Contact details (hardcoded throughout)
- Phone/WhatsApp: +91 98716 15884
- Email: globalhealthbridge.in@gmail.com
- Domain: globalhealthbridge.co.in
- WhatsApp link: https://wa.me/919871615884

## Social media
- Facebook: https://www.facebook.com/people/Global-Health-Bridge/61578458949745/
- Twitter/X: https://x.com/GlobalHealthBrg
- Instagram: https://www.instagram.com/globalhealthbridge.in/

## Partner hospitals
1. BLK-Max Super Speciality Hospital, Patel Nagar, New Delhi (Max Healthcare)
2. Max Hospital Saket, South Delhi (Max Healthcare)
3. Max Hospital Dwarka, South-West Delhi (Max Healthcare)
4. Fortis Flt. Lt. Rajan Dhall Hospital, Vasant Kunj, South Delhi (Fortis)
5. Fortis Escorts Heart Institute, Okhla Road, South Delhi (Fortis)

## Medical specialties covered
Cardiology, Oncology, Orthopaedics, Organ Transplant, Infertility & IVF, 
Urology & Surgery

## Design system
- Fonts: Playfair Display (display/headings), Inter (body)
- Primary color: Teal #0d6b55 (--teal)
- Secondary color: Blue #1a5fa8 (--blue)
- Background: White #ffffff and neutral #f7f9fc
- Dark section: Deep navy #07192e / #0a2744
- All CSS uses custom properties defined in :root
- Mobile-first responsive, breakpoints at 1024px, 768px, 480px

## Images
All images are Unsplash URLs (no local image files). They use lazy loading 
(loading="lazy") and are served from Unsplash's CDN. No image files are 
stored in this repository.

## SEO
- Full meta tags, Open Graph, Twitter Cards in <head>
- Schema markup: MedicalBusiness, FAQPage, Organization
- sitemap.xml submitted to Google Search Console
- robots.txt blocks dashboard from indexing

## Deployment workflow
1. Make changes to files in THIS preprod repo
2. Commit and push to preprod
3. Varun reviews at: https://varun5757.github.io/globalhealthbridge-preprod/
4. When approved, Varun manually copies files to production repo
5. Production: https://github.com/varun5757/globalhealthbridge

## Important rules
- NEVER push to the production repo (globalhealthbridge) — preprod only
- NEVER modify the Apps Script — it lives on Google's servers
- NEVER remove or change EmailJS keys, Apps Script URL, or contact details
  without explicit instruction
- ALWAYS test that the lead form fields have correct IDs before pushing
- When making CSS changes, use existing CSS variables — don't add new colors
- Keep the single-file architecture — don't split into multiple HTML/CSS/JS files
- Any new page must follow the existing page routing pattern (showPage function)

## How to make changes
When Varun asks for changes:
1. Edit the relevant section in index.html
2. Verify nothing else broke (grep for any changed IDs/classes)
3. git add . && git commit -m "clear description of change"
4. git push origin main
5. Tell Varun the preprod URL to review
