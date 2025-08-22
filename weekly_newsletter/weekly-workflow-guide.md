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
