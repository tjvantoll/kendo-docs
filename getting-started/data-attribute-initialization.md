---
title:  Data Attribute Initialization
slug: gs-data-attribute-initialization
tags:   101, Getting Started, widgets
Publish:    true
related:    gs-using-kendo-widgets, gs-data-attribute-initialization
---

# Data Attribute Initialization

In addition to the jQuery plugin initialization, each kendo widget can be initialized and configured by setting a `role` data attribute
on the target element and calling `kendo.init` on its element or any of its containers.

### Initialize a kendo DropDownList using a role attribute

    <div id="container">
        <select data-role="dropdownlist"></select>
    </div>
    <script>
        kendo.init($("#container"));
    </script>

The role attribute value is the name of the widget in lower case.

By default, `kendo.init` initializes all **web**/**dataviz** widgets. Kendo mobile applicaiton initializes all **mobile**, **web**, and **dataviz** widgets, in that priority.
This means that if an element with `data-role="listview" is found, a the mobile listview will be initialized, not the web one (which has the same role).
This behaviour can be overriden by specifying the full widget class name (with its namespace) in the role attribute.

    <div id="container">
        <div data-role="kendo.ui.ListView"></div>
    </div>
    <script>
        kendo.init($("#container"));
    </script>


### Configuration

Each widget configuration option can be specified via a data attribute on the respective element.
**Camel-cased options are translated to dash separated attributes**. For instance, dataTextField option of the autocomplete widget can be specified with `data-text-field="foo"` attribute.

> Options, which start with `data` do not require an additional "data" in the attribute name.

### Configure kendo DropDownList with data attributes

    <select data-role="dropdownlist" data-delay="1000">
    </select>

### Events / DataSource

A widget event can be bound using data attributes as well. The value of the data attribute will be resolved to a function, available in the global scope.

#### Bind to dropDownList change event

    <select data-role="dropdownlist" data-change="onChange">
    </select>
    <script>
        function onChange(e) {
            // ...
        }
    </script>

Event handlers also support member functions, using JavaScript syntax. An event handler can be specified using `foo.bar`, resolving to the member method `bar` of the object `foo`.

#### Bind to dropDownList change event to a member function

    <select data-role="dropdownlist" data-change="foo.bar">
    </select>
    <script>
    var foo = {
        bar: function(e) {
            // ...
        }
    }
    </script>

The declarative DataSource binding works in the same way, expecting a DataSource object or an array.


#### Specify DropDownList DataSource

    <select data-role="dropdownlist" data-source="source">
    </select>
    <script>
        var source = ["foo", "bar", "baz"];
    </script>

### Templates

For widgets that have template configuration options, the data attribute value will be resolved to an `id` of a `script`
element, with the contents of the template.

#### Specify DropDownList Template

    <select data-role="dropdownlist" data-template="foo"></select>

    <script id="foo" type="script/x-kendo-template">
        <span>#:data.Name</span>
    </script>

