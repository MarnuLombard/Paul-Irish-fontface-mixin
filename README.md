#A compass replacement @mixin that outputs @fontface 
## in line with Paul Irish's Bulletproof Method.


######His most recent version is the most solid way to serve webfonts as well as as remove the text from duplicating on iOS devices.

[Bulletproof @fontface implementation syntax - by Paul Irish](http://paulirish.com/2009/bulletproof-font-face-implementation-syntax/)

&nbsp;


**My above mixin takes this as input:**

	@include font-face(
		'OpenSans-Regular', 
	    font-files(
		  'OpenSans-Regular.woff', woff,
		  'OpenSans-Regular.otf', opentype,
		  'OpenSans-Regular.svg', svg ),
	  'OpenSans-Regular.eot'
	);

**and outputs this:**

	@font-face {
	  font-family: "OpenSans-Regular";
	  src: url('../fonts/OpenSans-Regular.eot');
	  src: local("?"), url('../fonts/OpenSans-Regular.woff') format('woff'), url('../fonts/OpenSans-Regular.otf') format('opentype'), url('../fonts/OpenSans-Regular.svg') format('svg');
	}

	@media screen and (max-device-width: 480px) {
	  @font-face {
	    font-family: "OpenSans-Regular";
	    src: local("?"), url('../fonts/OpenSans-Regular.woff') format('woff'), url('../fonts/OpenSans-Regular.otf') format('opentype'), url('../fonts/OpenSans-Regular.svg') format('svg');
	  }
	}