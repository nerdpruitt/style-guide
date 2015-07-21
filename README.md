# Base, Layout, Module, State
Division of style responsibilities.

# JavaScript Selectors
A selector that is used only for JavaScript logic

`.js-*`

_Examples:_
* `.js-open`
* `.js-needs-attention`

```
<button class="btn js-submit">Submit</button>
```

# State Selector
Shared by Sass and JavaScript and/or Handlebars. Should never be styled directly; only styled as an adjoining.

`.is-*`
`.has-*`

_Examples:_
* `.is-selected`
* `.has-error`

```
.btn {
  background-color: red;

  &.is-pressed {
    box-shadow: inset 0 1px 0 rgba(0, 0, 0, 0.25);
  }
}
```

# BEM Style Selector
Block, Element, Modifier. Used only in Sass. All modular and such. Favor multiple classes over @extends or it gets all wacky.

_Examples:_
* `.list`
* `.list__heading`
* `.list__heading--small`
* `.list__heading--large`
* `.list__heading--all-caps`


```
<ul class="list">
  <li class="list__item">
    <h2 class="list__heading">Heading</h2>
    <h3 class="list__heading list__heading--small">Smaller Heading</h3>
    <p class="list__text">And a complete sentence.</p>
  </li>
  <li class="list__item"></li>
  <li class="list__item"></li>
</ul>
```

* http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/
* http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/


# Sass
Rule sets should be ordered as follows:

* @extend
* @include without @content
* properties
* @include with @content
* nested rule sets


```
.element {
  $scoped-variable: whatever;
  @extend .other-element;
  @include mixin($argument);
  property: value;

  @include breakpoint($size) {
    /* styles here */
  }

  &:pseudo {
    /* styles here */
  }

  .nested {
    /* styles here */
  }
}
```

# Comment Levels
```
// *************************************
//
//   First Level
//   -> Description
//
// *************************************

// -------------------------------------
//   Second Level
// -------------------------------------

// ----- Third Level ----- //

// Fourth Level
```

# Using @extend and @mixin
`@extend` should only be used in a single file. `@mixin` should be used when working across different partials.

* http://csswizardry.com/2014/11/when-to-use-extend-when-to-use-a-mixin/
* http://jedmao.ghost.io/2014/12/09/stop-using-sass-extend-to-reduce-bloat/
* https://tech.bellycard.com/blog/sass-mixins-vs-extends-the-data/
