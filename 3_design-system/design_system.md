# AI Assessment Assistant - Design System

A comprehensive visual guide for the AI Assessment Assistant application, built with LaunchPad Lab's established branding and optimized for voice-based interactions.

## Brand Identity

**Logo Usage:**
- Primary: `Blue-Horizontal-LPL-Logo.svg` - Use on white/light backgrounds
- Alternative: `White-Horizontal-LPL-Logo.svg` - Use on dark/colored backgrounds  
- Monochrome: `Black-Horizontal-LPL-Logo.svg` - Use for print or single-color applications

**Logo Guidelines:**
- Minimum size: 120px width for digital applications
- Clear space: Equal to the height of the "L" in the logo on all sides
- Never stretch, rotate, or modify the logo proportions

## Color Palette

### Primary Colors
- **Primary Blue**: `#1E60BD` - Main brand color, primary buttons, links, focus states
- **Dark Charcoal**: `#2C2C35` - Primary text, headings, navigation
- **Pure White**: `#FFFFFF` - Page backgrounds, cards, button text

### Secondary Colors
- **Secondary Blue**: `#0B4E95` - Hover states, secondary buttons
- **Light Blue**: `#BFD7F0` - Backgrounds, disabled states, subtle highlights
- **Medium Gray**: `#393942` - Secondary text, icons
- **Gray**: `#525253` - Borders, dividers, placeholder text
- **Light Gray**: `#D9D9D9` - Input borders, card borders
- **Off White**: `#EEEEEE` - Section backgrounds, alternating rows

### Semantic Colors
- **Success**: `#22C55E` - Successful assessments, confirmations
- **Warning**: `#F59E0B` - Warnings, incomplete assessments
- **Error**: `#EF4444` - Errors, failed validations
- **Info**: `#1E60BD` - Information messages (uses primary blue)

### Brand Gradient
- **Primary Gradient**: `linear-gradient(135deg, #1E60BD 0%, #00ADEF 100%)`
- Use for: Hero sections, call-to-action areas, accent elements

## Typography

**Font Family:** Proxima Nova (with system fallbacks: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif)

### Text Hierarchy
- **H1**: 32px (2rem), Bold (700) - Page titles, main headings
- **H2**: 24px (1.5rem), Bold (700) - Section titles, dashboard headers  
- **H3**: 20px (1.25rem), Semibold (600) - Subsection headings, card titles
- **H4**: 18px (1.125rem), Semibold (600) - Component headers
- **Body Large**: 18px (1.125rem), Regular (400) - Important body text, voice interface text
- **Body**: 16px (1rem), Regular (400) - Standard body text, form labels
- **Body Small**: 14px (0.875rem), Regular (400) - Secondary text, metadata
- **Caption**: 12px (0.75rem), Regular (400) - Timestamps, fine print

### Voice Interface Typography
- **AI Response**: 18px (1.125rem), Regular (400), Primary Blue - AI agent messages
- **User Speech**: 18px (1.125rem), Regular (400), Dark Charcoal - Transcribed user speech
- **Status Text**: 16px (1rem), Medium (500), Medium Gray - Connection status, instructions

## Spacing Scale

- **xs**: 4px (0.25rem) - Icon spacing, tight elements
- **sm**: 8px (0.5rem) - Form element spacing
- **md**: 16px (1rem) - Standard component spacing
- **lg**: 24px (1.5rem) - Card padding, section spacing
- **xl**: 32px (2rem) - Page margins, large component spacing
- **2xl**: 48px (3rem) - Section separations
- **3xl**: 64px (4rem) - Major layout sections

## Component Library

### Buttons

**Primary Button:**
- Background: Primary Blue (`#1E60BD`)
- Text: White, 16px, Medium (500)
- Padding: 12px 24px
- Border radius: 8px
- Hover: Secondary Blue (`#0B4E95`)
- Shadow: `0 2px 4px rgba(30, 96, 189, 0.2)`

**Secondary Button:**
- Background: White
- Text: Primary Blue, 16px, Medium (500)
- Border: 2px solid Primary Blue
- Padding: 10px 22px
- Border radius: 8px
- Hover: Light Blue background (`#BFD7F0`)

**Voice Control Buttons:**
- **Start Assessment**: Large primary button (16px 32px padding)
- **Finish Assessment**: Secondary button with warning styling
- **Emergency Stop**: Error color background, white text

### Cards

**Standard Card:**
- Background: White
- Border: 1px solid Light Gray (`#D9D9D9`)
- Border radius: 12px
- Padding: 24px
- Shadow: `0 2px 8px rgba(0, 0, 0, 0.1)`

**Assessment Card:**
- Background: White
- Border radius: 16px
- Padding: 32px
- Shadow: `0 4px 16px rgba(0, 0, 0, 0.1)`
- Special: Gradient border for active assessments

### Form Elements

**Input Fields:**
- Background: White
- Border: 2px solid Light Gray (`#D9D9D9`)
- Border radius: 8px
- Padding: 12px 16px
- Text: 16px, Dark Charcoal
- Focus: Primary Blue border, blue shadow
- Placeholder: Gray (`#525253`)

**Text Areas:**
- Same as input fields
- Minimum height: 120px
- Resize: Vertical only

### Voice Interface Components

**Transcript Display:**
- Background: Off White (`#EEEEEE`)
- Border radius: 12px
- Padding: 24px
- Max height: 400px with scroll
- Font: 18px, line-height 1.6

**Audio Visualizer:**
- Primary color: Primary Blue with opacity variations
- Background: Light Blue (`#BFD7F0`)
- Height: 60px
- Border radius: 30px

**Status Indicators:**
- **Recording**: Pulsing red dot (8px)
- **Processing**: Animated Primary Blue spinner
- **Ready**: Static green dot (8px)

### Navigation

**Admin Navigation:**
- Background: White
- Border bottom: 1px solid Light Gray
- Logo: Blue horizontal logo (left aligned)
- Links: 16px, Dark Charcoal
- Active: Primary Blue with underline
- Mobile: Hamburger → slide-out drawer

**Breadcrumbs:**
- Text: 14px, Gray
- Separator: `/` in Gray
- Current page: Dark Charcoal, no link

## Layout Patterns

### Admin Dashboard
- **Sidebar**: 280px width, white background
- **Main Content**: Flexible width, Off White background
- **Cards Grid**: 24px gaps, responsive columns

### Assessment Interface
- **Centered Layout**: Max width 800px
- **Full Height**: Utilize full viewport for voice interface
- **Minimal Chrome**: Remove distractions during assessment

### Mobile Considerations
- **Breakpoints**: 640px (sm), 768px (md), 1024px (lg), 1280px (xl)
- **Voice Interface**: Full screen on mobile
- **Admin Dashboard**: Responsive cards, collapsible sidebar

## Accessibility

### Color Contrast
- All text combinations meet WCAG AA standards (4.5:1 minimum)
- Primary Blue on White: 5.8:1 ✓
- Dark Charcoal on White: 12.6:1 ✓
- White on Primary Blue: 5.8:1 ✓

### Focus States
- All interactive elements have visible focus indicators
- Focus ring: 2px Primary Blue with 2px offset
- Keyboard navigation support throughout

### Voice Interface Accessibility
- Clear visual indicators for recording state
- Text alternatives for audio-only information
- Support for screen reader announcements

## Technical Implementation

**CSS Framework:** Tailwind CSS with custom configuration
**Component Library:** Flowbite (customized with brand colors)
**Icons:** Heroicons (outline style preferred)

### Tailwind Configuration
```javascript
// Custom colors for tailwind.config.js
colors: {
  primary: {
    50: '#f0f6ff',
    500: '#1E60BD',
    600: '#0B4E95',
    700: '#1a365d',
  },
  charcoal: {
    500: '#2C2C35',
    600: '#393942',
  }
}
```

### Font Loading
```css
/* Include Proxima Nova via Adobe Fonts or similar */
@import url('https://use.typekit.net/[kit-id].css');

.font-proxima {
  font-family: 'proxima-nova', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}
```

## Voice Interface Specific Guidelines

### Visual Feedback
- Always provide visual confirmation of audio state
- Use animation to indicate active listening
- Clear visual separation between AI and user text

### Error States
- Microphone access denied: Clear instructions with retry button
- Poor audio quality: Gentle notification with improvement tips
- Connection issues: Obvious status with reconnection options

### Loading States
- Skeleton screens for content loading
- Smooth transitions between states
- Progress indicators for longer operations

## Brand Voice & Tone

**Professional yet Approachable:** Maintain LaunchPad Lab's expert positioning while being welcoming

**Clear and Direct:** Especially important for voice interface instructions

**Supportive:** Guide users through the assessment process without intimidation

This design system ensures consistent, accessible, and on-brand experiences across all touchpoints of the AI Assessment Assistant. 