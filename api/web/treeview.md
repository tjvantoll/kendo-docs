---
title: kendo.ui.TreeView
meta_title: Configuration, methods and events of Kendo UI TreeView
meta_description: Documentation guide that helps the developer configure TreeView UI widget in a few quick steps, apply methdos and trigger events.
slug: api-web-treeview
relatedDocs: gs-web-treeview-overview
tags: api,web
publish: true
---

# kendo.ui.TreeView

Represents the Kendo UI TreeView. Inherits from [Widget](/api/framework/widget).

## Configuration

### animation `Boolean|Object`

A collection of visual animations used when items are expanded or collapsed through user interaction.
Setting this option to **false** will disable all animations.

#### Example - disable animation of subnodes

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      animation: false,
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### animation.collapse `Boolean|Object`

The animation that will be used when collapsing items.

#### Example - disable the collapse animation

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      animation: {
        collapse: false
      },
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### animation.collapse.duration `Number` *(default: 200)*

The number of milliseconds used for the animation when a node is expanded.

#### Example - specify a collapse animation duration

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      animation: {
        collapse: {
          duration: 400
        }
      },
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### animation.collapse.effects `String`

A whitespace-delimited string of animation effects that are used when collapsing nodes.
The supported effects are **fadeOut** and **collapseVertical**.

#### Example - make sub-levels fade out and collapse vertically

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      animation: {
        collapse: {
          effects: "fadeOut collapseVertical"
        }
      },
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### animation.expand `Boolean|Object`

The animation that will be used when expanding items.

#### Example - disable expand animation

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      animation: {
        expand: false
      },
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### animation.expand.duration `Number` *(default: 200)*

 The number of milliseconds used for the animation when a
node is expanded.

#### Example - specify a slow expand animation

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      animation: {
        expand: {
          duration: 600
        }
      },
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### animation.expand.effects `String` *(default: "expandVertical")*

A whitespace-delimited string of animation effects that are used when expanding nodes.
The supported effects are **"expandVertical"** and **"fadeIn"**.

#### Example - make sub-levels fade in and expand vertically

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      animation: {
        expand: {
          effects: "fadeIn expandVertical"
        }
      },
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### autoBind `Boolean` *(default: true)*

If set to `false` the widget will not bind to the data source during initialization. In this case data binding will occur when the [change](/api/framework/datasource#events-change) event of the
data source is fired. By default the widget will bind to the data source specified in the configuration.

> Setting `autoBind` to `false` is useful when multiple widgets are bound to the same data source. Disabling automatic binding ensures that the shared data source does not make more than one request to the remote service.

#### Example - disable automatic binding

    <div id="treeview"></div>
    <script>
    var dataSource = new kendo.data.HierarchicalDataSource({
      data: [ { text: "Jane Doe" }, { text: "John Doe" }]
    });
    $("#treeview").kendoTreeView({
      autoBind: false,
      dataSource: dataSource
    });
    dataSource.read(); // "read()" will fire the "change" event of the dataSource and the widget will be bound
    </script>

### checkboxes `Boolean|Object`

If `true` or an object, renders checkboxes beside each treeview item.

#### Example - show node checkboxes

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      checkboxes: true,
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### checkboxes.name `String`

Sets the name attribute of the checkbox inputs. That name will be posted to the server.

#### Example

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      checkboxes: {
        name: "checkedItems[]"
      },
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### checkboxes.checkChildren `Boolean`*(default: false)*

Indicates whether checkboxes of child items should get checked when the checkbox of a parent item is checked. This
also enables tri-state checkboxes with an indeterminate state.

#### Example - enable tri-state checkboxes and propagate checked state to children

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      checkboxes: {
        checkChildren: true
      },
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### checkboxes.template `String|Function`

The [template](/api/framework/kendo#methods-template) which renders the checkboxes. Can be used to allow posting of
additional information along the treeview checkboxes.

The fields which can be used in the template are:

* item - the data item of the given node
* treeview - the treeview options

#### Example - specify a different name for each checkbox, bound to the item id

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      checkboxes: {
        template: "<input type='checkbox' name='checkedFiles[#= item.id #]' value='true' />"
      },
      dataSource: [
        { id: 1, text: "foo", items: [
          { id: 2, text: "bar" }
        ] }
      ]
    });
    </script>

### dataImageUrlField `String` *(default: null)*

Sets the field of the data item that provides the image URL of the treeview nodes.

#### Example - specify custom image URL field

    <div id="treeview"></div>
    <script>
    var items = [
      { text: "Mail", image: "http://demos.kendoui.com/content/web/treeview/mail.png" },
      { text: "Search", image: "http://demos.kendoui.com/content/web/treeview/search.png" }
    ];
    $("#treeview").kendoTreeView({
      dataImageUrlField: "image",
      dataSource: items
    });
    </script>

### dataSource `Object|Array|kendo.data.HierarchicalDataSource`

The data source of the widget which is used render nodes. Can be a JavaScript object which represents a valid data source configuration, a JavaScript array or an existing [kendo.data.HierarchicalDataSource](/api/framework/hierarchicaldatasource) instance.

If the `dataSource` option is set to a JavaScript object or array the widget will initialize a new [kendo.data.HierarchicalDataSource](/api/framework/hierarchicaldatasource) instance using that value as data source configuration.

If the `dataSource` option is an existing [kendo.data.HierarchicalDataSource](/api/framework/hierarchicaldatasource) instance the widget will use that instance and will **not** initialize a new one.

#### Example - set dataSource as a JavaScript object

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      dataSource: {
        data: [
          { text: "foo", items: [
            { text: "bar" }
          ] }
        ]
      }
    });
    </script>

#### Example - set dataSource as a JavaScript array

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

#### Example - set dataSource as an existing kendo.data.HierarchicalDataSource instance

    <div id="treeview"></div>
    <script>
    var dataSource = new kendo.data.HierarchicalDataSource({
      transport: {
        read: {
          url: "http://demos.kendoui.com/service/Employees",
          dataType: "jsonp"
        }
      },
      schema: {
        model: {
          id: "EmployeeId",
          hasChildren: "HasEmployees"
        }
      }
    });

    $("#treeview").kendoTreeView({
      dataSource: dataSource,
      dataTextField: "FullName"
    });
    </script>

### dataSpriteCssClassField `String` *(default: null)*

Sets the field of the data item that provides the sprite CSS class of the treeview nodes.
If an array, each level uses the field that is at the same index in the array, or the last item in the array.

#### Example

    <style>
      #treeview .k-sprite {
        background-image: url("http://demos.kendoui.com/content/web/treeview/coloricons-sprite.png");
      }

      .folder { background-position: 0 -16px; }
      .html { background-position: 0 -48px; }
    </style>

    <div id="treeview"></div>
    <script>
    var items = [
      { text: "assets", sprite: "folder" },
      { text: "index.html", sprite: "html" }
    ];
    $("#treeview").kendoTreeView({
      dataSpriteCssClassField: "sprite",
      dataSource: items
    });
    </script>

### dataTextField `String|Array` *(default: null)*

Sets the field of the data item that provides the text content of the treeview nodes.
If an array, each level uses the field that is at the same index in the array, or the last item in the array.

#### Example

    <div id="treeview"></div>
    <script>
    var items = [
      { ProductName: "Tea", items: [
        { ProductName: "Green Tea" },
        { ProductName: "Black Tea" }
      ] },
      { ProductName: "Coffee" }
    ];
    $("#treeview").kendoTreeView({
      dataTextField: "ProductName",
      dataSource: items
    });
    </script>

#### Example - using different fields on different levels

    <div id="treeview"></div>
    <script>
    var items = [
      { CategoryName: "Tea", items: [
        { ProductName: "Green Tea" },
        { ProductName: "Black Tea" }
      ] },
      { CategoryName: "Coffee" }
    ];
    $("#treeview").kendoTreeView({
      dataTextField: [ "CategoryName", "ProductName" ],
      dataSource: items
    });
    </script>

### dataUrlField `String` *(default: null)*

Sets the field of the data item that provides the link URL of the treeview nodes.

#### Example

    <div id="treeview"></div>
    <script>
    var items = [
      { text: "Tea", LinksTo: "http://tea.example.com" },
      { text: "Coffee", LinksTo: "http://coffee.example.com" }
    ];
    $("#treeview").kendoTreeView({
      dataUrlField: "LinksTo",
      dataSource: items
    });
    </script>

### dragAndDrop `Boolean` *(default: false)*

Disables (**false**) or enables (**true**) drag-and-drop of the nodes.

#### Example

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      dragAndDrop: true,
      dataSource: [
        { text: "foo" },
        { text: "bar" }
      ]
    });
    </script>

### loadOnDemand `Boolean` *(default: true)*

Indicates whether the child datasources should be fetched lazily when parent groups get expanded.
Setting this to false causes all child dataSources to be loaded at initialization time.
Note: when initializing a TreeView from array (rather than from a HierarchicalDataSource instance), this option defaults to false, rather than true.

#### Example - force lazy loading of sublevels

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      loadOnDemand: true,
      dataSource: [
        { text: "foo", items: [
          { text: "bar" }
        ] }
      ]
    });
    </script>

### template `String|Function`

Template for rendering of the nodes of the treeview.

#### Example

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      template: "#= item.text # (#= item.inStock #)",
      dataSource: [
        { text: "foo", inStock: 7, items: [
          { text: "bar", inStock: 2 },
          { text: "baz", inStock: 5 }
        ] }
      ]
    });
    </script>

## Methods

### append

Appends a node to any level of the treeview. This method may also be used to reorder the nodes of a TreeView.

#### Example

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      dataSource: [
        { text: "foo" }
      ]
    });

    var treeview = $("#treeview").data("kendoTreeView");
    // appends a new node to the root level
    treeview.append({ text: "bar" });

    // appends a new node to the first treeview item
    treeview.append({ text: "baz" }, $("#treeview .k-item:first"));

    // move the item with text "bar" within the item with text "foo"
    treeview.append(treeview.findByText("bar"), treeview.findByText("foo"));

    // append two items to the root level
    treeview.append([
      { text: "qux" },
      { text: "cat" }
    ]);
    </script>

#### Parameters

##### nodeData `Object|jQuery`

A JSON-formatted string or selector that specifies the node to be appended.
If the argument is a plain JavaScript object, a new item will be created.
If the argument is a jQuery element that holds a node, the treeview node will be moved.
If the argument is an array of objects, each item of the array will be appended.

##### parentNode `jQuery` *(optional)*

The node that will contain the newly appended node. If not specified, the new node will be appended to the
root group of the TreeView.

##### success `Function` *(optional)*

A success callback that will be called once the new node has been appended.
Useful in the case of remote binding where an item is appended to an unfetched node. The callback is called
once the siblings have been fetched.

#### Returns

`jQuery` The inserted `<li>` element, wrapped in a jQuery object,
or `null` if the new model has not been inserted immediately.

### collapse

Collapses nodes.

#### Example

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      dataSource: [
        { text: "foo", expanded: true, items: [
          { text: "bar" }
        ] },
        { text: "baz", expanded: true, items: [
          { text: "qux" }
        ] }
      ]
    });

    var treeview = $("#treeview").data("kendoTreeView");
    // collapse the item with text "foo"
    treeview.collapse(treeview.findByText("foo"));

    // collapse all items
    treeview.collapse(".k-item");
    </script>

#### Parameters

##### nodes `jQuery|Element|String`

The nodes that will be collapsed.

### dataItem

Returns the data item to which the specified node is bound.

#### Parameters

##### node `jQuery|Element|String`

A string, DOM element or jQuery object which represents the node. A string is treated as a jQuery selector.

#### Returns

`kendo.data.Node` The model of the item that was passed as a parameter.

#### Example - get the data item of the first node

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      dataSource: [
        { id: 1, text: "foo" },
        { id: 2, text: "bar" }
      ]
    });

    var treeview = $("#treeview").data("kendoTreeView");
    var dataItem = treeview.dataItem(".k-item:first");
    console.log(dataItem.text); // displays "foo"
    </script>

See also: [getting the node data in the select event handler](/getting-started/web/treeview/overview#getting-the-node-data-in-the-select-event-handler)

### destroy

Prepares the widget for safe removal from DOM. Detaches all event handlers and removes jQuery.data attributes to avoid memory leaks. Calls destroy method of any child Kendo widgets.

> This method does not remove the widget element from DOM.

#### Example

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      dataSource: [
        { id: 1, text: "foo" },
        { id: 2, text: "bar" }
      ]
    });

    var treeview = $("#treeview").data("kendoTreeView");
    treeview.destroy();
    </script>

### detach

Removes a node from a TreeView, but keeps its jQuery.data() objects.

#### Parameters

##### node `jQuery|Element|String`

The node that is to be detached.

#### Returns

`jQuery` The node that has been detached.

#### Example - remove the node with ID, firstItem

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      dataSource: [
        { id: 1, text: "foo" },
        { id: 2, text: "bar" }
      ]
    });

    var treeview = $("#treeview").data("kendoTreeView");
    var item = treeview.findByText("foo");
    item.data("id", "abc");
    treeview.detach(item);
    console.log(item.data("id")); // logs "abc"
    </script>

### enable

Enables or disables nodes.

#### Parameters

##### nodes `jQuery|Element|String`

The nodes that are to be enabled/disabled.

##### enable `Boolean` *(optional, default: true)*

Whether the nodes should be enabled or disabled.

#### Example

    <div id="treeview"></div>
    <script>
    $("#treeview").kendoTreeView({
      dataSource: [
        { text: "foo", enabled: false },
        { text: "bar", enabled: false }
      ]
    });

    var treeview = $("#treeview").data("kendoTreeView");
    // enable the item with text "foo"
    treeview.enable(treeview.findByText("foo"));

    // enable all items
    treeview.enable(".k-item");
    </script>

### expand

Expands nodes.

#### Example

    var treeview = $("#treeview").data("kendoTreeView");

    // expands the node with id="firstItem"
    treeview.expand(document.getElementById("firstItem"));

    // expands all nodes
    treeview.expand(".k-item");

#### Parameters

##### nodes `jQuery | Element | String`

The nodes that are to be expanded.

### findByText

Searches a TreeView for a node that has specific text.

#### Search a TreeView for the item that has the text, "CSS3 is da bomb!"

    var treeView = $("#treeView").data("kendoTreeView");
    var foundNode = treeView.findByText("CSS3 is da bomb!");

#### Parameters

##### text `String`

The text that is being searched for.

#### Returns

`jQuery` All nodes that have the text.

### findByUid

Searches a TreeView for a node with the given unique identifier.
Applicable when the widget is bound to a [HierarchicalDataSource](/api/framework/hierarchicaldatasource).

#### Search a TreeView for the item that has the unique id "95c1925d-a779-47fc-8420-b4274f01c037"

    var treeView = $("#treeView").data("kendoTreeView");
    var node = treeView.findByUid("95c1925d-a779-47fc-8420-b4274f01c037");

If you want to find a node by its `id`, use the [dataSource.get()](/api/framework/datasource#get) method and supply its uid to the `findByUid` method.

#### Parameters

##### text `String`

The text that is being searched for.

#### Returns

`jQuery` All nodes that have the text.

### insertAfter

Inserts a node after a specified node in a TreeView. This method may also be used to reorder the nodes of a
TreeView.

#### Insert a node with the text, "JavaScript" after the node with ID, firstItem

    var treeView = $("#treeView").data("kendoTreeView");
    treeView.insertAfter({ text: "JavaScript" }, $("#firstItem"));

#### Moves a node with ID, secondNode after a node with ID, firstItem

    var treeView = $("#treeView").data("kendoTreeView");
    treeView.insertAfter($("#secondNode"), $("#firstItem"));

#### Parameters

##### nodeData `Object`

A JSON-formatted string or selector that specifies the node to be inserted.

##### referenceNode `jQuery`

The node that will be preceed the newly-appended node.

### insertBefore

Inserts a node before another node. This method may also be used to reorder the nodes of a
TreeView.

#### Inserts a new node with the text, "CSS3" before the node with ID, firstItem

    var treeView = $("#treeView").data("kendoTreeView");
    treeView.insertBefore({ text: "CSS3" }, $("#firstItem"));

#### Moves the node with ID, secondNode before the node with ID, firstItem

    var treeView = $("#treeView").data("kendoTreeView");
    treeView.insertBefore($("#secondNode"), $("#firstItem"));

#### Parameters

##### nodeData `Object`

A JSON-formatted string or selector that specifies the node to be inserted.

##### referenceNode `jQuery`

The node that follows the inserted node.

### parent

Gets the parent node of the item

#### Example

    var treeView = $("#treeView").data("kendoTreeView");
    var parentNode = treeView.parent($("#firstItem"));

#### Parameters

##### node `jQuery | Element | String`

The child node whose parent will be returned.

#### Returns

`jQuery` The parent node of the given parameter node.

### remove

Removes a node from a TreeView.

#### Remove the node with ID, firstItem

    var treeView = $("#treeView").data("kendoTreeView");
    treeView.remove($("#firstItem"));

#### Parameters

##### node `jQuery | Element | String`

The node that is to be removed.

### select

Gets or sets the selected node of a TreeView.

#### Select the node with HTML id="firstItem"

    var treeView = $("#treeView").data("kendoTreeView");
    treeView.select($("#firstItem"));

#### Select the first node in the treeview

    var treeView = $("#treeView").data("kendoTreeView");
    treeView.select(".k-item:first");

#### Get the currently selected node

    var treeView = $("#treeView").data("kendoTreeView");
    var selectedNode = treeView.select();

#### Unselect all nodes

    var treeView = $("#treeView").data("kendoTreeView");
    treeView.select($());

#### Parameters

##### node `jQuery | Element | String` *(optional)*

If provided, the node of a TreeView that should be selected.

#### Returns

`jQuery` The selected node of a TreeView.

### setDataSource

Sets the dataSource of an existing TreeView and rebinds it.

#### Parameters

##### dataSource `kendo.data.HierarchicalDataSource`

#### Example

    var dataSource = new kendo.data.HierarchicalDataSource({
        data: [
            { text: "foo" }
        ]
    });

    $("#treeview").data("kendoTreeView").setDataSource(dataSource);

### text

Gets or sets the text of a node in a TreeView.

#### Get the text of the node with ID, firstItem

    var treeView = $("#treeView").data("kendoTreeView");
    var nodeText = treeView.text($("#firstItem"));

#### Parameters

##### node `String`

The node of which the text is being retrieved.

##### newText `String`

Optional. When passed, sets the node text to the specified string

    var treeView = $("#treeView").data("kendoTreeView");

    treeView.text(".k-item:first", "Salmon");

#### Returns

`String` The text of a node.

### toggle

Toggles the node of a TreeView between its expanded and collapsed states.

#### Toggle the state of a node with ID, firstItem

    var treeView = $("#treeView").data("kendoTreeView");
    treeView.toggle($("#firstItem"));

#### Parameters

##### node `String`

The node that should be toggled.

### updateIndeterminate

Updates the indeterminate state of the treeview checkboxes. Should be used for better performance when checking multiple checkboxes through code.

    // check many checkboxes through JS
    $(":checkbox").filter(function() {}).prop("checked", true);

    // update indeterminate state of all nodes
    treeview.updateIndeterminate();

#### Parameters

##### node `jQuery`

Optional. The root of the hierarchy that will be looped through. Allows only a subtree to be processed. The default value is the treeview root.

## Events

### collapse

Triggered before a subgroup gets collapsed.

#### Event Data

##### e.node `Element`

The collapsed node

### dataBound

Triggered after the dataSource change event has been processed (adding/removing items);

#### Event Data

##### e.node `jQuery`

The node whose children have been changed. If the changes have occured on the root level, this parameter is undefined.

### drag

Triggered while a node is being dragged.

#### Show the user that is not permitted to drop nodes outside of the #drop-area element

    treeview.data("kendoTreeView").bind("drag", function(e) {
        if ($(e.dropTarget).parents("#drop-area").length ) {
            e.setStatusClass("k-denied");
        }
    });

#### Event Data

##### e.sourceNode `Element`

The node that is being dragged.

##### e.dropTarget `Element`

The element that the node is placed over.

##### e.pageX `Number`

The x coordinate of the mouse.

##### e.pageY `Number`

The y coordinate of the mouse.

##### e.statusClass `String`

The status that the drag clue shows.

##### e.setStatusClass `Function`

Allows a custom drag clue status to be set.


Pre-defined status classes are:

*   **k-insert-top**
        - Indicates that the item will be inserted on top.
*   **k-insert-middle**
        - Indicates that the item will be inserted in the middle.
*   **k-insert-bottom**
        - Indicates that the item will be inserted at the bottom.
*   **k-add**
        - Indicates that the item will be added/appended.
*   **k-denied**
        - Indicates an invalid operation. Using this class will automatically
          make the drop operation invalid, so there will be no need to call
          `setValid(false)` in the `drop` event.

### dragend

Triggered after a node has been dropped.

#### Event Data

##### e.sourceNode `Element`

The node that is being dropped.

##### e.destinationNode `Element`

The node that the sourceNode is being dropped upon.

##### e.dropPosition `String`

Shows where the source has been dropped. One of the values **over**, **before**, or **after**.

### dragstart

Triggered before the dragging of a node starts.

#### Disable dragging of root nodes

    treeview.data("kendoTreeView").bind("dragstart", function(e) {
        if ($(e.sourceNode).parentsUntil(".k-treeview", ".k-item").length == 0) {
            e.preventDefault();
        }
    });

#### Event Data

##### e.sourceNode `Element`

The node that will be dragged.

### drop

Triggered when a node is being dropped.

#### Event Data

##### e.sourceNode `Element`

The node that is being dropped.

##### e.destinationNode `Element`

The node that the sourceNode is being dropped upon.

##### e.valid `Boolean`

Whether this drop operation is permitted.

##### e.setValid `Function`

Allows the drop to be prevented.

##### e.dropTarget `Element`

The element that the node is placed over.

##### e.dropPosition `String`

Shows where the source will be dropped. One of the values **over**, **before**, or **after**.

#### The difference between e.setValid(false) and e.preventDefault()

Both operations cancel the default drag operation, but the indication to the user is different.
`e.setValid(false)` indicates that the operation was unsuccessful by animating the drag clue to its original position.
`e.preventDefault()` simply removes the clue, as if it has been dropped.
As a general rule, use `preventDefault` to manually handle the drag&drop operation, and `setValid(false)` to indicate unsuccessful drag&drops.

### expand

Triggered before a subgroup gets expanded.

#### Event Data

##### e.node `Element`

The expanded node

### change

Triggered when the selection has changed (either by the user or through the `select` method).

### select

Triggered when a node is being selected by the user. Cancellable.

#### Event Data

##### e.node `Element`

The selected node

### navigate

Triggered when the user moves the focus on another node

#### Event Data

##### e.node `Element`

The focused node
