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
```

# Website Autoprefixed
https://autoprefixer.github.io/