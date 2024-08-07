# Install SASS
```sh
npm install -g sass
```

# Use SASS
```sh
cd to/path/scss

sass --watch scss/.:css/. --style compressed
```

# Import Defined Mixin
```css
@import "mixin/mixin";
@import "defind/defind";
```

# Using Mixin

## Font
- String
    ```css
    @include customFont(50px, 900, 100%, red, #{25px}, 0.7);
    ```
- Number Ratio (0 - 1)
    ```css
    @include customFont(50px, 900, 100%, red, 0.8, 0.7);
    ```

## Transition
```css
@include customTransition(all 0.15s ease-out);
```

## FlexBox
```css
@include flexCustome(row, nowrap, center, space-between, center, 20px);
```

```css
@include flexCenter(row, nowrap);
```

```css
@include flexBoxWidthCustome(20px, 2, 2, 1);
```

## Responsive
```css
@include responsiveFormat(Mobile){
    .example{
        background: red;
    }
}
```

## Website Auto prefixed
https://autoprefixer.github.io/