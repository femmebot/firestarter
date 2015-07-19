# Sass Basics

#### Installing Sass

```
sass --version
```
If Sass isn't installed, go ahead and install it.
```
gem install sass
```

To run a very basic Sass file. In this example, we're using Atom as our text editor.
```
touch example.scss
atom example.scss
```
Add some css to your test.css file, save, then check.
```
sass example.scss

```

```
sass --watch .
```

To specify input/output:

```
sass --watch sass_directory/example.scss:css_directory/example.css
```


#### Nesting Selectors

Reference parent selectors using `&`. Supports CSS `>` to reference children (i.e., immediate descendant) of a parent.


#### Variables

Use `$` to create variables to replace repetitive declarations.
Can be used with Math operators to perform calculations.


#### Mixins

To define a mixin, add `@mixin` with optional argument(s).

```
@mixin circle($diam) {
  height: $diam;
  width: $diam;
  border-radius: $diam / 2;
}
```
```
.avatar {
  @include circle(60px);
  border: 1px solid #000;
}
```


#### Extending Selectors

replace `#` or `.` with `%` to create a placeholder variable that can be used with `@extend`


#### Color

```
$light-olive: #cfdccc;
$background: $light-olive;
$overlay-color: desaturate($background, 50%);
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

#### Importing Files

**Conventions**
Separate scss files into `_variables.scss`, `_mixins.scss`, `_globals.scss`, `pages/_about_us.scss` and `@import` each into `main.scss`
The order is important!

```
@import _reset.scss;

// Definitions
@import "_variables.scss";
@import "_mixins.scss";

// Global Styles
@import "_globals.scss";

// Page-Specific
@import "pages/_about_us.scss";
```

#### Extending Sass

Functions: Use for calculations. Must return value.

```
@function circle($height){
  @return $height / 2
}

img {
  height: 30px;
  width: 30px;
  border-radius: circle(30px);
}
```

#### Media Queries


#### Interpolation

interpolation syntax `#{$variable}`.

```
@mixin color_class($color){
  .#{$color} {
    color: $color;
  }
}

@include color_class(blue);
```

#### If/Else Statements

```
@mixin tint($color){
  @if $color ==  red {
    background-color: lighten($color, 80%);
  } @else {
    background-color: lighten($color, 50%);
  }
}

@include tint(yellow);
```
