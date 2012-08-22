---
title: Troubleshooting
slug: widget-troubleshooting
publish: true
---

# Troubleshooting

This page provides solutions for common problems you may encounter while working with Kendo UI widgets.

## Known JavaScript Errors

### $ is undefined or jQuery is undefined

Means that jQuery is not included in the page or is included **after** the Kendo UI JavaScript files. The solution is to include jQuery **before** the Kendo UI JavaScript files.

### kendo is undefined

Will occur if the JavaScript file(s) which define(s) that particular Kendo Widget is(are) not included. Will also happen if jQuery is included twice. Make sure that the [required JavaScript files](/getting-started/javascript-dependencies)
are included and that jQuery is included **only once**.

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
