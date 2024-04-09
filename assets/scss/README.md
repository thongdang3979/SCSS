# Intall SASS
```
npm install -g sass
```

# Use SASS
```
cd to/path/scss

sass --watch scss/.:css/. --style compressed
```

# Import Defind Mixin
```
@import 'function.scss';
```

# Using Mixin
```
<!-- String -->
@include customFont(50px, 900, 100%, red, #{25px}, 0.7);

<!-- Number Ratio (0 - 1) -->
@include customFont(50px, 900, 100%, red, 0.8, 0.7);

<!-- Transition -->
@include customTransition(all 0.15s ease-out);

<!-- FlexBox -->
@include flexCustome(row, nowrap, center, space-between, center, 20px);

@include flexBoxWidthCustome(20px, 2, 2, 1);

<!-- Responsive -->
@include responsiveFormat(Mobile){
                
}
```

# Website Autoprefixed
https://autoprefixer.github.io/