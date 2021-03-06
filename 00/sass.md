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

#### Loops

`@for` and `@each`

```
@for $i from 1 through 3 {
  .item-#{$i} { width: 2em * $i; }
}
```

Above example gets compiled to:

```
.item-1 {
  width: 2em; }
.item-2 {
  width: 4em; }
.item-3 {
  width: 6em; }
```

`@each` takes a list and applies the styles to each list item

```
@each $social in facebook, twitter, instagram, tumblr {
  .#{$social}-icon {
    background-image: url('../images/#{$social}.svg');
  }
}
```

#### Advanced Mixins

```
@mixin social-icons ($networks...) {
  @each $social in $networks {
    .#{$social}-icon {
      background-image: url('../images/#{$social}.svg');
    }
  }  
}

@include social-icons(facebook, twitter, instagram, tumblr);
```

Alternately, we can eliminate the ellipsis and use a space-separated list:
```
@mixin social-icons ($networks) {
  @each $social in $networks {
    .#{$social}-icon {
      background-image: url('../images/#{$social}.svg');
    }
  }  
}

@include social-icons(facebook twitter instagram tumblr);
@include social-icons(github);
```

Mixins can have default values, and you can also pass named arguments and ignore the order when including the mixin

```
@mixin box ($size, $color, $display: block) {
  .box {
    height: $size;
    width: $size;
    background-color: $color;
    display: $display;
  }
}

@include box ($color: grey, $size: 30px);
```
