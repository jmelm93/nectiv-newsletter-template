# Nectiv Email Templates - Project Guide

## Repository Overview
This repository contains HTML email templates for Nectiv's weekly newsletter "The GEO Insider" - a newsletter focused on SEO and Generative Engine Optimization (GEO) insights for AI-powered search strategies.

## Core Purpose
Create and maintain professional, branded email templates that:
- Deliver weekly SEO and GEO insights to subscribers
- Work within Kit.com's (formerly ConvertKit) platform limitations
- Maintain consistent Nectiv branding
- Optimize for maximum email client compatibility

## 🎨 Nectiv Brand Color Theme

### Primary Colors
- **Primary Blue**: `#0066FF` - Used for accents, footer background, links, and the Nectiv dot
- **Black**: `#000000` - Headers, primary buttons, CTA backgrounds, section borders
- **White**: `#FFFFFF` - Text on dark backgrounds, button text

### Secondary Colors
- **Dark Background**: `#1A1A1A` - Main email wrapper background
- **Header Background**: `#2A2A2A` - Newsletter header section
- **Text Dark**: `#1A1A1A` - Primary text color
- **Text Light**: `#666666` - Descriptions and secondary text
- **Border Gray**: `#E5E5E5` - Section dividers and borders

### Accent Colors
- **Success Green**: `#00D084` - "New" badges
- **Alert Red**: `#FF6B6B` - "Trending" badges  
- **Light Gray**: `#F8F8F8` - Background for tool spotlight sections
- **Light Blue**: `#F0F7FF` - Optional light background

### Typography
- **Section Headers**: 20px, font-weight: 700
- **Article Titles**: 18px, font-weight: 600
- **Body Text**: 14px, line-height: 22px
- **Small Text**: 12px (badges, footer)
- **Font Family**: Arial, sans-serif (email-safe)

## 📁 File Structure
```
/nectiv-email-templates/
├── CLAUDE.md                           # This guide
├── Kit.com Template Creation - Everything to Know.md  # Technical documentation
├── weekly-workflow-guide.md            # Step-by-step workflow
└── weekly_newsletter/
    ├── nectiv-email-template.html      # Main template (one-time import to Kit.com)
    └── weekly-content-template.html    # Weekly content snippets
```

## 🔧 Template System Architecture

### Two-File System (Kit.com Workaround)
Due to Kit.com's limitation of only ONE editable content area via `{{ message_content }}`:

1. **Main Template** (`nectiv-email-template.html`)
   - Contains fixed header with Nectiv branding
   - Welcome message with personalization
   - Single `{{ message_content }}` variable for editable content
   - Fixed CTA section
   - Fixed footer with compliance links

2. **Weekly Content Template** (`weekly-content-template.html`)
   - Modular HTML snippets for weekly content
   - Pre-formatted sections that get pasted into Kit.com editor
   - All content uses inline CSS for compatibility

## 📋 Newsletter Content Sections

### Standard Weekly Sections:
1. **🚀 AI Search & GEO News** (5 items)
   - Headlines with links
   - Brief descriptions (100-150 chars)
   - Optional badges (Trending/New)

2. **💡 SEO & GEO Insights** (3-4 items)
   - Tactical tips and strategies
   - In-depth analysis links

3. **🛠️ Tool Spotlight** (1 featured tool)
   - Tool name and description
   - Key features list
   - Pricing information
   - CTA button

4. **📚 Resources & Guides** (3 items)
   - Downloadable resources
   - Guides and checklists
   - Tools and calculators

## ⚠️ Kit.com Requirements & Limitations

### Mandatory Variables (Template won't work without these):
```html
{{ message_content }}        <!-- Where email content goes -->
{{ unsubscribe_link }}      <!-- Or {{ unsubscribe_url }} -->
{{ address }}               <!-- Physical address for CAN-SPAM -->
```

### Optional Personalization:
```html
{{ subscriber.first_name | default: "SEO Professional" }}
{{ subscriber_preferences_url }}
{{ subscriber.custom_field_name }}
```

### Platform Limitations:
- Only ONE editable content area
- No multiple independent sections
- No custom variables or loops
- Cannot edit HTML templates in visual editor
- No JavaScript support
- No external CSS files
- No video elements
- No forms
- Maximum email size: 102KB

## 📝 HTML Email Best Practices

### Always Use:
- ✅ Table-based layouts (not divs)
- ✅ Inline CSS for all styling
- ✅ Absolute URLs (https://...)
- ✅ Maximum width of 600px
- ✅ Alt text for images
- ✅ Web-safe fonts
- ✅ MSO conditional comments for Outlook

### Never Use:
- ❌ JavaScript
- ❌ External stylesheets
- ❌ CSS positioning
- ❌ Placeholder URLs like `[LINK]`
- ❌ Video elements
- ❌ Forms
- ❌ Complex CSS selectors

## 🚀 Weekly Workflow

### Initial Setup (One Time):
1. Import `nectiv-email-template.html` to Kit.com
2. Save as "Nectiv GEO Insider - Weekly Template"
3. Optionally set as default template

### Weekly Newsletter Creation:
1. **Gather Content:**
   - 5 AI/GEO news items
   - 3 SEO insights
   - 1 tool to spotlight
   - 3 resources/guides

2. **Edit Content Template:**
   - Open `weekly-content-template.html`
   - Replace all placeholders
   - Update all URLs to real links
   - Add UTM parameters: `?utm_source=newsletter&utm_medium=email&utm_campaign=geo-insider-week-XX`

3. **Create in Kit.com:**
   - New Broadcast → Select template
   - Paste edited HTML into content area
   - Set subject line (30-50 chars)
   - Set preheader text (50-100 chars)

4. **Test & Send:**
   - Preview in Kit.com
   - Send test emails
   - Check all links
   - Schedule for Tuesday-Thursday, 10am EST

## 📊 Performance Targets
- **Open Rate**: 35-45%
- **Click Rate**: 8-12%
- **Unsubscribe Rate**: <0.5%
- **Bounce Rate**: <2%

## 🔍 Testing Checklist
- [ ] All placeholders replaced
- [ ] Links tested and working
- [ ] Mobile responsiveness verified
- [ ] Dark mode compatibility checked
- [ ] Personalization fallbacks work
- [ ] Unsubscribe link present
- [ ] Physical address included
- [ ] Under 102KB total size

## 💡 Important Reminders

### Content Guidelines:
- Headlines: Keep under 80 characters
- Descriptions: 100-150 characters optimal
- Focus on value and benefits
- Use action words and keywords (AI, SEO, GEO, ChatGPT)
- Create urgency when appropriate

### Technical Notes:
- Always wrap `{{ message_content }}` with proper padding container
- Use valid URLs (never brackets or placeholders)
- Test with subscribers who have/lack personalization fields
- Keep modular structure for easy section management
- Save successful emails for reference

### Common Issues & Solutions:
- **Content flush against edges**: Ensure padding wrapper around `{{ message_content }}`
- **Links not working**: Use full URLs including https://
- **Template rejected**: Verify all required variables present
- **Personalization failing**: Check liquid tag syntax exactly

## 🎯 Brand Voice & Messaging
- Professional but approachable
- Focus on actionable insights
- Emphasize practical value
- Position Nectiv as GEO thought leader
- Help subscribers succeed with AI-powered search

## 📈 A/B Testing Ideas
- Subject line variations (questions vs statements)
- Number of content items per section
- CTA button text and colors
- Section order
- Badge usage and placement

## 🔗 Nectiv Links
- Website: https://nectivdigital.com
- Blog: https://nectivdigital.com/blog
- Contact: https://nectivdigital.com/contact
- LinkedIn: https://www.linkedin.com/company/nectiv
- Twitter: https://twitter.com/nectiv

## 📌 Quick Command Reference

### Validate HTML:
Check for unclosed tags, proper nesting, and email compatibility.

### Add Section:
Copy section template structure, maintain consistent spacing.

### Remove Section:
Delete entire table blocks, adjust spacing dividers.

### Update Colors:
Use only the approved brand colors listed above.

### Test Email:
Always test on Gmail, Outlook, iOS Mail, and dark mode.

---

Remember: The goal is to provide valuable, actionable SEO and GEO content that helps subscribers succeed in AI-powered search while maintaining Nectiv's professional brand standards.