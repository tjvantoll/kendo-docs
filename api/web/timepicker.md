---
title: kendo.ui.TimePicker
meta_title: Configuration, methods and events of Kendo UI TimePicker
meta_description: What type of animations you can use in TimePicker UI widget, find supported methods and see which events are triggered once the value is changed.
slug: api-web-timepicker
relatedDocs: gs-web-timepicker-overview
tags: api,web
publish: true
---

# kendo.ui.TimePicker

Represents the Kendo UI TimePicker. Inherits from [Widget](/api/framework/widget).

## Configuration

### animation `Object`

Configures the opening and closing animations of the popup. Setting the `animation` option to `false` will disable the opening and closing animations. As a result the popup will open and close instantly.

#### Example - disable open and close animations

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
      animation: false
    });
    </script>

#### Example - configure the animation

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
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

The animation played when the popup is closed.

#### Example - configure the close animation

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
      animation: {
       close: {
         effects: "zoom:out",
         duration: 300
       }
      }
    });
    </script>

### animation.close.effects `String`

The effect(s) to use when playing the open animation. Multiple effects should be separated with a space.

[Complete list of available animations](/api/framework/fx#effects)

### animation.close.duration `Number`

The duration of the close animation in milliseconds.

### animation.open `Object`

The animation played when the calendar popup is opened.

#### Example - configure the open animation

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
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

### culture `String`*(default: "en-US")*

 Specifies the culture info used by the widget.

#### Example - specify German culture internationalization

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        culture: "de-DE"
    });
    </script>

### dates `Array`

 Specifies a list of dates, which are shown in the time drop-down list. If not set, the DateTimePicker will auto-generate the available times.


#### Example

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        dates: [
            new Date(2000, 10, 10, 10, 0, 0),
            new Date(2000, 10, 10, 30, 0)
        ] //the drop-down list will consist only two entries - "10:00 AM" and "10:30 AM"
    });
    </script>

### format `String`*(default: "h:mm tt")*

 Specifies the format, which is used to format the value of the TimePicker displayed in the input. The format also will be used to parse the input.

#### Example - specify a custom time format

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        format: "HH:mm"
    });
    </script>

### interval `Number`*(default: "30")*

Specifies the interval, between values in the popup list, in minutes.

#### Example - specify a time interval

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        interval: 15
    });
    </script>

### max `Date`*(default: "00:00")*

Specifies the end value in the popup list.

#### Example - specify a maximum selectable time

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        max: new Date(2000, 0, 1, 22, 0, 0) //date part is ignored
    });
    </script>

### min `Date`*(default: "00:00")*

Specifies the start value in the popup list.

#### Example - specify a minimum selectable time

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        min: new Date(2000, 0, 1, 8, 0, 0) //date part is ignored
    });
    </script>

### parseFormats `Array`

 Specifies the formats, which are used to parse the value set with the value method or by direct input. If not set the value of the options.format will be used. Note that value of the format option is always used.

#### Example

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        format: "h:mm tt",
        parseFormats: ["HH:mm"] //format also will be added to parseFormats
    });
    </script>

### value `Date`*(default: null)*

Specifies the selected time.

#### Example

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        value: new Date(2011, 0, 1, 10, 30)
    });
    </script>

## Methods

### close

Closes the drop-down list of a TimePicker.

#### Example

    <input id="timepicker" />
    <button id="close">Close</button>
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    $("#close").click(function() {
        timepicker.close();
    });
    </script>

### destroy
Prepares the **TimePicker** for safe removal from DOM. Detaches all event handlers and removes jQuery.data attributes to avoid memory leaks. Calls destroy method of any child Kendo widgets.

> **Important:** This method does not remove the TimePicker element from DOM.

#### Example

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    // detach events
    timepicker.destroy();
    </script>

### enable

Enables or disables a TimePicker.

#### Parameters

##### enable `Boolean`

Enables (**true** or undefined) or disables (**false**) a TimePicker.

#### Example - disable TimePicker widget

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.enable(false);
    </script>

#### Example - enable TimePicker widget

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.enable(true);
    </script>

### readonly

Controls whether the widget is editable or readonly.

#### Parameters

##### readonly `Boolean`

The argument, which defines whether the timepicker should be readonly or editable.

#### Example - make TimePicker widget readonly

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.readonly();
    </script>

#### Example - make TimePicker widget editable

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.readonly(false);
    </script>

### max

Gets or sets the maximum value of the TimePicker.

#### Parameters

##### value `Date|String`

The maximum time value to set for a TimePicker, expressed as a Date object or as a string.

#### Returns

`Date` The maximum time value of a TimePicker.

#### Example - get the max value of the timepicker

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var max = timepicker.max();

    console.log(max);
    </script>

#### Example - set the max value of the timepicker

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.max(new Date(2000, 0, 1, 22, 0, 0));
    </script>

### min

Gets or sets the minimum value of the TimePicker.

#### Parameters

##### value `Date|String`

The minimum time value to set for a TimePicker, expressed as a Date object or as a string.

#### Returns

`Date` The minimum time value of a TimePicker.

#### Example - get the min value of the timepicker

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var min = timepicker.min();

    console.log(min);
    </script>

#### Example - set the min value of the timepicker

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.min(new Date(2000, 0, 1, 8, 0, 0));
    </script>

### open

Opens the drop-down list of a TimePicker.

#### Example

    <input id="timepicker" />
    <button id="open">Open</button>
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    $("#open").click(function() {
        timepicker.open();
    });
    </script>

### value

Gets or sets the value of the TimePicker.

#### Get the value of a TimePicker

    var timePicker = $("#timePicker").data("kendoTimePicker");
    var timePickerValue = timePicker.value();

#### Set the value of a TimePicker

    var timePicker = $("#timePicker").data("kendoTimePicker");
    timePicker.value("10:00 AM");

#### Parameters

##### value `Date|String`

The time value to set for a TimePicker, expressed as a Date object or as a string.

#### Returns

`Date` The time value of a TimePicker.

#### Example - gets the value of the widget

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        value: "10:00 AM"
    });

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var value = timepicker.value();
    console.log(value);
    </script>

#### Example - sets the value of the widget

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.value("10:00 AM");
    </script>

## Events

### change

Fires when the selected date is changed

#### Example - subscribe to the "change" event during initialization

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        change: function() {
            var value = this.value();
            console.log(value); //value is the selected date in the timepicker
        }
    });
    </script>

#### Example - subscribe to the "change" event after initialization

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.bind("change", function() {
        var value = this.value();
        console.log(value); //value is the selected date in the timepicker
    });
    </script>

### close

Fires when the time drop-down list is closed

#### Example - subscribe to the "close" event during initialization

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        close: function(e) {
            e.preventDefault(); //prevent popup closing
        }
    });
    </script>

#### Example - subscribe to the "close" event after initialization

    <input id="timepicker" />
    <script>
    $("#timepicker").timepicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.bind("close", function(e) {
        e.preventDefault(); //prevent popup closing
    });
    </script>

### open

Fires when the time drop-down list is opened

#### Example - subscribe to the "open" event during initialization

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker({
        open: function(e) {
            e.preventDefault(); //prevent popup opening
        }
    });
    </script>

#### Example - subscribe to the "open" event after initialization

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    timepicker.bind("open", function(e) {
        e.preventDefault(); //prevent popup opening
    });
    </script>

## Field

### element
A jQuery object of the original input element.

#### Example - modify input element

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var element = timepicker.element;

    element.css("background-color", "red");
    <script>

### options
An object, which holds the options of the widget.

#### Example - get options of the widget

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var options = timepicker.options;
    <script>

### wrapper
A jQuery object of the span element which wraps the input.

#### Example - get wrapper element

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var wrapper = timepicker.wrapper;
    <script>

### timeView
An instance of the TimeView object, responsible for the drop-down list of available hours.

#### Example - get widget's timeView instance

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var timeView = timepicker.timeView;
    <script>

#### popup
The Popup instance used by the widget.

#### Example - get widget popup

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var popup = timepicker.popup;

    console.log(popup.visible());
    <script>

#### ul
A jQuery object of the ul element, which holds the available hours.

#### Example

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var ul = timepicker.ul;
    <script>

#### list
A jQuery object of the drop-down list element.

#### Example

    <input id="timepicker" />
    <script>
    $("#timepicker").kendoTimePicker();

    var timepicker = $("#timepicker").data("kendoTimePicker");

    var list = timepicker.list;
    <script>

#### template
A template used to render available options in the list.
