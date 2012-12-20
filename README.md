A compass replacement @mixin that outputs @fontfaces in line with Paul Irish's Bulletproof Method.
===

His most recent version is the most solid way to serve webfonts as well as as remove the text from duplicating on iOS devices.
---
http://paulirish.com/2009/bulletproof-font-face-implementation-syntax/

My above mixin takes this as input:
>@include font-face(
>  'OpenSans-Regular', 
>    font-files(
>	  'OpenSans-Regular.woff', woff,
>	  'OpenSans-Regular.otf', opentype,
>	  'OpenSans-Regular.svg', svg ),
>  'OpenSans-Regular.eot'
>);

and outputs this:
>@font-face {
>  font-family: "OpenSans-Regular";
>  src: url('../fonts/OpenSans-Regular.eot');
>  src: local("?"), url('../fonts/OpenSans-Regular.woff') format('woff'), url('../fonts/OpenSans-Regular.otf') format('opentype'), url('../fonts/OpenSans-Regular.svg') format('svg');
>}
>
>@media screen and (max-device-width: 480px) {
>  @font-face {
>    font-family: "OpenSans-Regular";
>    src: local("?"), url('../fonts/OpenSans-Regular.woff') format('woff'), url('../fonts/OpenSans-Regular.otf') format('opentype'), url('../fonts/OpenSans-Regular.svg') format('svg');
>  }
>}

The original compass @fontface goes like this:
>@mixin font-face($name, $font-files, $eot: false, $weight: false, $style: false) {
>  $iefont: unquote("#{$eot}?#iefix");
>  @font-face {
>    font-family: quote($name);
>    @if $eot {
>      src: font-url($eot);
>      $font-files: font-url($iefont) unquote("format('eot')"), $font-files; }
>    src: $font-files;
>    @if $weight {
>      font-weight: $weight; }
>    @if $style {
>      font-style: $style; } } }