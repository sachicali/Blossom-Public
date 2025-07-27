# Speech Bubbles Design System

## Overview
The speech bubble system is a core component of Blossomss's landing page, providing natural conversation-style interactions. This document outlines the updated technical specifications focused on creating authentic speech bubble proportions rather than banner-style layouts.

## Design Philosophy
**From Banner to Bubble**: The system now prioritizes natural conversation aesthetics over wide horizontal layouts, creating more authentic dialog experiences while maintaining feature-focused content.

## Components

### Child Speech Bubble
```tsx
// Location: client/src/components/landing/child-speech-bubble.tsx

// Natural Proportions (Updated)
- Container max-width: min(90vw, 420px) [reduced from 640px]
- Bubble constraints: min-width: 280px, max-width: 420px
- Vertical emphasis with responsive padding: clamp(16px, 4vw, 24px)
- Content flows naturally without artificial truncation

// Typography Enhancement
- Line height: 1.4 (improved from 1.5)
- Removed WebkitLineClamp and maxHeight constraints
- Natural text flow without ellipsis truncation
- Font sizes: 17px/18px/19px (optimized for new proportions)

// Mobile Optimization
- More vertical, less horizontal spread
- Better thumb-friendly interactions
- Improved readability on smaller screens

// Styling
background: gradient-to-br from-white via-white to-violet-50/95
border: border-violet-300/80
border-radius: rounded-[32px] sm:rounded-[36px]
padding: responsive clamp values
shadow: enhanced depth with hover effects
animations: spring-based transitions with bubble physics
```

### Parent Speech Bubbles
```tsx
// Location: client/src/components/landing/parent-speech-bubbles.tsx

// Natural Proportions (Updated)
- Container max-width: min(85vw, 360px) [more compact than child]
- Better positioning: marginLeft/Right reduced from -10vw to -8vw
- Improved content flow with enhanced padding: px-3 sm:px-4

// Typography Enhancement
- Line height: 1.4 (improved from 1.2)
- Font sizes: 14px/15px/16px (optimized for parent context)
- Better text shadow and spacing for readability
- Natural line breaks without artificial constraints

// Visual Improvements
- More conversational bubble proportions
- Better rounded corners: rounded-[40px] sm:rounded-[44px]
- Enhanced pointer design with layered styling
- Improved glow and particle effects

// Animation Sequence
1. Sachi types message
2. Father starts typing after Sachi completes
3. Mother interrupts halfway through father's message
```

## Key Improvements Made

### 1. Removed Banner-Style Constraints
**Before:**
- WebkitLineClamp: 2 (artificial text truncation)
- maxHeight: '3em' (forced horizontal layout)
- Wide fixed widths (640px+ containers)

**After:**
- Natural text flow without truncation
- Content-driven height calculation
- Narrower, more conversation-like proportions (280px-420px)

### 2. Enhanced Typography Flow
**Before:**
- lineHeight: 1.5 with ellipsis truncation
- Fixed horizontal emphasis
- Text cut off mid-sentence

**After:**
- lineHeight: 1.4 for better readability
- Natural line breaks and word wrapping
- Complete message display without cutoff

### 3. Improved Mobile Experience
**Before:**
- Wide banner feel on mobile
- Horizontal scrolling issues
- Touch targets too spread out

**After:**
- Vertical emphasis on mobile
- Better thumb accessibility
- More natural conversation appearance

### 4. Content-Adaptive Sizing
**Before:**
- One-size-fits-all approach
- Fixed dimensions regardless of content

**After:**
- Bubble size adapts to message length
- Minimum and maximum constraints for readability
- Responsive padding based on viewport
```

## Implementation Guidelines

### 1. Dynamic Positioning System
- Use useDynamicBubblePosition hook for consistent positioning
- Implement responsive sizing based on viewport
- Maintain smooth transitions between breakpoints
- Use relative units (vh, vw) for spacing

### 2. Visual Hierarchy
- Speech bubbles maintain z-index: 50
- Consistent border radiuses across screen sizes
- Smooth scaling animations on hover
- Hardware-accelerated transforms

### 3. Typography
- Font sizes scale with viewport width
- Line heights remain consistent
- Text remains centered and readable
- Maximum width constraints for readability

### 4. Animation
- Spring physics for natural movement
- Hardware-accelerated properties
- Consistent timing across interactions
- Reduced motion support

## Screen Size Considerations

### Mobile (<480px)
- Width: min(90vw, 480px)
- Bottom spacing: max(8vh, 40px)
- Centered positioning
- Adjusted font sizes
- Touch-optimized interactions

### Tablet (480px - 1024px)
- Width: min(95vw, 640px)
- Bottom spacing: max(4vh, 20px)
- Balanced typography scale
- Enhanced hover states

### Desktop (>1024px)
- Maximum width: 640px
- Optimized padding
- Full animation suite
- Rich hover interactions

## Best Practices

1. **Performance**
   - Use will-change hints appropriately
   - Hardware-accelerate transforms
   - Efficient animation properties
   - Debounced window resize handlers

2. **Accessibility**
   - Maintain readable contrast ratios
   - Support reduced motion
   - Proper ARIA attributes
   - Keyboard navigation support

3. **Responsiveness**
   - Mobile-first approach
   - Fluid typography
   - Breakpoint-based adjustments
   - Container queries where needed

## Maintenance

When updating speech bubble components:
1. Test across all breakpoints
2. Verify animation performance
3. Check touch interactions
4. Maintain documentation
5. Update responsive tests
