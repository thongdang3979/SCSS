# SCSS Framework

Lightweight SCSS framework with zero-redundancy design. Only generates CSS for mixins you actually use.

## File Structure

```
scss/
├── base/
│   ├── _reset.scss
│   ├── _color.scss
│   ├── _font.scss
│   └── base.scss
├── mixins/
│   ├── _flexbox.scss
│   ├── _layout.scss
│   ├── _responsive.scss
│   ├── _typography.scss
│   ├── _transition.scss
│   ├── _animation.scss
│   ├── _transform.scss
│   └── mixins.scss
└── main.scss
```

## Installation

```sh
npm install -g sass
```

## Usage

```sh
sass --watch scss/.:css/. --style compressed
```

## Import

```scss
@import "mixins/mixins";
@import "base/base";
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

### Breakpoints Available
- `xs` (0+), `sm` (576px+), `md` (768px+), `lg` (992px+), `xl` (1200px+), `xxl` (1400px+)
- `mobile` (max 767px), `tablet` (max 991px), `laptop` (max 1199px), `desktop` (1200px+)
- Custom pixel values: `@include respond(600px)`

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
@mixin rotate($angle)
@mixin skew($x, $y)
@mixin transform-origin($origin)
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
```

## Variables

### Colors
```scss
$white, $black
$gray-50, $gray-100, ..., $gray-900
$primary, $primary-light, $primary-dark
$secondary, $success, $danger, $warning, $info
```

### Typography
```scss
// Sizes
$text-xs, $text-sm, $text-base, $text-lg, $text-xl
$text-2xl, $text-3xl, $text-4xl, $text-5xl, $text-6xl

// Weights
$font-thin, $font-light, $font-normal, $font-medium
$font-semibold, $font-bold, $font-extrabold, $font-black

// Line Heights
$leading-none, $leading-tight, $leading-snug
$leading-normal, $leading-relaxed, $leading-loose

// Families
$font-sans, $font-serif, $font-mono
```

### CSS Variables
Available in `:root` for runtime theming:
```css
--white, --black, --primary, --success, --danger, --warning
--gray-50, --gray-100, ..., --gray-900
```

## Complete Example

```scss
.card {
    @include container();
    @include grid(1, 20px);
    @include transition-colors();
    background: $white;
    
    @include respond(md) {
        @include grid(2, 30px);
    }
    
    &-header {
        @include flex-between();
        @include font($text-lg, $font-semibold);
    }
    
    &-content {
        @include font($text-base, $font-normal, $leading-relaxed);
        @include text-truncate(3);
    }
    
    &:hover {
        @include scale(1.02);
        @include translate-y(-2px);
    }
}
```