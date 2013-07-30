---
title: kendo.mobile.ui.ScrollView
meta_title: Configuration, methods and events of Kendo UI Mobile ScrollView
meta_description: You will learn how to configure Mobile ScrollView widget, update the scrollview HTML content and scroll to a given page by using methods.
slug: api-mobile-scrollview
relatedDocs: gs-mobile-scrollview
tags: api,mobile
publish: true
---

# kendo.mobile.ui.ScrollView

Represents the Kendo UI Mobile ScrollView widget. Inherits from [kendo.mobile.ui.Widget](/api/framework/mobilewidget).

## Configuration

### autoBind `Boolean`*(default: true)*

 If set to false the widget will not bind to the data source during initialization. In this case data binding will occur when the change event of the data source is fired. By default the widget will bind to the data source specified in the configuration.

 **Applicable only in data bound mode.**

### bounceVelocityThreshold `Number`*(default: 1.6)*

 The velocity threshold after which a swipe will result in a bounce effect.

### contentHeight `Number|String`*(default: "auto")*

The height of the ScrollView content. Supports `100%` if the scrollview is embedded in a stretched view and the scrollview element **is an immediate child** of the view element.

#### Stretched scrollview

    <div data-role="view" data-stretch="true">
        <div data-role="scrollview" data-content-height="100%">
            <div data-role="page">This page will stretch to fit the entire view height</div>
            <div data-role="page">This page will stretch to fit the entire view height</div>
            <div data-role="page">This page will stretch to fit the entire view height</div>
        </div>
    </div>

### dataSource `kendo.data.DataSource | Object`

 Instance of DataSource that the mobile ScrollView will be bound to. *If DataSource is set, the widget will operate in data bound mode.*

 > **Important:** In case the total amount of displayed data is large, it is recommended to turn off the pager by setting `enablePager: false` in the configuration options or via `data-enable-pager="false"` data attribute.

### duration `Number`*(default: 300)*

 The milliseconds that take the ScrollView to snap to the current page after released.

### emptyTemplate `String`*(default: "")*

 The template which is used to render the pages without content. By default the ScrollView renders a blank page.

 **Applicable only in data bound mode.**

### enablePager `Boolean`*(default: true)*

 If set to true the ScrollView will display a pager. By default pager is enabled.

### itemsPerPage `Number`*(default: 1)*

 Determines how many data items will be passed to the page template.

 > **Important:** In order ensure smooth scrolling the **pageSize of the DataSource should be 6 times itemsPerPage amount** or higher. For example, if itemsPerPage is set to 4, then the pageSize must be 24 (4*6) or higher.

 **Applicable only in data bound mode.**

### page `Number`*(default: 0)*

 The initial page to display.

### pageSize `Number`*(default: 1)*

Multiplier applied to the snap amount of the ScrollView. By default, the widget scrolls to the next screen when swipe. If the `pageSize` property is set to `0.5`, the ScrollView will scroll by half of the widget width.

 **Not applicable in data bound mode.**

### template `String`*(default: "#:data#")*

 The template which is used to render the content of pages. By default the ScrollView renders a div element for every page.

 **Applicable only in data bound mode.**

#### Example: single item template

    <script id="scrollview-template" type="text/x-kendo-template">
        <p>#= ProductName #</p>
    </script>

#### Example: multiple items template (data is accessed via `data[index].fieldName`)

    <script id="scrollview-template" type="text/x-kendo-template">
        <div>
            <p>#= data[0].ProductName #</p>
        </div>
        <div>
            <p>#= data[1].ProductName #</p>
        </div>
    </script>

    <div data-role="view" data-stretch="true" data-init="onInit">
        <div id="scrollview"></div>
    </div>

    <script>
        var app = new kendo.mobile.Application();

        function onInit() {
            $("#scrollview").kendoMobileScrollView({
                dataSource: {
                    type: "odata",
                    transport: {
                        read: {
                            url: "http://demos.kendoui.com/service/Northwind.svc/Products"
                        }
                    },
                    serverPaging: true,
                    pageSize: 30
                },
                itemsPerPage: 2,
                template: $("#scrollview-template").html(),
                contentHeight: 120,
                enablePager: false
            });
        }
    </script>

### velocityThreshold `Number`*(default: 0.8)*

 The velocity threshold after which a swipe will navigate to the next page (as opposed to snapping back to the current page).

## Methods

### content

Update the scrollview HTML content.

> **Important:** This method is **not** supported in data bound mode.

#### Example

    <div data-role="scrollview" id="scrollview"></div>

    <script>
       $("#scrollview").data("kendoMobileScrollView").content("<span>Foo</span>");
    </script>

#### Parameters

##### content `String | jQuery`

the new scrollView content.

### destroy
Prepares the **ScrollView** for safe removal from DOM. Detaches all event handlers and removes jQuery.data attributes to avoid memory leaks. Calls destroy method of any child Kendo widgets.

> **Important:** This method does not remove the ScrollView element from DOM.

#### Example

    var scrollView = $("#scrollView").data("kendoMobileScrollView");

    // detach events
    scrollView.destroy();

### refresh

Redraw the mobile ScrollView pager. Called automatically on device orientation change event.

#### Example

    <div data-role="scrollview" id="scrollview"></div>

    <script>
       $("#scrollview").data("kendoMobileScrollView").refresh();
    </script>

### scrollTo

Scroll to the given page. Pages are zero-based indexed.

#### Example

    <div data-role="scrollview" id="scrollview"></div>

    <script>
       // Scroll to the second page of the scrollView
       $("#scrollview").data("kendoMobileScrollView").scrollTo(1);
    </script>

#### Parameters

##### page `Number`

The page to scroll to.

##### instant `Boolean` *(default: false)*

If set to true, the scrollview will jump instantly to the given page without any animation effects.

## Events

### changing

Fires before the widget page is changed. The change can be prevented by calling the preventDefault method of the event parameter, in which case the widget will snap back to the current page.

#### Event Data

##### e.currentPage `Number`

The current page (zero based index)

##### e.nextPage `Number`

The page about to be displayed (zero based index)

### change

Fires when the widget page is changed.

#### Event Data

##### e.page `Number`

The current page (zero based index)

##### e.element `jQuery`

The page element. **Available only in data bound mode.** Parameter will be undefined in standard mode.

##### e.data `Array`

The data collection. **Available only in data bound mode.** Parameter will be undefined in standard mode.

### refresh

Fires when widget refreshes

#### Event Data

##### e.pageCount `Number`

The number of pages

##### e.page `Number`

The current page number (zero based index)
