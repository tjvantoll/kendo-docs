---
title: kendo.ui.DropTargetArea
slug: framework-kendo.ui.droptargetarea
tags: api,framework
publish: true
---

# kendo.ui.DropTargetArea

## Configuration

### group `String`*(default: "default")*

 Used to group sets of draggable and drop targets. A draggable with the same group value as a drop target will be accepted by the drop target.

### filter `String`*(default: "*")*

 Selector to filter the drop targets in the area. Every matched element acts as a drop target and fires events on the DropTargetArea.

## Events

### dragenter

Fires when draggable moves over one of the drop targets.

#### Event Data

##### e.draggable `jQuery`

Reference to the draggable that enters a drop target.

### dragleave

Fires when draggable moves out of one of the drop targets.

#### Event Data

##### e.draggable `jQuery`

Reference to the draggable that leaves a drop target.

### drop

Fires when draggable is dropped over one of the drop targets.

#### Event Data

##### e.draggable `jQuery`

Reference to the draggable that is dropped over the drop target.

##### e.draggable.currentTarget `jQuery`

The element that the drag and drop operation started from.

##### e.dropTarget `jQuery`

The current drop target in the area that initiated the event.
