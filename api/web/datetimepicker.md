---
title: kendo.ui.DateTimePicker
meta_title: Configuration, methods and events of Kendo UI DateTimePicker
meta_description: Learn how to configure the UI DateTimePicker widget. Use methods to open, close, remove, enable, disable, set maximum or minimum values and more.
slug: api-web-datetimepicker
relatedDocs: gs-web-datetimepicker-overview
tags: api,web
publish: true
---

# kendo.ui.DateTimePicker

Represents the Kendo UI DateTimePicker widget. Inherits from [Widget](/api/framework/widget).

## Configuration

### animation `Object`

Configures the opening and closing animations of the popups. Setting the `animation` option to `false` will disable the opening and closing animations. As a result the popup will open and close instantly.

#### Example - disable open and close animations

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
      animation: false
    });
    </script>

#### Example - configure the animation

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
      animation: {
       close: {
         effects: "fadeOut zoom:out",
         duration: 300
       },
       open: {
         effects: "fadeIn zoom:in",
         duration: 300
       }
      }
    });
    </script>

### animation.close `Object`

The animation played when a popup is closed.

#### Example - configure the close animation

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
      animation: {
       close: {
         effects: "zoom:out",
         duration: 300
       }
      }
    });
    </script>

### animation.close.effects `String`

The effect(s) to use when playing the close animation. Multiple effects should be separated with a space.

[Complete list of available animations](/api/framework/fx#effects)

### animation.close.duration `Number`

The duration of the close animation in milliseconds.

### animation.open `Object`

The animation played when the popup is opened.

#### Example - configure the open animation

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
      animation: {
       open: {
         effects: "zoom:in",
         duration: 300
       }
      }
    });
    </script>

### animation.open.effects `String`

The effect(s) to use when playing the open animation. Multiple effects should be separated with a space.

[Complete list of available animations](/api/framework/fx#effects)

### animation.open.duration `Number`

The duration of the open animation in milliseconds.

### ARIATemplate `String`*(default: "Current focused date is #=kendo.toString(data.current, 'G')#")*

 Specifies a template used to populate value of the aria-label attribute.

#### Example

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        ARIATemplate: "Date: #=kendo.toString(data.current, 'G')#"
    });
    </script>

### culture `String`*(default: "en-US")*

 Specifies the culture info used by the widget.

#### Example - specify German culture internationalization

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        culture: "de-DE"
    });
    </script>

### dates `Array`

 Specifies a list of dates, which will be passed to the month template of the DateView. All dates, which match the date portion of the selected date will be used to re-bind the TimeView.

#### Example - specify a list of dates

    <input id="datetimepicker" />
    <script>
        $("#datetimepicker").kendoDateTimePicker({
            value: new Date(2000, 10, 1),
            dates: [
                new Date(2000, 10, 10, 10, 0, 0),
                new Date(2000, 10, 12, 10, 30, 0)
            ] //can manipulate month template depending on this array.
        });
    </script>

### depth `String`

Specifies the navigation depth of the calendar. The following
settings are available for the **depth** value:


#### *"month"*

shows the days of the month

#### *"year"*

shows the months of the year

#### *"decade"*

shows the years of the decade

#### *"century"*

shows the decades from the century

#### Example - set navigation depth of the calendar popup

    <div id="datetimepicker"></div>
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        depth: "year"
    });
    </script>

### footer `String`

 The [template](/api/framework/kendo#methods-template) which renders the footer of the calendar. If false, the footer will not be rendered.

#### Example - specify footer template as a function

    <input id="datetimepicker" />
    <script id="footer-template" type="text/x-kendo-template">
        Today - #: kendo.toString(data, "d") #
    </script>
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        footer: kendo.template($("#footer-template").html())
    });
    </script>

#### Example - specify footer template as a string

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        footer: "Today - #: kendo.toString(data, 'd') #"
    });
    </script>

### format `String`*(default: "MM/dd/yyyy h:mm tt")*

 Specifies the format, which is used to format the value of the DateTimePicker displayed in the input. The format also will be used to parse the input.

#### Example - specify a custom date format

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        format: "yyyy/MM/dd hh:mm tt"
    });
    </script>

### interval `Number`*(default: 30)*

 Specifies the interval, between values in the popup list, in minutes.

#### Example - specify a time interval

    <input id="datetimepicker" />
    <script>
    $("#dateTimePicker").kendoDateTimePicker({
        interval: 15
    });
    </script>

### max `Date`*(default: Date(2099, 11, 31))*

 Specifies the maximum date, which the calendar can show.

#### Example - specify the maximum date

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        max: new Date(2013, 0, 1, 22, 0, 0)
    });
    </script>

### min `Date`*(default: Date(1900, 0, 1))*

 Specifies the minimum date that the calendar can show.

#### Example - specify the minimum date

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        min: new Date(2011, 0, 1, 8, 0, 0)
    });
    </script>

### month `Object`

 Templates for the cells rendered in the calendar "month" view.

### month.content `String`

 Template to be used for rendering the cells in the calendar "month" view, which are in range.

#### Example - specify cell template as a string

    <input id="datetimepicker" />
    <script id="cell-template" type="text/x-kendo-template">
        <div class="#= data.value < 10 ? 'exhibition' : 'party' #"></div>
        #= data.value #
    </script>
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        month: {
           content: $("#cell-template").html()
        }
    });
    </script>

### month.empty `String`

The template used for rendering the cells in the calendar "month" view, which are not in the range between
the minimum and maximum values.

#### Example - specify an empty cell template as a string

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        month: {
           empty: '-'
        }
    });
    </script>

### parseFormats `Array`

 Specifies the formats, which are used to parse the value set with value() method or by direct input. If not set the value of the options.format and options.timeFormat will be used. Note that value of the format option is always used.

#### Example

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        format: "yyyy/MM/dd hh:mm tt",
        parseFormats: ["MMMM yyyy", "HH:mm"] //format also will be added to parseFormats
    });
    </script>

### start `String`*(default: "month")*

 Specifies the start view of the calendar.
 The following settings are available for the **start** value:

#### *"month"*

shows the days of the month

#### *"year"*

shows the months of the year

#### *"decade"*

shows the years of the decade

#### *"century"*

shows the decades from the century


#### Example - specify the initial view, which calendar renders

    <input id="datetimepicker" />
    <script>
        $("#datetimepicker").kendoDateTimePicker({
            start: "year"
        });
    </script>

### timeFormat `String`*(default: "h:mm tt")*

 Specifies the format, which is used to format the values in the time drop-down list.

#### Example

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        timeFormat: "HH:mm" //24 hours format
    });
    </script>

### value `Date`*(default: null)*

 Specifies the selected value.

#### Example

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        value: new Date(2011, 0, 1)
    });
    </script>

## Methods

### close

Closes the calendar or the time drop-down list.

#### Parameters

##### view `String`

The view of the DateTimePicker, expressed as a string.
Available views are "time" and "date".

#### Example - close the calendar popup

    <input id="datetimepicker" />
    <button id="close">Close</button>
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    $("#close").click(function() {
        datetimepicker.close("date");
    });
    </script>

#### Example - close the time popup

    <input id="datetimepicker" />
    <button id="close">Close</button>
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    $("#close").click(function() {
        datetimepicker.close("time");
    });
    </script>

### destroy
Prepares the **DateTimePicker** for safe removal from DOM. Detaches all event handlers and removes jQuery.data attributes to avoid memory leaks. Calls destroy method of any child Kendo widgets.

> **Important:** This method does not remove the DateTimePicker element from DOM.

#### Example

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    // detach events
    datetimepicker.destroy();
    </script>

### enable

Enables or disables a DateTimePicker.

#### Enable a DateTimePicker

    $("dateTimePicker").data("kendoDateTimePicker").enable();

#### Enable a dateTimePicker

    $("dateTimePicker").data("kendoDateTimePicker").enable(true);

#### Disable a dateTimePicker

    $("dateTimePicker").data("kendoDateTimePicker").enable(false);

#### Parameters

##### enable `Boolean`

Enables (**true** or undefined) or disables (**false**) a DateTimePicker.

#### Example - disable DateTimePicker widget

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.enable(false);
    </script>

#### Example - enable DateTimePicker widget

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.enable();
    </script>

### readonly

Controls whether the widget is editable or readonly.

#### Parameters

##### readonly `Boolean`

The argument, which defines whether the datetimepicker should be readonly or editable.

#### Example - make DateTimePicker widget readonly

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.readonly();
    </script>

#### Example - make DateTimePicker widget editable

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.readonly(false);
    </script>

### max

Gets or sets the maximum value of the DateTimePicker.

#### Parameters

##### value `Date|String`

The maximum time value to set for a DateTimePicker, expressed as a Date object or as a string.

#### Returns

`Date` The maximum time value of a DateTimePicker.

#### Example - get the max value of the datetimepicker

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var max = datetimepicker.max();

    console.log(max);
    </script>

#### Example - set the max value of the datetimepicker

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.max(new Date(2100, 0, 1));
    </script>

### min

Gets or sets the minimum value of the DateTimePicker.

#### Parameters

##### value `Date|String`

The minimum time value to set for a DateTimePicker, expressed as a Date object or as a string.

#### Returns

`Date` The minimum time value of a DateTimePicker.

#### Example - get the min value of the datetimepicker

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var min = datetimepicker.min();

    console.log(min);
    </script>

#### Example - set the min value of the datetimepicker

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.min(new Date(2000, 0, 1));
    </script>

### open

Opens the calendar or the time drop-down list.

#### Parameters

##### view `String`

The view of the DateTimePicker, expressed as a string.
Available views are "time" and "date".

#### Example - open the calendar popup

    <input id="datetimepicker" />
    <button id="open">Open</button>
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    $("#open").click(function() {
        datetimepicker.open("date");
    });
    </script>

#### Example - open the time popup

    <input id="datetimepicker" />
    <button id="open">Open</button>
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    $("#open").click(function() {
        datetimepicker.open("time");
    });
    </script>

### toggle

Toggles the calendar or the time drop-down list.

#### Parameters

##### view `String`

The view of the DateTimePicker, expressed as a string.
Available views are "time" and "date".

#### Example - toggle the calendar popup

    <input id="datetimepicker" />
    <button id="toggle">Toggle</button>
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    $("#toggle").click(function() {
        datetimepicker.toggle("date");
    });
    </script>

#### Example - toggle the time popup

    <input id="datetimepicker" />
    <button id="toggle">Toggle</button>
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    $("#toggle").click(function() {
        datetimepicker.toggle("time");
    });
    </script>

### value

Gets or sets the value of the DateTimePicker.

#### Get the value of a DateTimePicker

    var dateTimePicker = $("#dateTimePicker").data("kendoDateTimePicker");
    var timePickerValue = dateTimePicker.value();

#### Set the value of a DateTimePicker

    var dateTimePicker = $("#dateTimePicker").data("kendoDateTimePicker");
    dateTimePicker.value("2/23/2000 10:00 AM");

#### Parameters

##### value `Date|String`

The time value to set for a DateTimePicker, expressed as a Date object or as a string.

#### Returns

`Date` The time value of a DateTimePicker.

#### Example - gets the value of the widget

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        value: new Date(2013, 10, 10)
    });

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var value = datetimepicker.value();
    console.log(value);
    </script>

#### Example - sets the value of the widget

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        value: new Date(2013, 10, 10)
    });

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.value(new Date());
    </script>

## Events

### change

Triggered when the underlying value of a DateTimePicker is changed.

#### Example - subscribe to the "change" event during initialization

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        change: function() {
            var value = this.value();
            console.log(value); //value is the selected date in the datetimepicker
        }
    });
    </script>

#### Example - subscribe to the "change" event after initialization

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.bind("change", function() {
        var value = this.value();
        console.log(value); //value is the selected date in the datetimepicker
    });
    </script>

### close

Fires when the calendar or the time drop-down list is closed

#### Event Data

##### e.view `String`

The view which is closed. Possible values are "date" and "time".

#### Example - subscribe to the "close" event during initialization

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        close: function(e) {
            if (e.view === "date") {
                e.preventDefault(); //prevent popup closing
            }
        }
    });
    </script>

#### Example - subscribe to the "close" event after initialization

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.bind("close", function(e) {
        if (e.view === "date") {
            e.preventDefault(); //prevent popup closing
        }
    });
    </script>

### open

Fires when the calendar or the time drop-down list is opened

#### Event Data

##### e.view `String`

The view which is opened. Possible values are "date" and "time".

#### Example - subscribe to the "open" event during initialization

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker({
        open: function(e) {
            if (e.view === "time") {
                e.preventDefault(); //prevent popup opening
            }
        }
    });
    </script>

#### Example - subscribe to the "open" event after initialization

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    datetimepicker.bind("open", function(e) {
        if (e.view === "time") {
            e.preventDefault(); //prevent popup opening
        }
    });
    </script>

## Field

### element
A jQuery object of the original input element.

#### Example - modify input element

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var element = datetimepicker.element;

    element.css("background-color", "red");
    <script>

### options
An object, which holds the options of the widget.

#### Example - get options of the widget

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("datetimepicker");

    var options = datetimepicker.options;
    <script>

### wrapper
A jQuery object of the span element which wraps the input.

#### Example - get wrapper element

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var wrapper = datetimepicker.wrapper;
    <script>

### dateView
An instance of the DateView object, responsible for the popup calendar.

#### Example - get widget's dateView instance

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var dateView = datetimepicker.dateView;
    <script>

#### calendar
The Calendar instance.

#### Example - modify calendar popup

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var dateView = datetimepicker.dateView;

    dateView.calendar.navigate(datetimepicker.value(), "year"); //navigate popup calendar manually
    <script>

#### popup
The Popup instance.

#### Example - get dateView popup

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var popup = datetimepicker.popup;

    console.log(popup.visible());
    <script>

#### div
jQuery object of the popup element.

#### Example - get popup div element

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var div = datetimepicker.div;
    <script>

### timeView
An instance of the TimeView object, responsible for the drop-down list of available hours.

#### Example - get widget's timeView instance

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var timeView = datetimepicker.timeView;
    <script>

#### popup
The Popup instance used by the widget.

#### Example - get timeView popup

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var popup = datetimepicker.popup;

    console.log(popup.visible());
    <script>

#### ul
A jQuery object of the ul element, which holds the available hours.

#### Example

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var ul = datetimepicker.ul;
    <script>

#### list
A jQuery object of the drop-down list element.

#### Example

    <input id="datetimepicker" />
    <script>
    $("#datetimepicker").kendoDateTimePicker();

    var datetimepicker = $("#datetimepicker").data("kendoDateTimePicker");

    var list = datetimepicker.list;
    <script>

#### template
A template used to render available options in the list.
