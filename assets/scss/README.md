<!-------- Intall SASS ------->
npm install -g sass

<!-------- Use SASS -------->
sass --watch scss/.:css/. --style compressed
@import 'function.scss';

<!-------- Use Mixin with type of -------->

<!-- String -->
@include customFont(50px, 900, 100%, red, #{25px}, 0.7);

<!-- Number -->
@include customFont(50px, 900, 100%, red, 25px, 0.7);


<!------- Website Autoprefixed-------->
https://autoprefixer.github.io/