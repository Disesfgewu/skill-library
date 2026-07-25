---
name: theme-factory
description: Toolkit for styling artifacts with a theme. These artifacts can be slides,
  docs, reportings, HTML landing pages, etc. There are 10 pre-set themes with colors/fonts
  that you can apply to any artifact that has been creating, or can generate a new
  theme on-the-fly.
version: 1.0.0
author: Anthropic / disesfgewuAgent
tags:
- design
- themes
- colors
- styling
---

# Theme Factory Skill

This skill provides a curated collection of professional font and color themes themes, each with carefully selected color palettes and font pairings. Once a theme is chosen, it can be applied to any artifact.

## Purpose

To apply consistent, professional styling to presentation slide decks, use this skill. Each theme includes:
- A cohesive color palette with hex codes
- Complementary font pairings for headers and body text
- A distinct visual identity suitable for different contexts and audiences

## Usage Instructions

To apply styling to a slide deck or other artifact:

1. **Present the theme catalog below** (name + colors + best-used-for) so the user can pick one. If the output format supports images, generate small swatches instead of just listing hex codes.
2. **Ask for their choice**: Ask which theme to apply to the deck
3. **Wait for selection**: Get explicit confirmation about the chosen theme
4. **Apply the theme**: Once a theme has been chosen, apply the selected theme's colors and fonts to the deck/artifact

## Theme Catalog

### Ocean Depths
A professional and calming maritime theme that evokes the serenity of deep ocean waters.
- **Deep Navy** `#1a2332` — primary background
- **Teal** `#2d8b8b` — accent for highlights and emphasis
- **Seafoam** `#a8dadc` — secondary accent for lighter elements
- **Cream** `#f1faee` — text and light backgrounds
- Headers: DejaVu Sans Bold · Body: DejaVu Sans
- Best for: corporate presentations, financial reports, professional consulting decks, trust-building content

### Sunset Boulevard
A warm and vibrant theme inspired by golden hour sunsets, perfect for energetic and creative presentations.
- **Burnt Orange** `#e76f51` — primary accent
- **Coral** `#f4a261` — secondary warm accent
- **Warm Sand** `#e9c46a` — highlighting and backgrounds
- **Deep Purple** `#264653` — dark contrast and text
- Headers: DejaVu Serif Bold · Body: DejaVu Sans
- Best for: creative pitches, marketing presentations, lifestyle brands, event promotions, inspirational content

### Forest Canopy
A natural and grounded theme featuring earth tones inspired by dense forest environments.
- **Forest Green** `#2d4a2b` — primary dark green
- **Sage** `#7d8471` — muted green accent
- **Olive** `#a4ac86` — light accent color
- **Ivory** `#faf9f6` — backgrounds and text
- Headers: FreeSerif Bold · Body: FreeSans
- Best for: environmental presentations, sustainability reports, outdoor brands, wellness content, organic products

### Modern Minimalist
A clean and contemporary theme with a sophisticated grayscale palette for maximum versatility.
- **Charcoal** `#36454f` — primary dark color
- **Slate Gray** `#708090` — medium gray for accents
- **Light Gray** `#d3d3d3` — backgrounds and dividers
- **White** `#ffffff` — text and clean backgrounds
- Headers: DejaVu Sans Bold · Body: DejaVu Sans
- Best for: tech presentations, architecture portfolios, design showcases, modern business proposals, data visualization

### Golden Hour
A rich and warm autumnal palette that creates an inviting and sophisticated atmosphere.
- **Mustard Yellow** `#f4a900` — bold primary accent
- **Terracotta** `#c1666b` — warm secondary color
- **Warm Beige** `#d4b896` — neutral backgrounds
- **Chocolate Brown** `#4a403a` — dark text and anchors
- Headers: FreeSans Bold · Body: FreeSans
- Best for: restaurant presentations, hospitality brands, fall campaigns, cozy lifestyle content, artisan products

### Arctic Frost
A cool and crisp winter-inspired theme that conveys clarity, precision, and professionalism.
- **Ice Blue** `#d4e4f7` — light backgrounds and highlights
- **Steel Blue** `#4a6fa5` — primary accent color
- **Silver** `#c0c0c0` — metallic accent elements
- **Crisp White** `#fafafa` — clean backgrounds and text
- Headers: DejaVu Sans Bold · Body: DejaVu Sans
- Best for: healthcare presentations, technology solutions, winter sports, clean tech, pharmaceutical content

### Desert Rose
A soft and sophisticated theme with dusty, muted tones perfect for elegant presentations.
- **Dusty Rose** `#d4a5a5` — soft primary color
- **Clay** `#b87d6d` — earthy accent
- **Sand** `#e8d5c4` — warm neutral backgrounds
- **Deep Burgundy** `#5d2e46` — rich dark contrast
- Headers: FreeSans Bold · Body: FreeSans
- Best for: fashion presentations, beauty brands, wedding planning, interior design, boutique businesses

### Tech Innovation
A bold and modern theme with high-contrast colors perfect for cutting-edge technology presentations.
- **Electric Blue** `#0066ff` — vibrant primary accent
- **Neon Cyan** `#00ffff` — bright highlight color
- **Dark Gray** `#1e1e1e` — deep backgrounds
- **White** `#ffffff` — clean text and contrast
- Headers: DejaVu Sans Bold · Body: DejaVu Sans
- Best for: tech startups, software launches, innovation showcases, AI/ML presentations, digital transformation content

### Botanical Garden
A fresh and organic theme featuring vibrant garden-inspired colors for lively presentations.
- **Fern Green** `#4a7c59` — rich natural green
- **Marigold** `#f9a620` — bright floral accent
- **Terracotta** `#b7472a` — earthy warm tone
- **Cream** `#f5f3ed` — soft neutral backgrounds
- Headers: DejaVu Serif Bold · Body: DejaVu Sans
- Best for: garden centers, food presentations, farm-to-table content, botanical brands, natural products

### Midnight Galaxy
A dramatic and cosmic theme with deep purples and mystical tones for impactful presentations.
- **Deep Purple** `#2b1e3e` — rich dark base
- **Cosmic Blue** `#4a4e8f` — mystical mid-tone
- **Lavender** `#a490c2` — soft accent color
- **Silver** `#e6e6fa` — light highlights and text
- Headers: FreeSans Bold · Body: FreeSans
- Best for: entertainment industry, gaming presentations, nightlife venues, luxury brands, creative agencies

## Application Process

After a preferred theme is selected:
1. Apply the specified colors and fonts consistently throughout the deck
2. Ensure proper contrast and readability
3. Maintain the theme's visual identity across all slides

## Create your Own Theme
To handle cases where none of the existing themes work for an artifact, create a custom theme. Based on provided inputs, generate a new theme similar to the ones above. Give the theme a similar name describing what the font/color combinations represent. Use any basic description provided to choose appropriate colors/fonts. After generating the theme, show it for review and verification. Following that, apply the theme as described above.
