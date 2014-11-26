Title: Fixing Flexbox Incompatibilities
Category: css
Created: 2014-11-10
Updated: 2014-11-10

## Description

Flexbox is a layout technology helping to manipulate the boxes. The [flexbox][] specification went through three iterations. A Web site might be using a flexbox syntax which is either

* only compatible with WebKit rendering engines
* compatible with the second generation syntax.

These are not supported in every browsers.

## How to detect

When viewed on a browser which is not Webkit, boxes and images are not aligned. The CSS code contains property such as:

    display:-webkit-box;
    display:box;

@@insert here an image@@

## How to fix it

There is not a one-to-one total equivalence of the old and new property, but it is usually not too hard to fix. The first step is often done, by adding the most recent version of the syntax. For example, let's take a common markup such as:

    nav {
        background: #fff;
        border-bottom: 1px solid #dadada;
        display: -webkit-box;
        padding: 4px 0;
        width: 100%;
    }

We would modify it by adding the appropriate `display: flex;`

    nav {
        background: #fff;
        border-bottom: 1px solid #dadada;
        display: -webkit-box;
        display: flex;
        padding: 4px 0;
        width: 100%;
    }

and from there, we would modify the other flexbox properties. We decided to keep the old properties around, because some of the WebKit devices are not maintained anymore with new versions of iOS and Safari. It means that if we retire too soon these properties, we create this time a Web compatibility issues for users of old devices.

Some properties are more subtle than others. You may have to read about their definitions to find out the right properties. For example, the equivalent of `-webkit-box-flex: 1;` is `flex-grow: 1;`.

## Benefits

By switching to the new CSS Flexbox syntax, the Web site is [compatible with more browsers](http://caniuse.com/#feat=flexbox). It basically extends the market share outreach of the Web site, instead of just the WebKit platform. It also makes the Web site ready for the future, when the old syntax is not supported anymore.

## References

* CSS Tricks provides an helpful resource for [Mixing Old and New syntax](http://css-tricks.com/using-flexbox/).
* [Flexy Boxes](http://the-echoplex.net/flexyboxes/) will generate old and new syntax for you and will help to visualize the rendering.

[flexbox]: http://dev.w3.org/csswg/css-flexbox/
