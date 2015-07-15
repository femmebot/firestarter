# CSS Selectors

Notes from O'Reilly webcast, [CSS Selectors with Rachel Andrew](https://event.on24.com/eventRegistration/EventLobbyServlet?target=lobby20.jsp&eventid=1013158&sessionid=1&key=F1BE14FF965B659861E1033DF49568F5&eventuserid=121203768)

Target elements based on document position without having to create classes.
'Common sense' selectors lets you target elements based on position or type.

#### Attribute Selectors

```
form input[type="text"] { }
form input[type="submit"] { }
```
use input type to target specific form input


```
label[for="fContact"] { }
```
Use `for` attribute to select a specific input type.

```
a[href ^="mailto:"] {
  padding-right: 20px;
  background-image: url(email.png);
  background-repeat: no-repeat;
  background-position: right center;
}
```
use `^=` to match href that begins with `mailto:`

#### Structural Pseudo-Class Selectors

Select elements based on their position in the document

```
a:link {}
a:visited {}
```
Examples of pseudo-class selectors


```
a:hover {}
a:active {}
```
Examples of dynamic pseudo-classes


`:first-child` applied only to first paragraph in a div
```
<div>
  <p> ... </p>
  <p> ... </p>
  <p> ... </p>
</div>
```

```
p:first-child { font-size: 36px; }
```

can be appended to any selector including classes and IDs

```
.classname:first-child
```

```
#idname:last-child
```

`:nth-child()` can be used to target select multiple elements based on their position in the document tree. Can be used, for example, to create striped table rows.

```
tr:nth-child(odd) td { background-color: #ddd; }
```

target a specific row:
```
tr:nth-child(3) td { background-color: #ddd; }
```

can be used with math calculations:
```
tr:nth-child(2n+1) td { background-color: #ddd; }
```

Also have `:nth-of-type` which is similar to :nth-child but targets only elements of the same type
```
p:nth-of-type(odd) { background-color: #ddd; }
```

`:only-child` targets elements that are solo children of a parent. Useful if you have a list style that works when you have multiple items in a list but want to style single list items differently

```
li { list-style-type: disc; }
li:only-child { list-style-type: none; }
```

`:empty` matches an element if it's empty

```
p { padding: 20px 0; }
p:empty { padding: 0; }
```

#### UI Element States

Pseudo-Classes for use with web forms

`:checked` the checked/selected state of a radio button or checkbox
```
.agreeterms { border: 1px solid #ccc; }
.agreeterms:checked { border: 2px solid green; }
```

`:enabled` or `:disabled` detects whether input is enabled or disabled
```
input:enabled { color: #000; }
input:disabled { color: #ddd; }
```

#### The Input Pseudo-Classes (Level 4)

`:default`
`:valid`
`:invalid`
`:in-range`
`:out-of-range`
`:required`
`:optional`
`:read-only`
`:read-write`
These link to HTML5 attributes. (Browser must support HTML5)

```
<input type="text" name="fName" id="fName" required="required" />
<input type="email" name="fEmail" id="fEmail" required="required" placeholder="name@example.com" />
```

In this example, using above form, we can display an error image when user provides invalid input by chaining several pseudo-classes
```
input:focus:required:invalid { background: url(error.png) no-repeat; }
```
```
input:focus:required:valid { background: url(valid.png) no-repeat; }
```

#### The Negation Pseudo_Class

`:not(selector)`


#### Pseudo-Elements

Matching virtual elements that don't explicitly exist in the document tree. Pseudo-Elements act as if a new element, such as `<span>` was added to your document and then the style applied to that.

`:first-letter` in the example below used to style a drop cap

```
.wrapper:first-letter { font-size: 200%; font-weight: bold; color: red; }
```

`:first-line` for formatting the first line of text

```
.wrapper:first-line { text-transform: uppercase; }
```

`:before` and `:after` render the content before or after the element when using generated content
```
.content:before { content: "Start here:"; }
```
example uses for inserting copyright info, adding bubble arrow or automatically inserting clearfix hack for floats


#### Combinators

Combining selectors to target elements

* Descendant Selector: Selects all descendants of a specified parent
* Child Selector: `>` Selects all children of a specified parent `li { color: 000; } ul > li  { color: red; }`