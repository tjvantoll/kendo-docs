---
title:  Using Kendo Widgets
meta_title: Using Kendo UI widgets
meta_description: See how to easily initialize jQuery-powered Kendo UI widgets, set configuration, get the client object, use event binding.
slug: gs-using-kendo-widgets
tags:   101, Getting Started, widgets
Publish:    true
related:    gs-downloading-kendo, gs-data-attribute-initialization
---

# Using Kendo UI Widgets

## Widget initialization

Since Kendo UI is built on top of jQuery, using the Kendo UI widgets is very intuitive.
For example, to use Kendo AutoComplete, first you write some HTML:

    <input id="myAutoComplete" />

Then, to initialize this HTML input and give it the Kendo AutoComplete functionality and styling, a single jQuery JavaScript line is required:

    $("#myAutoComplete").kendoAutoComplete(["Apples", "Oranges", "Grapes"]);

## Widget configuration

To set additional configuration on widgets you can provide a JavaScript object to the widget constructor.

      $("#customers").kendoGrid({
          columns:[
              {
                  field: "FirstName",
                  title: "First Name"
              },
              {
                  field: "LastName",
                  title: "Last Name"
          }],
          dataSource: {
              data: [
                  {
                      FirstName: "Joe",
                      LastName: "Smith"
                  },
                  {
                      FirstName: "Jane",
                      LastName: "Smith"
              }]
          }
      });

The specific property names and configuration options for each widget can be found in the [API reference](jhttp://docs.kendoui.com/api) section of this site.

## Getting the widget client object

The widget client object is preserved in the jQuery [data store](http://docs.jquery.com/core/data "jQuery data store") for the corresponding element.
The following code snippet shows how to get the client object of the grid widget.

    var customers = $("#customers").data("kendoGrid");

> The name of the data key is built by adding "kendo" prefix to the name of the type of widget being referenced

## Widget event binding

There are two ways to subscribe to Kendo UI widget events:

*   Provide a handler in the configuration during widget initialization
*   Using the **bind** method

### Subscribing during widget initialization

     $("#products").kendoAutoComplete({
        change: onChange,
        close: onClose,
        open: onOpen
    });


### Subscribing via the `bind` method

    var autoComplete = $("#products").data("kendoAutoComplete");
    autoComplete.bind("change", onChange);

The handler is a callback function, as shown below. Within the handler, the keyword `this` refers to the Kendo widget to which the handler is subscribed.

    <script>
     function onChange(args) {
          //"this" refers to the AutoComplete widget that triggers the event

          console.log(this.value()); // outputs the value of the widget
     }
    </script>
