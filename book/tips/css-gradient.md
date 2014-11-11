Title: Fixing CSS Gradients Incompatibilities
Category: css
Created: 2014-11-11
Updated: 2014-11-11

## Description
CSS Gradients are a way to create linear or radial gradients in a box with CSS properties. They are specified by W3C in the [CSS Image Values and Replaced Content Module Level 3][gradients].

## How to detect
The Web site often shows a missing background, very often in menus and banners. For example, the text is white on white and is not readable or slightly visible. This is probably due to the use of gradients which are not compatible with your current browser. Very often, the site is using an only WebKit syntax. (just an example)

    nav ul li {
        /* here some other properties */
        background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#97b8e1), color-stop(20%,#2E70C2), color-stop(80%,#225491), color-stop(100%,#0c1f36));
    }


## How to fix it
The current syntax for [linear gradient](http://dev.w3.org/csswg/css-images-3/#linear-gradients) is defined by

    linear-gradient(
      [ <angle> | to <side-or-corner> ]? ,
      <color-stop-list>
    )

To fix the previous example, you would write:

    nav ul li {
        /* here some other properties */
        background: #97b8e1;
        background: linear-gradient(to bottom, #97b8e1 0%,#2e70c2 20%,#225491 80%,#0c1f36 100%); /* W3C */
    }

As you can see, this is more compact. Another good tip is to add a default background color in your CSS, so that old browsers not supporting the gradients fall back on a plain background color. It will avoid the issue of text being not readable.

There are tools to help you create the appropriate CSS. [Ultimate CSS Gradient Generator](http://www.colorzilla.com/gradient-editor/) has an **import from CSS** that will take your WebKit property and convert it to all possible syntaxes.

## Benefits
Converting your Web site to standard CSS gradients will make your Web site forward compatible and then reach a lot more customers. This is currently [supported by all main browsers](http://caniuse.com/#feat=css-gradients).

## References
* [CSS3 gradients From #000 to #fff in 45 minutes](http://lea.verou.me/css3-gradients/)

[gradients]: http://dev.w3.org/csswg/css-images-3/#gradients