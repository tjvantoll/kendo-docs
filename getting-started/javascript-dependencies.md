---
title: Javascript Dependencies
meta_title: Javascript Dependencies
meta_description: A list of scripts that Kendo UI widgets require to work, detailed explanation about all JavaScript files
slug: gs-javascript-dependencies
publish: true
---

# JavaScript files used by Kendo UI

Every widget from **Kendo UI** needs its JavaScript files to be included in order to work properly. This help topic lists the JavaScript files required by each widget.

## Combined Scripts

The following combined scripts are made available in order to simplify development and deployment.

*   **kendo.all.min.js** contains a minified version of all scripts (Web, DataViz and Mobile).

> **Important**: kendo.all.min.js is only available in the Kendo UI Complete package. The contents of
**kendo.aspnetmvc.min.js** are **not** included in kendo.all.min.js - you need to include kendo.aspnetmvc.min.js in addition to kendo.all.min.js or use the
[custom download builder tool](http://www.kendoui.com/custom-download).

*   **kendo.web.min.js** contains a minified version of all scripts from Kendo UI Web.
*   **kendo.dataviz.min.js** contains a minified version of all scripts from Kendo UI DataViz.
*   **kendo.mobile.min.js** contains a minified version of all scripts from Kendo UI Mobile.

**Important:** Only one of the above scripts can be included at a time.

## Custom Combined Scripts

Users who own a commercial license can use the [custom download builder tool](http://www.kendoui.com/custom-download)
to create a single JavaScript file which contains only the required widgets and features.

## CDN

The minified versions of all JavaScript files (except jQuery) are also available via CDN

    http://cdn.kendostatic.com/<version>/js/<filename>.min.js

**e.g.** `http://cdn.kendostatic.com/2012.2.710/js/kendo.all.min.js`

> **Important:** in order to use HTTPS, you need to directly access the CloudFront CDN

    https://da7xgjtj801h2.cloudfront.net/<version>/js/<filename>.min.js

## jQuery version

Kendo UI requires **jQuery 1.7.1** or later. There are occasions in which a new jQuery version is released, which introduces breaking changes and is not compatible with existing Kendo UI versions.
In such cases we recommend using the previous jQuery version until the next official Kendo UI release that resolves the problems. We normally do not change the jQuery version that is shipped with Kendo UI
for service packs. We can do this for major releases.

## Individual scripts

If more granular control is required, the following script files, either minified or not,
can be included on a per-widget basis.

### AutoComplete

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.odata.js (if binding to OData)
1.  kendo.model.js (if binding to XML)
1.  kendo.data.xml.js (if binding to XML)
1.  kendo.data.js
1.  kendo.fx.js (optional for animation)
1.  kendo.popup.js
1.  kendo.list.js
1.  kendo.autocomplete.js


### Calendar

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.fx.js (optional for animation)
1.  kendo.calendar.js

### Chart

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.odata.js (if binding to OData)
1.  kendo.data.xml.js (if binding to XML)
1.  kendo.data.js
1.  <span>kendo.binder.js (if using MVVM)</span>
1.  kendo.dataviz.core.js
1.  kendo.dataviz.vml.js
1.  kendo.dataviz.svg.js
1. kendo.dataviz.themes.js
1. kendo.dataviz.chart.js


### ComboBox

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.odata.js (if binding to OData)
1.  kendo.model.js (if binding to XML)
1.  kendo.data.xml.js (if binding to XML)
1.  kendo.data.js
1.  kendo.fx.js (optional for animation)
1.  kendo.popup.js
1.  kendo.list.js
1.  kendo.combobox.js


### DataSource

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.odata.js (if binding to OData)
1.  kendo.model.js (if binding to XML or editing)
1.  kendo.data.xml.js (if binding to XML)
1.  kendo.data.js


### DatePicker

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.fx.js (optional for animation)
1.  kendo.popup.js
1.  kendo.calendar.js
1.  kendo.datepicker.js


### Drag and Drop

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.draganddrop.js


### DropDownList

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.odata.js (if binding to OData)
1.  kendo.model.js (if binding to XML)
1.  kendo.data.xml.js (if binding to XML)
1.  kendo.data.js
1.  kendo.fx.js (optional for animation)
1.  kendo.popup.js
1.  kendo.list.js
1.  kendo.dropdownlist.js


### Editor

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.popup.js
1.  kendo.list.js
1.  kendo.dropdownlist.js
1.  kendo.combobox.js
1.  kendo.fx.js (optional for animation)
1.  kendo.draganddrop.js (if popups are draggable and/or resizable)
1.  kendo.window.js
1.  kendo.editor.js


### Gauge

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.js (if using MVVM)
1.  kendo.binder.js (if using MVVM)
1.  kendo.dataviz.core.js
1.  kendo.dataviz.vml.js
1.  kendo.dataviz.svg.js
1.  kendo.dataviz.gauge.js


### Grid

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.odata.js (if binding to OData)
1.  kendo.data.xml.js (if binding to XML)
1.  kendo.data.js
1.  kendo.fx.js (optional for animation)
1.  kendo.popup.js (if editing or filtering is enabled)
1.  kendo.list.js&nbsp;(if editing or filtering is enabled)
1.  kendo.calendar.js (if editing or filtering is enabled)
1.  kendo.datepicker.js (if editing or filtering is enabled)
1.  kendo.numerictextbox.js (if editing or filtering is enabled)
1.  kendo.validator.js (if editing is enabled)
1.  kendo.binder.js (if editing is enabled)
1.  kendo.dropdownlist.js (if filtering is enabled)
1.  kendo.filtermenu.js (if filtering is enabled)
1.  kendo.pager.js (if paging is enabled)
1.  kendo.sortable.js (if sorting is enabled)
1.  kendo.draganddrop.js (if grouping, resizing or reordering is enabled)
1.  kendo.groupable.js (if grouping is enabled)
1.  kendo.editable.js (if editing is enabled)
1.  kendo.selectable.js (if selection is enabled)
1.  kendo.resizable.js (if resizing is enabled)
1.  kendo.reorderable.js (if reordering is enabled)
1.  kendo.grid.js


### ListView

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.odata.js (if binding to OData)
1.  kendo.data.xml.js (if binding to XML)
1.  kendo.data.js
1.  kendo.validator.js (if editing is enabled)
1.  kendo.binder.js (if editing is enabled)
1.  kendo.pager.js (if pager is used)
1.  kendo.editable.js (if editing is enabled)
1.  kendo.selectable.js (if selection is enabled)
1.  kendo.listview.js


### Menu

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.fx.js (optional for animation)
1.  kendo.popup.js
1.  kendo.menu.js


### NumericTextBox

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.numerictextbox.js


### PanelBar

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.fx.js (optional for animation)
1.  kendo.panelbar.js


### Slider and RangeSlider

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.binder.js (if using MVVM)
1.  kendo.draganddrop.js
1.  kendo.slider.js


### Splitter

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.draganddrop.js
1.  kendo.resizable.js
1.  kendo.splitter.js


### TabStrip

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.js
1.  kendo.fx.js (optional for animation)
1.  kendo.tabstrip.js


### TimePicker

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.fx.js (optional for animation)
1.  kendo.popup.js
1.  kendo.timepicker.js


### TreeView

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.js
1.  kendo.fx.js (optional for animation)
1.  kendo.draganddrop.js (if drag &amp; drop enabled)
1.  kendo.treeview.js


### Upload

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.upload.js


### Validator

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.validator.js


### Window

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.fx.js (optional for animation)
1.  kendo.draganddrop.js
1.  kendo.resizable.js
1.  kendo.window.js


### Mobile Application

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js

### Mobile ActionSheet

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.popup.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.shim.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.actionsheet.js


### Mobile Button

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.button.js


### Mobile ButtonGroup

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.buttongroup.js


### Mobile ListView

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.data.js
1.  kendo.data.odata.js
1.  kendo.data.xml.js
1.  kendo.model.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.listview.js

### Mobile ModalView

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.popup.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.shim.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.modalview.js

### Mobile NavBar

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.navbar.js

### Mobile PopOver

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.popup.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.shim.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.popover.js

### Mobile Scroller

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js


### Mobile ScrollView

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.scrollview.js

### Mobile SplitView

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.splitview.js


### Mobile Switch

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.switch.js


### Mobile TabStrip

1.  jquery-1.7.1.js
1.  kendo.core.js
1.  kendo.history.js
1.  kendo.fx.js
1.  kendo.draganddrop.js
1.  kendo.mobile.scroller.js
1.  kendo.mobile.view.js
1.  kendo.mobile.pane.js
1.  kendo.mobile.application.js
1.  kendo.mobile.tabstrip.js

