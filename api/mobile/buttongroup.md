---
title: kendo.mobile.ui.ButtonGroup
meta_title: Kendo UI Mobile ButtonGroup API reference
meta_description: Learn how to define the initially selected button, select a button and get the currently selected button.
slug: mobile-kendo.mobile.ui.buttongroup
tags: api,mobile
publish: true
---

# kendo.mobile.ui.ButtonGroup

## Configuration

### index `Number`

Defines the initially selected Button.

## Methods

### current

Get the currently selected Button.

#### Returns

`jQuery` the currently selected Button.

### select

Select a Button.

#### Example

    var buttongroup = $("#buttongroup").data("kendoMobileButtonGroup");

    // selects by jQuery object
    buttongroup.select(buttongroup.element.children().eq(0));

    // selects by index
    buttongroup.select(1);

#### Parameters

##### li `jQuery | Number`

LI element or index of the Button.

## Events

### select

Fires when a Button is selected.

#### Handle select event

    <ul id="buttongroup" data-role="buttongroup">
      <li>Option 1</li>
      <li>Option 2</li>
    </ul>

    <script>
     $("#buttongroup").data("kendoMobileButtonGroup").bind("select", function(e) {
         //handle select event
     }
    </script>
