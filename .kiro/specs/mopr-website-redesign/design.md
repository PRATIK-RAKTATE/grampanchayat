# Design Document

## Overview

This design document outlines the transformation of the existing Gram Panchayat website to replicate the exact visual design and functionality of the official Ministry of Panchayati Raj (MOPR) website. The redesign will replace the current modern, minimalist approach with a government-standard layout that includes official branding, specific color schemes, and structured content organization.

## Architecture

### Layout Structure
The website will follow a traditional government portal structure:
- **Header Section**: Government branding with official logos and ministry identification
- **Navigation Bar**: Horizontal menu with dropdown functionality
- **Hero Banner**: Prominent announcement section with carousel functionality
- **Main Content**: Two-column layout with primary content and sidebar
- **Footer**: Government-standard footer with official information

### Visual Hierarchy
1. **Primary Level**: Government emblem and ministry branding
2. **Secondary Level**: Main navigation and hero announcements
3. **Tertiary Level**: Content sections and supplementary information

## Components and Interfaces

### Header Component
```
Structure:
├── Government Emblem (Left)
├── Ministry Title (Center)
│   ├── Hindi: "पंचायती राज मंत्रालय"
│   └── English: "Ministry of Panchayati Raj"
└── Official Logos (Right)
    ├── Swachh Bharat Logo
    ├── G20 India Logo
    └── Additional Government Badges
```

**Styling Specifications:**
- Background: Pure white (#ffffff)
- Height: ~80-100px
- Logo dimensions: 60-70px height
- Typography: Official government fonts
- Alignment: Flex layout with space-between

### Navigation Component
```
Structure:
├── HOME (Active state)
├── ABOUT US ▼
├── PANCHAYAT FINANCE ▼
├── PESA ▼
├── PRI ▼
├── RGSA ▼
├── SDG ▼
├── PAI ▼
├── SVAMITVA
├── E-GOVERNANCE ▼
├── AWARDS ▼
└── Mobile Menu (☰)
```

**Styling Specifications:**
- Background: Dark teal/blue (#1e3a5f or similar)
- Active item background: Lighter teal (#4a90a4)
- Text color: White
- Font weight: Medium
- Dropdown styling: White background with dark text

### Hero Banner Component
```
Structure:
├── Background Image (PM photo)
├── Content Overlay
│   ├── "MANN Ki BAAT" (Large red text)
│   ├── Date: "on 31st August 2025"
│   ├── Time: "TIME 11:00 AM"
│   └── "WATCH LIVE" Button
├── Navigation Controls
│   ├── Previous Arrow (◀)
│   ├── Pause/Play (⏸)
│   └── Next Arrow (▶)
└── News Ticker: "LATEST NEWS"
```

**Styling Specifications:**
- Height: ~400-500px
- Background: Image with overlay
- "MANN Ki BAAT" color: #d32f2f (red)
- Button styling: Red background with white text
- News ticker: Dark blue background

### Content Layout Component
```
Structure:
├── Main Content (Left Column - 70%)
│   ├── "About MOPR" Section
│   └── Detailed content paragraphs
└── Sidebar (Right Column - 30%)
    ├── "What's New" Section
    └── Recent updates list
```

## Data Models

### Navigation Menu Structure
```javascript
{
  menuItems: [
    { name: "HOME", active: true, hasDropdown: false },
    { name: "ABOUT US", hasDropdown: true, items: [...] },
    { name: "PANCHAYAT FINANCE", hasDropdown: true, items: [...] },
    // ... other menu items
  ]
}
```

### Hero Banner Data
```javascript
{
  slides: [
    {
      title: "MANN Ki BAAT",
      date: "31st August 2025",
      time: "11:00 AM",
      backgroundImage: "pm-image.jpg",
      ctaButton: { text: "WATCH LIVE", link: "#" }
    }
  ],
  newsTicker: "LATEST NEWS"
}
```

### Content Sections
```javascript
{
  aboutSection: {
    title: "About MOPR",
    content: "The Ministry of Panchayati Raj looks after the ongoing process..."
  },
  whatsNew: {
    title: "What's New",
    items: [
      { title: "Gramodyay Sankalp – 16", date: "..." },
      // ... other news items
    ]
  }
}
```

## Error Handling

### Image Loading
- Implement fallback images for government logos
- Graceful degradation for hero background images
- Alt text for all images for accessibility

### Navigation Failures
- Ensure dropdown menus have fallback behavior
- Mobile menu should work without JavaScript
- Keyboard navigation support

### Content Loading
- Progressive enhancement for dynamic content
- Fallback content for failed API calls
- Proper loading states

## Testing Strategy

### Visual Regression Testing
- Compare rendered output with official MOPR website screenshots
- Test across different browsers and devices
- Verify color accuracy and spacing

### Functionality Testing
- Test all navigation dropdown menus
- Verify carousel functionality in hero section
- Test responsive behavior on mobile devices
- Validate accessibility compliance

### Cross-browser Compatibility
- Test on Chrome, Firefox, Safari, Edge
- Verify on different screen resolutions
- Test on mobile devices (iOS/Android)

### Performance Testing
- Optimize image loading for government logos
- Ensure fast page load times
- Test with slow network connections

## Implementation Notes

### Color Palette
- Primary Blue: #1e3a5f (navigation background)
- Active Blue: #4a90a4 (active menu items)
- Accent Red: #d32f2f (Mann Ki Baat text, buttons)
- Background White: #ffffff
- Text Dark: #333333

### Typography
- Primary Font: Arial, sans-serif (government standard)
- Heading sizes: Follow government website hierarchy
- Line heights: 1.4-1.6 for readability

### Responsive Breakpoints
- Desktop: 1200px+
- Tablet: 768px - 1199px
- Mobile: Below 768px

### Asset Requirements
- Government of India emblem (SVG/PNG)
- Ministry logos (Swachh Bharat, G20, etc.)
- Prime Minister photo for hero background
- Placeholder images for content sections