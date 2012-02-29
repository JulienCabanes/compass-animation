# Compass CSS Animation Mixins

Requirements : Make sure your Sass version is *3.2+*

Those Compass mixins allows you to play with CSS Animations stuffs like ```@keyframes``` and all…

Those mixins was written with [W3C specs](http://www.w3.org/TR/css3-animations/) in mind so if you know them, you know how to use it.

## How to use ?
```
// Single shortcut way 
@include animation(anim-1 2s linear infinite);

// Single property way
@include animation-delay(3s);

// Multiple shortcut way
@include animation(anim-1 1s ease infinite, demo-2 2s linear infinite);

// Multiple property way
@include animation-duration(10s, 4s);

// Forgot the shortcut arguments order ? There's a mixin for that too
@include animation-simple(
	$name: anim-2,
	$iteration-count: infinite,
	$duration: 10s,
);
```

## I already found a plugin for that
It seems like but it's not a fork from [this plugin](https://github.com/ericam/compass-animation)

## Prefixing the good way
This plugin is cool but it doesn't make use of default specs values and it unfortunately does something I disagree with : it considers *actual* browser support for prefixing.

Instead, those mixins will only rely on ```$experimental-support-for-vendor``` variables. So, if your experimental support is set for every browsers, those mixins will output prefixed ```@keyframes``` and ```animation-*``` properties for those browsers, not only the ones supporting CSS Animations today.

This is a more **future-proof** way of doing. For instance, Opera doesn't currently support CSS Animations but it's coming in a [near future](http://caniuse.com/#search=keyframe).

## Scoped prefixing
The *coolest* feature is something I called "scoped prefixing". The output from a prefixed animation like ```@-moz-keyframes``` will only contain ```-moz-``` prefixed properties, no ```-webkit-transform``` as it's useless. Avoiding CSS bloat is always good.
