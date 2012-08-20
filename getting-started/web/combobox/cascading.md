---
title: Cascading ComboBoxes
slug: gs-web-cascading-comboboxes
tags: getting-started,web
publish: true
---

# Cascading ComboBoxes

The cascading comboboxes are a series of 2 or more comboboxes in which each combobox is filtered according to the previous combobox.

##How it works?

Here is a simple example:

    <input id="parent" />
    <input id="child" />

    <script type="text/javascript">
         $(function() {
             $("#parent").kendoComboBox({
                dataTextField: "parentName",
                dataValueField: "parentID"
                //Define the combobox's settings
             });

             $("#child").kendoComboBox({
                cascadeFrom: "parent"
                //Define other settings
             });
         });
    </script>
The "child" combobox will cascade from the "parent" combobox if the [cascadeFrom](http://docs.kendoui.com/api/web/combobox#configuration) option is defined. The value of the `cascadeFrom` option should be the ID of the parent combobox.

> **Important:** If the `cascadeFrom` property is not defined or the parent combobox is not initialized then the cascading functionality will not **work**.

Here is a list of the actions which the child combobox makes during the initialization:

- Checks if the "cascadeFrom" property is set. If not then the cascading is not enabled.
- Tries to find the parent combobox object. If the result is null, then the functionality is omitted.
- The child combobox will listen to any changes of the parent's value.
- If the parent does not have a value, then the child will be disabled.
- If the parent has a value, then the child will be enabled and will filter its data depending on it. Here how the filter options will look like:


    {

        field: "parentID",  //the dataValueField of the parent
        operator: "eq",
        value: "" //parent's value
    }

> Please note that the filter operator will always be "eq". The child combobox will use the `dataValueField` option of the parent combobox in order to filter the data.

####FAQ

Q: I am using cascading comboboxes with a `"autoBind: true"` option and I need to pre-set the selected items. How to do that?

A: You need to set the value of the comboboxes. For instance, you can define it before initialization:

    <input id="parent" value="1" />
    <input id="child" value="36" />

    <script>
       //initialization of the comboboxes
    </script>

The other optios is to use the [value](http://docs.kendoui.com/api/web/combobox#configuration) option.

Q: I am using comboboxes with load on demand (autoBind: false) and I need to pre-set the selected items. How to do that?

A: You need to set the value and the text of the combobox. You can use the [value](http://docs.kendoui.com/api/web/combobox#configuration) and [text](http://docs.kendoui.com/api/web/combobox#configuration) options.

    <input id="parent" value="1" />
    <input id="child" value="36" />

    <script>
       $(function() {
            $("#parent").kendoComboBox({
               value: "1",
               text: "Parent1",
               dataTextField: "ParentName",
               dataValueField: "ParentID",
               dataSource: {
                  //dataSource settings
               },
               autoBind: false
            });

            $("#child").kendoComboBox({
               cascadeFrom: "parent",
               value: "36",
               text: "Child36",
               dataTextField: "ChildName",
               dataValueField: "ChildID",
               dataSource: {
                  //dataSource settings
               },
               autoBind: false
            });
       });
    </script>

Q: The serverFiltering is disabled and the child combobox does not work?

A: When the [serverFiltering](http://docs.kendoui.com/api/framework/datasource#configuration) is disabled, then the combobox will not make any additional requests to the server. Hence it will filter the initial data using the parent's dataValueField property. If no items is found, then the child combobox will be empty. If you need to use child combobox with disabled server filtering, then you will need to provide all neccessary data on the client.
