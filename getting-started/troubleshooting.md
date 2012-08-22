---
title: Troubleshooting
slug: widget-troubleshooting
publish: true
---

# Troubleshooting

This page provides solutions for common problems you may encounter while working with Kendo UI widgets.

## Known JavaScript Errors

### JavaScript error that jQuery is unavailable or undefined

If jQuery is not included (or is included after the Kendo JavaScript files) the Kendo UI widgets will not function as expected.
The following JavaScript errors will be thrown (depending on the browser):

* ReferenceError: jQuery is not defined (in Google Chrome and FireFox)
* 'jQuery' is undefined (in Internet Explorer)

#### Solution
Make sure that jQuery is included **before** the Kendo JavaScript files.

### JavaScript error that Kendo widgets are unavailable or undefined

If jQuery is included more than once in the page all existing jQuery plugins (including Kendo UI) will be wiped out. Will also occur
if the [required Kendo JavaScript files](/getting-started/javascript-dependencies) are not included.

The following JavaScript errors will be thrown (depending on the browser):

* TypeError: Object #<Object> has no method 'kendoGrid' (in Google Chrome)
* TypeError: $("#Grid").kendoGrid is not a function (in FireFox)
* Object doesn't support property or method 'kendoGrid' (in Internet Explorer 9+)
* Object doesn't support this property or method (in older versions of Internet Explorer)

> **Note**: All Kendo widgets will be affected by this problem, not just the Kendo Grid. Just the error message will be different e.g. "kendoChart is not a function" or "Object has no method kendoEditor".

#### Solution
Make sure jQuery is not included more than once in your page. Remove any duplicate `script` references to jQuery. Include all [required Kendo JavaScript files](/getting-started/javascript-dependencies).

## Certain Kendo UI versions are not available on CDN

Kendo CDN is updated only when a new official version is released (major or service pack). Internal builds are not uploaded to CDN.

## The widget object is undefined after loading a page through AJAX

Usually caused when the page loaded via AJAX contains a script reference to jQuery. When jQuery is re-initialized, all jQuery-based data attributes are cleared, including the data("kendoWidget") attribute that holds the Kendo UI widget object.

The solution is to load a partial HTML fragment that doesn't contain any unneeded jQuery references, or use an iframe to load the complete page.

#### Example: Problem

    $("#dialog").kendoWinodow({
        // loads complete page
        content: "/foo"
    });

#### Example: Solution

    $("#dialog").kendoWinodow({
        // load complete page...
        content: "/foo",
        // ... and show it in an iframe
        iframe: true
    });

    // or

    $("#dialog").kendoWinodow({
         // load partial page, without jQuery reference
        content: "/foo"
    });
