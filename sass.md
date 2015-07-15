# Sass Basics

#### Color

```
$light-olive: #cfdccc;
$background: $light-olive;
$overlay-color: desaturate($background, 50%)
$blended-color: mix(#fe0, #9ff);
$text-color: #3a3737;
$hyperlink-color: #ff5154;
$highlighted-text: lighten($text-color, 20%);
$button-color: complement($background);


body {
  background-color: $light-olive;
  font-family: sans-serif;
  color: $text-color;
}

a {
  color: $hyperlink-color;
  span {
    color: $highlighted-text;
  }
}
```

**Conventions**
Separate scss files into `_variables.scss`, `_mixins.scss`, `_globals.scss`, `pages/_about_us.scss`and ``@import` each into `main.scss`
The order is important!

```
// Definitions
@import "_variables.scss";
@import "_mixins.scss";

// Global Styles
@import "_globals.scss";

// Page-Specific
@import "pages/_about_us.scss";
```
