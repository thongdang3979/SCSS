# SCSS Framework

Lightweight SCSS framework with zero-redundancy design. Only generates CSS for mixins you actually use.

## File Structure

```
scss/
├── base/
│   ├── _reset.scss
│   ├── _color.scss
│   ├── _font.scss
│   └── _index.scss
├── mixins/
│   ├── _flexbox.scss
│   ├── _layout.scss
│   ├── _responsive.scss
│   ├── _typography.scss
│   ├── _transition.scss
│   ├── _animation.scss
│   ├── _transform.scss
│   └── _index.scss
└── main.scss
```

## Installation

```bash
npm install -g sass
```

## Usage

```bash
sass --watch scss/.:css/. --style compressed
```

## Import

```scss
@use "mixins/index" as *;
@use "base/index" as *;
```

## Typography

### Font Mixin
```scss
@mixin font($size, $weight, $line-height, $color, $tablet-ratio, $mobile-ratio, $transition)

// Examples
.title {
    @include font($text-2xl, $font-bold, $leading-tight, $primary);
}

.responsive-text {
    @include font($text-lg, $font-medium, $leading-normal, $black, 0.8, 0.6);
}
```

### Fluid Typography
```scss
@mixin fluid-font($min-size, $max-size, $min-width, $max-width)

// Example
.hero-title {
    @include fluid-font(1.5rem, 3rem, 320px, 1200px);
}
```

### Text Utilities
```scss
@mixin text-truncate($lines)
@mixin font-smooth
@mixin text-selection($bg, $color)
@mixin placeholder($color, $opacity)
@mixin heading($level)

// Examples
.card-text {
    @include text-truncate(3);
}

.smooth-text {
    @include font-smooth;
}

.custom-selection {
    @include text-selection($primary, $white);
}

.main-heading {
    @include heading(1);
}
```

## Flexbox

### Basic Flex
```scss
@mixin flex($direction, $wrap, $justify, $align, $gap)

// Examples
.navbar {
    @include flex(row, nowrap, space-between, center, 20px);
}

.sidebar {
    @include flex(column, nowrap, flex-start, stretch, 15px);
}
```

### Flex Shortcuts
```scss
@mixin flex-center($direction, $gap)
@mixin flex-between($direction, $align, $gap)
@mixin flex-around($direction, $align, $gap)
@mixin flex-evenly($direction, $align, $gap)

// Examples
.modal {
    @include flex-center(column, 20px);
}

.header {
    @include flex-between(row, center, 30px);
}
```

### Flex Items
```scss
@mixin flex-item($grow, $shrink, $basis)
@mixin flex-width($gap, $columns, $tablet-columns, $mobile-columns)

// Examples
.main-content {
    @include flex-item(1, 1, 0);
}

.card {
    @include flex-width(20px, 3, 2, 1);
}
```

### Positioning
```scss
@mixin absolute-center($horizontal, $vertical)

// Example
.overlay {
    @include absolute-center(true, true);
}
```

## Layout

### Grid System
```scss
@mixin col($size, $total)
@mixin col-auto
@mixin col-full
@mixin col-sm($size, $total)
@mixin col-md($size, $total)
@mixin col-lg($size, $total)
@mixin col-xl($size, $total)

// Examples
.article {
    @include col-md(8);
    @include col-lg(9);
}

.sidebar {
    @include col-md(4);
    @include col-lg(3);
}
```

### Container System
```scss
@mixin container($padding)
@mixin container-responsive($sm, $md, $lg, $xl, $xxl)
@mixin row($gutter)

// Examples
.main-container {
    @include container();
    @include container-responsive();
}

.grid-row {
    @include row(20px);
}
```

### CSS Grid
```scss
@mixin grid($columns, $gap)
@mixin grid-item($col-start, $col-end, $row-start, $row-end)

// Examples
.gallery {
    @include grid(3, 20px);
}

.featured {
    @include grid-item(1, 3, 1, 2);
}
```

### Aspect Ratio
```scss
@mixin aspect-ratio($width, $height)

// Example
.video-container {
    @include aspect-ratio(16, 9);
}
```

## Responsive

### Breakpoint Mixins
```scss
@mixin respond($breakpoint)
@mixin respond-down($breakpoint)
@mixin respond-between($lower, $upper)

// Examples
.example {
    font-size: 1rem;
    
    @include respond(md) {
        font-size: 1.5rem;
    }
    
    @include respond-down(sm) {
        font-size: 0.875rem;
    }
    
    @include respond-between(md, lg) {
        background: $primary;
    }
}
```

### Visibility Controls
```scss
@mixin hide-on($breakpoint)
@mixin show-on($breakpoint)

// Examples
.mobile-menu {
    @include show-on(mobile);
}

.desktop-nav {
    @include hide-on(mobile);
}
```

### Available Breakpoints
- **Standard**: `xs` (0+), `sm` (576px+), `md` (768px+), `lg` (992px+), `xl` (1200px+), `xxl` (1400px+)
- **Semantic**: `mobile` (max 767px), `tablet` (max 991px), `laptop` (max 1199px), `desktop` (1200px+)
- **Custom**: Any pixel value like `@include respond(600px)`

## Transitions

```scss
@mixin transition($property, $duration, $timing)
@mixin transition-delay($delay)
@mixin transition-colors($duration)
@mixin transition-opacity($duration)
@mixin transition-transform($duration, $timing)
@mixin transition-none

// Examples
.button {
    @include transition-colors(0.2s);
}

.modal {
    @include transition-opacity(0.3s);
    @include transition-delay(0.1s);
}

.card:hover {
    @include transition-transform(0.3s, ease-out);
}
```

## Animations

```scss
@mixin animation($animation)
@mixin fade-in($duration, $timing)
@mixin fade-out($duration, $timing)
@mixin slide-in-up($duration, $distance)
@mixin slide-in-down($duration, $distance)
@mixin bounce($duration)
@mixin pulse($duration)

// Examples
.hero {
    @include fade-in(0.5s);
}

.notification {
    @include slide-in-down(0.3s, 50px);
}

.loading {
    @include pulse(1.5s);
}
```

## Transforms

```scss
@mixin transform($value)
@mixin translate($x, $y)
@mixin translate-x($x)
@mixin translate-y($y)
@mixin translate-3d($x, $y, $z)
@mixin scale($x, $y)
@mixin scale-x($x)
@mixin scale-y($y)
@mixin rotate($angle)
@mixin rotate-x($angle)
@mixin rotate-y($angle)
@mixin rotate-z($angle)
@mixin skew($x, $y)
@mixin skew-x($x)
@mixin skew-y($y)
@mixin transform-origin($origin)
@mixin perspective($perspective)
@mixin backface-visibility($visibility)
@mixin transform-style($style)
@mixin hardware-acceleration

// Examples
.card:hover {
    @include scale(1.05);
    @include translate-y(-5px);
}

.spinner {
    @include rotate(45deg);
    @include hardware-acceleration;
}

.flip-container {
    @include perspective(1000px);
    @include transform-style(preserve-3d);
}
```

## Variables

### Colors
```scss
// Base colors
$white: #ffffff;
$black: #000000;

// Gray scale
$gray-50: #f9fafb;
$gray-100: #f3f4f6;
$gray-200: #e5e7eb;
$gray-300: #d1d5db;
$gray-400: #9ca3af;
$gray-500: #6b7280;
$gray-600: #4b5563;
$gray-700: #374151;
$gray-800: #1f2937;
$gray-900: #111827;

// Theme colors
$primary: #3b82f6;
$primary-light: #60a5fa;
$primary-dark: #2563eb;
$secondary: #6b7280;
$success: #10b981;
$danger: #ef4444;
$warning: #f59e0b;
$info: #3b82f6;
```

### Typography
```scss
// Font families
$font-sans: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
$font-serif: ui-serif, Georgia, Cambria, 'Times New Roman', Times, serif;
$font-mono: ui-monospace, SFMono-Regular, 'SF Mono', Consolas, 'Liberation Mono', Menlo, monospace;

// Font sizes
$text-xs: 0.75rem;    // 12px
$text-sm: 0.875rem;   // 14px
$text-base: 1rem;     // 16px
$text-lg: 1.125rem;   // 18px
$text-xl: 1.25rem;    // 20px
$text-2xl: 1.5rem;    // 24px
$text-3xl: 1.875rem;  // 30px
$text-4xl: 2.25rem;   // 36px
$text-5xl: 3rem;      // 48px
$text-6xl: 3.75rem;   // 60px

// Font weights
$font-thin: 100;
$font-light: 300;
$font-normal: 400;
$font-medium: 500;
$font-semibold: 600;
$font-bold: 700;
$font-extrabold: 800;
$font-black: 900;

// Line heights
$leading-none: 1;
$leading-tight: 1.25;
$leading-snug: 1.375;
$leading-normal: 1.5;
$leading-relaxed: 1.625;
$leading-loose: 2;
```

### CSS Custom Properties
Available in `:root` for runtime theming and JavaScript access:
```css
--white, --black
--gray-50, --gray-100, --gray-200, --gray-300, --gray-400, --gray-500, --gray-600, --gray-700, --gray-800, --gray-900
--primary, --primary-light, --primary-dark
--secondary, --success, --danger, --warning, --info
```

## Complete Example

```scss
@use "mixins/index" as *;
@use "base/index" as *;

.card {
    @include container(20px);
    @include grid(1, 20px);
    @include transition-colors();
    background: $white;
    border-radius: 8px;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    
    @include respond(md) {
        @include grid(2, 30px);
    }
    
    &__header {
        @include flex-between(row, center, 15px);
        @include font($text-lg, $font-semibold, $leading-tight, $gray-900);
        padding-bottom: 15px;
        border-bottom: 1px solid $gray-200;
    }
    
    &__content {
        @include font($text-base, $font-normal, $leading-relaxed, $gray-700);
        @include text-truncate(3);
        padding: 15px 0;
    }
    
    &__footer {
        @include flex-between(row, center);
        @include font($text-sm, $font-medium, $leading-normal, $gray-500);
        padding-top: 15px;
        border-top: 1px solid $gray-100;
    }
    
    &:hover {
        @include scale(1.02);
        @include translate-y(-2px);
        @include transition-transform(0.3s, ease-out);
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.15);
    }
}

.hero-section {
    @include container();
    @include flex-center(column, 30px);
    @include aspect-ratio(16, 9);
    background: linear-gradient(135deg, $primary, $primary-dark);
    
    &__title {
        @include heading(1);
        @include text-selection($white, $primary);
        @include fade-in(0.8s);
        color: $white;
        text-align: center;
    }
    
    &__subtitle {
        @include font($text-xl, $font-normal, $leading-relaxed, rgba(255, 255, 255, 0.9), 0.8, 0.7);
        @include slide-in-up(0.6s, 30px);
        text-align: center;
        max-width: 600px;
    }
}

.responsive-grid {
    @include container();
    @include grid(4, 20px);
    
    @include respond(lg) {
        @include grid(3, 20px);
    }
    
    @include respond(md) {
        @include grid(2, 15px);
    }
    
    @include respond(sm) {
        @include grid(1, 10px);
    }
    
    &__item {
        @include transition-transform();
        
        &:hover {
            @include scale(1.05);
        }
    }
}
```

## Features

- **Zero Redundancy**: Only generates CSS for mixins you actually use
- **Modern Reset**: Comprehensive CSS reset with accessibility considerations
- **Responsive First**: Mobile-first approach with flexible breakpoint system
- **Performance Optimized**: Hardware acceleration support for smooth animations
- **Accessibility Ready**: Focus-visible support and reduced motion preferences
- **CSS Custom Properties**: Runtime theming support
- **Fallback Support**: Graceful degradation for older browsers (aspect-ratio fallback included)

## Browser Support

- Modern browsers (Chrome 60+, Firefox 60+, Safari 12+, Edge 79+)
- Graceful fallbacks for older browsers where applicable
- Automatic vendor prefixing recommended via autoprefixer