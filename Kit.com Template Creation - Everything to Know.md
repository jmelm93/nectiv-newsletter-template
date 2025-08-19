# Kit.com Template Creation - Everything to Know

## Overview
This document contains comprehensive knowledge about creating HTML email templates for Kit.com (formerly ConvertKit), including limitations, workarounds, and best practices discovered through practical implementation.

## Core Kit.com Template Limitations

### 1. Single Editable Area Limitation
**The Problem:** Kit.com HTML templates only support ONE editable content area via the `{{ message_content }}` variable.
- You cannot create multiple independent editable sections
- You cannot use custom variables or loops for repeatable content
- The template structure is fixed once imported

**The Solution:** Use a two-file system:
1. **Main Template:** Contains header, footer, and styling with `{{ message_content }}` placeholder
2. **Weekly Content Template:** Pre-formatted HTML snippets that get pasted into the email editor

### 2. Template Types in Kit.com
- **HTML Templates:** Custom coded, cannot be edited in visual editor, only one editable area
- **Starting Point Templates:** Fully editable in visual editor but less design control
- **Classic Templates:** Limited editing capabilities, only default content block editable

## Required Kit.com Template Variables

### Mandatory Variables (Template won't work without these)
```html
{{ message_content }}        <!-- Where email content goes -->
{{ unsubscribe_link }}      <!-- Or {{ unsubscribe_url }} for href attribute -->
{{ address }}               <!-- Physical mailing address for CAN-SPAM compliance -->
```

### Optional Personalization Variables
```html
{{ subscriber.first_name }}           <!-- Subscriber's first name -->
{{ subscriber.first_name | default: "Friend" }}  <!-- With fallback -->
{{ subscriber_preferences_link }}     <!-- Profile update link -->
{{ subscriber_preferences_url }}      <!-- For href attribute -->
{{ subscriber.custom_field_name }}    <!-- Any custom field -->
```

## Common Issues and Solutions

### Issue 1: Padding Not Working in Email Content
**Problem:** Content appears flush against email edges when pasted into Kit.com

**Root Cause:** Kit.com strips some styling when content is pasted directly into the editor

**Solution:** Wrap `{{ message_content }}` in the main template with proper padding:
```html
<td style="background-color: #ffffff; padding: 0;">
    <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
        <tr>
            <td style="padding: 40px 30px;">
                {{ message_content }}
            </td>
        </tr>
    </table>
</td>
```

### Issue 2: Invalid href Values
**Problem:** Kit.com rejects templates with placeholder URLs like `href="[LINK-URL]"`

**Solution:** Always use valid URLs in templates:
- Use `https://example.com` as placeholder
- Replace with actual URLs when creating weekly content
- Never use brackets or invalid URL formats

### Issue 3: Multiple Editable Sections Needed
**Problem:** Need to edit different sections (news, tools, resources) independently

**Solution:** Create modular HTML blocks in separate file:
1. Structure content as standalone HTML snippets
2. Use clear section separators
3. Copy entire HTML into Kit.com's editor
4. Edit the HTML directly in the editor for weekly updates

## Email HTML Best Practices for Kit.com

### 1. Table-Based Layout
```html
<!-- Use tables for structure, not divs -->
<table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
    <tr>
        <td>Content here</td>
    </tr>
</table>
```

### 2. Inline CSS Required
```html
<!-- Always use inline styles -->
<p style="color: #666666; font-size: 14px; line-height: 22px;">
    Text content
</p>
```

### 3. Outlook Compatibility
```html
<!--[if mso]>
<xml>
    <o:OfficeDocumentSettings>
        <o:AllowPNG/>
        <o:PixelsPerInch>96</o:PixelsPerInch>
    </o:OfficeDocumentSettings>
</xml>
<![endif]-->

<!-- MSO-specific CSS properties -->
<style>
table, td { 
    mso-table-lspace: 0pt !important; 
    mso-table-rspace: 0pt !important; 
}
</style>
```

### 4. Mobile Responsiveness
```css
@media screen and (max-width: 600px) {
    table.responsive-table { width: 100% !important; }
    .mobile-hide { display: none !important; }
    .mobile-padding { padding: 20px !important; }
}
```

### 5. Dark Mode Considerations
```css
@media (prefers-color-scheme: dark) {
    /* Invert your dark mode styles for emails */
    /* Most email clients don't handle dark mode well */
    .dark-mode-bg { background-color: #ffffff !important; }
    .dark-mode-text { color: #1a1a1a !important; }
}
```

## Working Template Structure

### Main Template File Structure
```html
<!DOCTYPE html>
<html>
<head>
    <!-- Meta tags and styles -->
</head>
<body>
    <!-- Preheader text (hidden) -->
    <div style="display: none;">Preheader text here</div>
    
    <!-- Main container -->
    <table width="100%">
        <!-- Header (fixed) -->
        <tr><td>Logo and branding</td></tr>
        
        <!-- Content area (editable) -->
        <tr>
            <td style="padding: 40px 30px;">
                {{ message_content }}
            </td>
        </tr>
        
        <!-- Footer (fixed) -->
        <tr><td>
            {{ address }}
            {{ unsubscribe_link }}
        </td></tr>
    </table>
</body>
</html>
```

### Weekly Content Template Structure
```html
<!-- Section 1 -->
<h2 style="[inline styles]">Section Title</h2>
<div style="[inline styles]">
    <h3><a href="https://example.com">Headline</a></h3>
    <p>Description</p>
</div>

<!-- Spacing -->
<div style="height: 30px;">&nbsp;</div>

<!-- Section 2 -->
<!-- Repeat pattern -->
```

## Import Process to Kit.com

### Step-by-Step Import
1. Navigate to: Profile → Email → Email Templates
2. Click "New Email Template"
3. Select "Create HTML Template"
4. Paste complete HTML code
5. Name the template
6. Save and optionally set as default

### Testing Checklist
- [ ] Preview in Kit.com's preview mode
- [ ] Send test email to multiple email clients
- [ ] Check all links work
- [ ] Verify personalization fallbacks
- [ ] Confirm unsubscribe link present
- [ ] Check physical address displays
- [ ] Test on mobile devices
- [ ] Verify dark mode rendering

## Color and Styling Guidelines

### Standard Email-Safe Fonts
```css
font-family: Arial, Helvetica, sans-serif;
font-family: Georgia, serif;
font-family: 'Courier New', monospace;
```

### Button Styles
```html
<!-- Primary button -->
<a href="#" style="
    background-color: #000000;
    border-radius: 6px;
    color: #ffffff;
    display: inline-block;
    font-size: 16px;
    font-weight: 600;
    padding: 14px 32px;
    text-decoration: none;
">Button Text</a>

<!-- Secondary button -->
<a href="#" style="
    background-color: #ffffff;
    border: 2px solid #000000;
    border-radius: 6px;
    color: #000000;
    display: inline-block;
    font-size: 16px;
    font-weight: 600;
    padding: 12px 30px;
    text-decoration: none;
">Button Text</a>
```

### Image Handling
```html
<img src="https://example.com/image.png" 
     alt="Description" 
     width="600" 
     style="display: block; width: 100%; max-width: 600px; height: auto;">
```

## Content Management Workflow

### Weekly Newsletter Process
1. **Template Setup (One Time)**
   - Import main template to Kit.com
   - Save weekly content template locally

2. **Weekly Content Creation**
   - Open weekly content template
   - Replace placeholder content with actual content
   - Update all URLs to real destinations
   - Copy entire HTML

3. **Email Creation in Kit.com**
   - Create new broadcast
   - Select your template
   - Paste weekly content HTML into editor
   - Preview and test
   - Schedule send

### Content Organization Tips
- Keep a spreadsheet of used content to avoid repetition
- Create a content bank of evergreen items
- Save successful email HTML for reference
- Track metrics for each section type

## Troubleshooting Guide

### Problem: Content Not Displaying
- Check for unclosed HTML tags
- Verify no conflicting CSS
- Ensure proper table structure

### Problem: Links Not Working
- Use full URLs (https://...)
- No spaces in URLs
- Special characters properly encoded (%20 for space)

### Problem: Personalization Not Working
- Check liquid tag syntax exactly
- Ensure fallback values provided
- Test with subscriber that has/lacks the field

### Problem: Template Rejected by Kit.com
- Verify all required variables present
- Check for valid unsubscribe link
- Ensure physical address included
- Validate HTML syntax

## Key Learnings and Best Practices

### Do's
✅ Always use tables for layout
✅ Inline all CSS styles
✅ Test across multiple email clients
✅ Include alt text for images
✅ Use absolute URLs for all links
✅ Keep email width at 600px max
✅ Provide fallbacks for personalization
✅ Use web-safe fonts

### Don'ts
❌ Don't use JavaScript
❌ Don't rely on external CSS files
❌ Don't use video elements
❌ Don't use forms
❌ Don't exceed 102KB in size
❌ Don't use CSS positioning
❌ Don't forget mobile optimization
❌ Don't use placeholder URLs in templates

## Advanced Tips

### 1. Conditional Content with Liquid
```liquid
{% if subscriber.first_name %}
    Hello {{ subscriber.first_name }}!
{% else %}
    Hello there!
{% endif %}
```

### 2. Background Images (with VML for Outlook)
```html
<!--[if mso]>
<v:rect xmlns:v="urn:schemas-microsoft-com:vml" fill="true" stroke="false">
<v:fill type="tile" src="background.jpg" />
<v:textbox inset="0,0,0,0">
<![endif]-->
<div style="background-image: url('background.jpg');">
    Content here
</div>
<!--[if mso]>
</v:textbox>
</v:rect>
<![endif]-->
```

### 3. Preheader Text Optimization
```html
<div style="display: none; font-size: 1px; color: #ffffff; line-height: 1px; max-height: 0px; max-width: 0px; opacity: 0; overflow: hidden;">
    Preheader text here. Add white space to prevent email client preview text&nbsp;&zwnj;&nbsp;&zwnj;&nbsp;&zwnj;
</div>
```

## File Organization

### Recommended File Structure
```
/email-templates/
├── kit-main-template.html          # Main template with header/footer
├── weekly-content-template.html    # Weekly content snippets
├── weekly-workflow-guide.md        # Instructions for team
├── content-archive/                # Past newsletters
│   ├── 2024-week-01.html
│   ├── 2024-week-02.html
│   └── ...
└── resources/                      # Images, logos, etc.
    └── logo.png
```

## Metrics to Track

### Email Performance KPIs
- **Open Rate:** Target 35-45%
- **Click Rate:** Target 8-12%
- **Unsubscribe Rate:** Keep below 0.5%
- **Bounce Rate:** Keep below 2%

### Section Performance
- Track which content sections get most clicks
- A/B test different section orders
- Monitor engagement by content type

## Platform-Specific Notes

### Kit.com Specific Limitations
1. No support for AMP emails
2. Limited template variable options
3. Cannot edit HTML templates in visual editor
4. No built-in template versioning
5. Limited conditional logic support

### Workarounds We Developed
1. **Two-file system** for editable sections
2. **Wrapper tables** for consistent padding
3. **Example URLs** instead of placeholders
4. **Modular HTML blocks** for easy updates
5. **Inline everything** for maximum compatibility

## Summary

Creating effective Kit.com email templates requires understanding the platform's limitations and working within them. The key insight is that Kit.com's single `{{ message_content }}` variable limitation can be overcome by using a two-file system: a main template for structure and branding, and a weekly content template for the actual email content.

Always remember:
- Kit.com is designed for simplicity, not complex templates
- Work with the platform's limitations, not against them
- Test thoroughly across email clients
- Keep content modular and reusable
- Document your process for team consistency

This approach allows for professional, branded emails while maintaining the flexibility to update content weekly without touching the main template structure.