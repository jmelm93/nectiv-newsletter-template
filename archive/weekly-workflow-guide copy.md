# Nectiv Newsletter - Weekly Workflow Guide

## Overview

This guide explains how to create and send your weekly Nectiv newsletter using the new modular template system in Kit.com.

## Files You'll Need

1. **nectiv-email-template.html** - The main template (one-time setup)
2. **weekly-content-template.html** - Your weekly content snippets
3. **This guide** - Step-by-step instructions

## Initial Setup (One Time Only)

### Step 1: Import the Template to Kit.com

1. Open `nectiv-email-template.html` in a text editor
2. Copy ALL content (Ctrl+A, then Ctrl+C)
3. Log into Kit.com
4. Navigate to: Profile Icon → Email → Email Templates
5. Click "New Email Template"
6. Select "Create HTML Template"
7. Paste the template code
8. Name it: "Nectiv GEO Insider - Weekly Template"
9. Click "Save Template"
10. Optional: Set as default template (three dots menu → "Set as default")

## Weekly Newsletter Creation Process

### Step 1: Create a New Email

1. Go to Broadcasts → New Broadcast
2. Select your template: "Nectiv GEO Insider - Weekly Template"
3. The template will load with the `{{ message_content }}` area ready for your content

### Step 2: Add Your Weekly Content

1. Open `weekly-content-template.html` in a text editor
2. Replace all `[UPDATE]` placeholders with your actual content:
   - Search for `[UPDATE]` to find all placeholders that need replacement
   - Replace with actual headlines, descriptions, button text, etc.
   - Replace all `https://example.com/` URLs with real links
   - Remove any sections you don't need this week
3. Copy the entire edited HTML
4. In Kit.com's email editor, paste into the content area

### Step 3: Customize Content

#### For AI Search & GEO News:

```html
<!-- Replace these placeholders -->
[UPDATE] → "Google Launches New AI Overview Features for B2B Queries" [UPDATE] →
"Google's latest update prioritizes B2B content in AI overviews, creating new
opportunities for enterprise SEO strategies." https://example.com/ →
"https://yourdomain.com/actual-article-url"
```

#### Adding/Removing News Items:

- Keep 3-5 items for optimal engagement
- Delete entire `<tr>` blocks to remove items
- Copy and paste `<tr>` blocks to add more

#### Using Badges:

Add badges to highlight special content:

- **Trending** (Red): For hot topics
- **New** (Green): For fresh content
- **Default** (Blue): For categorization

```html
<!-- Add before headline -->
<span style="background-color: #FF6B6B; color: #ffffff; ...">Trending</span>
```

#### For Tool Spotlight:

Replace all `[UPDATE]` placeholders with:

- Tool name
- Tool description (2-3 sentences about what it does)
- Key features or benefits (list items)
- Pricing information (free, paid, or price range)
- Button text ("Try It Free", "Learn More", etc.)

Replace `https://example.com/` with the actual tool URL.

#### For Resources & Guides:

Each resource card needs:

- Icon emoji (🎯, 📖, 💡, etc.)
- Title (clear and benefit-focused)
- Description (what they'll get)
- CTA button text
- Download/access link

### Step 4: Content Editing Tips

#### Headlines Best Practices:

- Keep under 80 characters
- Use action words
- Include keywords (AI, SEO, GEO, ChatGPT, etc.)
- Create urgency when appropriate

#### Description Guidelines:

- 100-150 characters per description
- Focus on value/benefit
- Use clear, simple language
- Include specific details (percentages, timeframes)

#### Link Management:

- Always use full URLs (https://...)
- Add UTM parameters for tracking:
  ```
  ?utm_source=newsletter&utm_medium=email&utm_campaign=geo-insider-week-XX
  ```
- Test all links before sending

### Step 6: Preview and Test

1. Use Kit.com's preview button to check formatting
2. Send a test email to yourself
3. Check on multiple devices:
   - Desktop (Gmail, Outlook)
   - Mobile (iOS Mail, Gmail app)
   - Dark mode compatibility
4. Verify all links work
5. Check personalization fallbacks

### Step 7: Final Checklist

Before sending:

- [ ] All `[UPDATE]` placeholders replaced with real content
- [ ] All `https://example.com/` URLs replaced with actual links
- [ ] Links tested and working
- [ ] Images have alt text (if used)
- [ ] Unsubscribe link visible (automatic)
- [ ] Physical address included (automatic)
- [ ] Subject line written (30-50 characters)
- [ ] Preheader text set (50-100 characters)
- [ ] Send time scheduled (best: Tuesday-Thursday, 10am EST)

### Step 8: Schedule and Send

1. Set your subject line
2. Set preheader text
3. Choose your audience segment
4. Schedule for optimal time
5. Click "Schedule Broadcast"

## Content Section Management

### To Remove a Section:

Simply don't include it in your weekly content. The template is modular.

### To Reorder Sections:

Cut and paste entire section blocks in the HTML to reorder.

### To Add Custom Sections:

Use this template structure:

```html
<table
  role="presentation"
  cellspacing="0"
  cellpadding="0"
  border="0"
  width="100%"
>
  <tr>
    <td>
      <h2
        style="border-bottom: 3px solid #0066FF; color: #1a1a1a; font-size: 20px; font-weight: 700; margin-bottom: 20px; padding-bottom: 10px; font-family: Arial, sans-serif;"
      >
        [SECTION ICON] [SECTION TITLE]
      </h2>
    </td>
  </tr>
  <tr>
    <td>[YOUR CONTENT HERE]</td>
  </tr>
</table>
```

## Time-Saving Tips

### Create Content Banks:

1. Keep a running document of:

   - Interesting AI/SEO news throughout the week
   - Tool discoveries
   - Resource ideas
   - Insight topics

2. Use a spreadsheet to track:
   - What content you've shared
   - Engagement metrics
   - Popular topics to revisit

### Batch Content Creation:

- Write 2-3 newsletters at once
- Schedule them in advance
- Keep emergency backup content ready

### Use Templates for Consistency:

- Save successful headline formats
- Reuse description structures that work
- Keep CTA button text consistent

## Troubleshooting

### Content Not Displaying Correctly:

- Ensure you're pasting into the email editor, not the template editor
- Check for unclosed HTML tags
- Verify no conflicting styles
- Ensure all `[UPDATE]` placeholders have been replaced
- Verify all `https://example.com/` URLs have been updated

### Links Not Working:

- Ensure full URLs (including https://)
- No spaces in URLs
- Special characters properly encoded

### Personalization Not Working:

- Check liquid tag syntax: `{{ subscriber.first_name }}`
- Ensure fallback values are set
- Test with a subscriber that has/hasn't the field

## Performance Tracking

### Key Metrics to Monitor:

- **Open Rate**: Target 35-45%
- **Click Rate**: Target 8-12%
- **Best Performers**: Which sections get most clicks
- **Unsubscribe Rate**: Keep below 0.5%

### A/B Testing Ideas:

- Subject lines (question vs. statement)
- Number of news items (3 vs. 5)
- CTA button text
- Content order

## Support Resources

### Kit.com Help:

- [Email Editor Guide](https://help.kit.com/en/articles/2943289)
- [Template Documentation](https://help.kit.com/en/articles/2810363)
- [Personalization Guide](https://help.kit.com/en/articles/2502633)

### Content Inspiration:

- Monitor SEOFOMO newsletter for trends
- Follow AI search news on Twitter/LinkedIn
- Subscribe to competitor newsletters
- Track Google Search Central updates

## Quick Reference

### HTML Color Codes:

- Primary Blue: `#0066FF`
- Success Green: `#00D084`
- Alert Red: `#FF6B6B`
- Text Dark: `#1a1a1a`
- Text Light: `#666666`
- Background Light: `#F0F7FF`
- Border: `#E5E5E5`

### Font Sizes:

- Section Headers: `20px`
- Article Titles: `18px`
- Body Text: `14px`
- Small Text: `12px`

### Spacing:

- Section padding: `30px`
- Item spacing: `20px`
- Line height: `22px`

---

Remember: The goal is to provide valuable, actionable content that helps your audience succeed with SEO and GEO. Focus on quality over quantity, and always test before sending!
