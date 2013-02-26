#A replacement @fontface mixin
## Based on Paul Irish's Bulletproof Method.

[Bulletproof @fontface implementation syntax - by Paul Irish](http://paulirish.com/2009/bulletproof-font-face-implementation-syntax/)

&nbsp;

---


**His most recent version is the most solid way to serve webfonts as well as as remove the text from duplicating on iOS devices.**

#####My above mixin takes this as input

	@include font-face(FontName);



#####And outputs this
**Assuming your fonts director is set up as `/fonts` in your config.rb file**

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