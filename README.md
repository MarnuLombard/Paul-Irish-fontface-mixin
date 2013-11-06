#A replacement @fontface mixin
## Based on Paul Irish's Bulletproof Method.

[Bulletproof @fontface implementation syntax - by Paul Irish](http://paulirish.com/2009/bulletproof-font-face-implementation-syntax/)

&nbsp;

---


**His most recent version is the most solid way to serve webfonts as well as as remove the text from duplicating on iOS devices.**

#####My above mixin takes this as input

	@include font-face(FontName);
or

	@include font-face(FontName, '../custom/font/directory/');



#####And outputs this

	@font-face {
	  font-family: "FontName";
	  src: url('../fonts/FontName.eot');
	  src: local("?"), url('../fonts/FontName.woff') format('woff'), url('../fonts/FontName.otf') format('opentype'), url('../fonts/FontName.svg#FontName') format('svg');
	}

	@media screen and (max-device-width: 480px) {
	  @font-face {
	    font-family: "OpenSans-Regular";
	    src: url('../fonts/FontName.woff') format('woff'), url('../fonts/FontName.otf') format('opentype'), url('../fonts/FontName.svg') format('svg');
	  }
	}

---
####Version History

1.3.0 remove need for compass' `font-url()`

1.2.1 add option for custom fon directory

1.2.0 drastically simplify the mixin's arguements

1.0.0 Initial release