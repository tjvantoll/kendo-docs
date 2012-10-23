---
title: Swipe
meta_title: Documentation for Kendo UI Mobile swipe component
meta_description: How to handle user horizontal swiping events in your HTML5 mobile app by using mobile swipe component. Learn how to register a swipe event for a given jQuery selector.
slug: gs-mobile-swipe
tags: getting-started,mobile
publish: true
---

# Swipe

The mobile swipe component handles user horizontal swiping events.

## Getting Started

To register a swipe event for a given jQuery selector, use the `kendoMobileSwipe` jQuery plugin method.

### swipe event handling

    <div>
        <p>Foo</p>
        <p>Bar</p>
    </div>

    <script>
        $("p").kendoMobileSwipe(function(e) {
            console.log("You swiped" + e.target.text());
        });
    </script>

The event handler accepts a parameter with the following fields:

*   **target** - The DOM element which was swiped
*   **direction** - The swipe direction. Can be either `left` or `right`.
*   **drag** - An instance of the [kendo.Drag](/api/framework/drag) component, containing additional information about the drag event sequence that generated the swipe.

