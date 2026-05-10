# MixedDrive Lab — Deployment Notes

## File Structure

```
public_html/
├── index.html              # Main landing page
├── 404.html                # Custom error page
├── .htaccess               # Apache config (HTTPS, headers, caching)
├── favicon.ico             # Multi-size legacy favicon (16/32/48/64)
├── favicon-16.png          # 16x16
├── favicon-32.png          # 32x32
├── apple-touch-icon.png    # 180x180 iOS home screen
├── og-image.png            # 1200x630 social sharing image
├── robots.txt              # Crawler rules + AI bot blocks
├── sitemap.xml             # Search engine sitemap
├── humans.txt              # /humans.txt convention
├── security.txt            # RFC 9116 security contact
└── assets/
    ├── logo-master.png     # 512x512 source icon (PNG fallback)
    └── logo-master.webp    # 512x512 source icon (modern browsers)
```

## Deployment Steps (Rumahweb cPanel)

### 1. Upload files
- Login cPanel → File Manager
- Navigate to `public_html/` (root) OR addon domain folder for `mixeddrivelab.org`
- Delete default files (`default.html`, `cgi-bin/` placeholder, etc.)
- Upload all files from this package, preserving directory structure
- IMPORTANT: `.htaccess` is hidden by default — enable "Show Hidden Files" in File Manager settings

### 2. Verify file permissions
- Files: 644
- Directories: 755
- `.htaccess`: 644

### 3. Enable SSL
- cPanel → SSL/TLS Status → AutoSSL (Let's Encrypt)
- Wait for certificate issuance (5-15 min)
- Verify https://mixeddrivelab.org loads with padlock

### 4. Setup `.com` redirect
- cPanel → Redirects
- Type: Permanent (301)
- Source: `mixeddrivelab.com` (and `www.mixeddrivelab.com`)
- Destination: `https://mixeddrivelab.org`
- Wildcard redirect: ON

### 5. Test checklist
- [ ] https://mixeddrivelab.org loads
- [ ] http:// auto-redirects to https://
- [ ] www.mixeddrivelab.org redirects to non-www
- [ ] mixeddrivelab.com redirects to .org
- [ ] /robots.txt returns content
- [ ] /sitemap.xml returns content
- [ ] /404.html accessible (and triggered by random URL)
- [ ] Favicon shows in browser tab (icon visible at 16/32px)
- [ ] OG image preview works (test: https://www.opengraph.xyz/)
- [ ] Mobile responsive (test at 375px width — hero stacks correctly)
- [ ] Hero icon animation (gentle floating) visible on desktop

### 6. Submit to search engines
- Google Search Console: https://search.google.com/search-console
  - Add property `https://mixeddrivelab.org`
  - Verify via DNS TXT record (Rumahweb DNS Zone Editor)
  - Submit sitemap: `https://mixeddrivelab.org/sitemap.xml`
- Bing Webmaster Tools: https://www.bing.com/webmasters
  - Same flow

### 7. Configure Google Workspace email
- Update MX records in Rumahweb DNS Zone Editor
- See: https://support.google.com/a/answer/140034
- Test send/receive at contact@mixeddrivelab.org

## Brand asset usage

| Asset | Use for |
|---|---|
| `assets/logo-master.png` (512px) | Master source. Use as-is for any large display. |
| `assets/logo-master.webp` (512px) | Same artwork as WebP — served preferentially via `<picture>` |
| `apple-touch-icon.png` (180px) | iOS home screen, also good for Slack/Discord avatars |
| `favicon-32.png` | Browser tab icon |
| `og-image.png` (1200x630) | Social link previews (auto-served via og:image meta) |

For external profile avatars (GitHub org, LinkedIn, etc.), export from `logo-master.png` at the size required by each platform.

## Color palette (for any external use)

```
Background:   #0a1628  (navy-deep)
Text:         #e8eef5  (ink, primary)
Text muted:   #9bafc7  (ink-muted)
Text subtle:  #5d7894  (ink-subtle)
Accent:       #5fb8a8  (teal, primary brand)
Accent warm:  #d4a574  (orange, used sparingly)
Rule:         #1f3454  (dividers, borders)
```

## Maintenance

- Update `<lastmod>` in sitemap.xml when content changes
- Re-test SSL certificate auto-renewal monthly
- Monitor uptime (free: UptimeRobot)
- Check Google Search Console weekly for crawl errors

## Updates planned

- After Paper #1 acceptance (Sep 2026): add Publications section
- After GitHub org public: add link to org in footer
- After ORCID/Scholar verified: add researcher links
