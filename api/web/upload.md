---
title: kendo.ui.Upload
meta_title: Configuration, methods and events of Kendo UI Upload
meta_description: How to configure the ability to upload files in an asynchronous manner in Upload UI widget.
slug: api-web-upload
relatedDocs: gs-web-upload-overview
tags: api,web
publish: true
---

# kendo.ui.Upload

Represents the Kendo UI Upload. Inherits from [Widget](/api/framework/widget).

## Configuration

### async `Object`

Configures the ability to upload a file(s) in an asynchronous manner. Please refer to the
[async mode help topic](/getting-started/web/upload/modes#asynchronous-mode)
for more details.

### async.autoUpload `Boolean`*(default: true)*

The selected files will be uploaded immediately by default. You can change this behavior by setting
autoUpload to false.

### async.batch `Boolean`*(default: false)*

The selected files will be uploaded in separate requests, if this is supported by the browser.
You can change this behavior by setting batch to true.

### async.removeField `String`*(default: "fileNames")*

The name of the form field submitted to the Remove URL.

### async.removeUrl `String`

The URL of the handler responsible for removing uploaded files (if any). The handler must accept POST
requests containing one or more "fileNames" fields specifying the files to be deleted.

### async.removeVerb `String`*(default: "POST")*

The HTTP verb to be used by the remove action.

### async.saveField `String`

The name of the form field submitted to the save URL. The default value is the input name.

### async.saveUrl `String`

The URL of the handler that will receive the submitted files. The handler must accept POST requests
containing one or more fields with the same name as the original input name.

### enabled `Boolean`*(default: true)*

Enables (**true**) or disables (**false**) an **Upload**. A disabled
**Upload** may be re-enabled via enable().

### files `Array`

List of files to be initially rendered in the Upload widget files list.

#### Each file object in the array should contain the following properties

*   name
*   size
*   extension

> **Important:** This option could be used only when the Upload widget is in [async mode](/getting-started/web/upload/modes#asynchronous-mode). The files will be rendered as successfully uploaded.

#### Example - passing an array of initial files

	<input type="file" name="files" id="upload" />
	<script>
        var files = [
		    { name: "file1.doc", size: 525, extension: ".doc" },
		    { name: "file2.jpg", size: 600, extension: ".jpg" },
		    { name: "file3.xls", size: 720, extension: ".xls" },
	    ];

    	$("#upload").kendoUpload({
    	    async: {
		        saveUrl: "Home/Save",
		        removeUrl: "Home/Remove",
		        autoUpload: true
		    },
		    files: files
    	});
	</script>


### localization `Object`

Sets the strings rendered by the Upload.

### localization.cancel `String`

Sets the text of the cancel button text.

### localization.dropFilesHere `String`*(default: "drop files here to upload")*

Sets the drop zone hint.

### localization.headerStatusUploaded `String`

Sets the header status message for uploaded files.

### localization.headerStatusUploading `String`

Sets the header status message for files that are being uploaded.

### localization.remove `String`

Sets the text of the remove button text.

### localization.retry `String`

Sets the text of the retry button text.

### localization.select `String`

Sets the "Select..." button text.

### localization.statusFailed `String`

Sets the status message for failed uploads.

### localization.statusUploaded `String`

Sets the status message for uploaded files.

### localization.statusUploading `String`

Sets the status message for files that are being uploaded.

### localization.uploadSelectedFiles `String`

Sets the text of the "Upload files" button.

### multiple `Boolean`*(default: true)*

Enables (**true**) or disables (**false**) the ability to select multiple files.
If **false**, users will be able to select only one file at a time. Note: This option does not
limit the total number of uploaded files in an asynchronous configuration.

### showFileList `Boolean`*(default: true)*

Enables (**true**) or disables (**false**) the ability to display a file listing
for uploading a file(s). Disabling a file listing may be useful you wish to customize the UI; use the
client-side events to build your own UI.

### template `String|Function`
The [template](http://docs.kendoui.com/api/framework/kendo#methods-template) used to render the files in the list

#### Template data `Array`

*   name - the name of the file (string of all file names separated with comma, if batch upload is used)
*   size - the file size in bytes / the total file size if batch upload is used (null if not available)
*   files - array with information about all selected files - name, size and extension

> **Important:** You should add the following markup to the template in order to render an action button for each file: `<button type='button' class='k-upload-action'></button>`.
>To use the default progress-bar, you should add the following markup at the beginning of the template `<span class='k-progress'></span>` and render the rest of the template relative to it. Please check [Upload Templates](http://demos.kendoui.com/web/upload/templates.html) for a live demo.

#### Example - specify template as a function

	<input type="file" name="files" id="upload" />
	<script id="fileTemplate" type="text/x-kendo-template">
    	<div>
    	    <p>Name: #=name#</p>
    	    <p>Size: #=size# bytes</p>
        	<p>Extension: #=files[0].extension#</p>
        	<button type='button' class='k-upload-action' style='position: absolute; top: 0; right: 0;'></button>
    	</div>
	</script>
	<script>
    	$("#upload").kendoUpload({
    	    template: kendo.template($('#fileTemplate').html())
    	});
	</script>

#### Example - specify template as a string

	<input type="file" name="files" id="upload" />
	<script>
		$("#upload").kendoUpload({
        template: "<div><p>Name: #=name#</p>" +
                  "<p>Size: #=size# bytes</p><p>Extension: #=files[0].extension#</p>" +
                  "<button type='button' class='k-upload-action' style='position: absolute; top: 0; right: 0;'></button>" +
                  "</div>"
    	});	
	</script>

## Methods

### destroy
Prepares the **Upload** for safe removal from DOM. Detaches all event handlers and removes jQuery.data attributes to avoid memory leaks. Calls destroy method of any child Kendo widgets.

> **Important:** This method does not remove the Upload element from DOM.

#### Example

    var upload = $("#upload").data("kendoUpload");

    // detach events
    upload.destroy();

### disable

Disables the upload.

#### Example

    var upload = $("#upload").data("kendoUpload");

    // disables the upload
    upload.disable();

### enable

Enables the upload.

#### Example

    var upload = $("#upload").data("kendoUpload");

    // enables the upload
    upload.enable();

#### Parameters

##### enable `Boolean` *(optional)*

The argument, which defines whether to enable/disable the upload.

### toggle

Toggles the upload enabled state.

#### Example

    var upload = $("#upload").data("kendoUpload");

    // toggles the upload enabled state
    upload.toggle();

#### Parameters

##### enable `Boolean`

(Optional) The new enabled state.

## Events

### cancel

Fires when the upload has been cancelled while in progress.



Note: The cancel event fires only when the upload is in
[async mode](/getting-started/web/upload/modes#asynchronous-mode).

#### Example

    $("#photos").kendoUpload({
        // ...
        cancel: onCancel
    });

    function onCancel(e) {
        // Array with information about the uploaded files
        var files = e.files;

        // Process the Cancel event
    }

#### Event Data

##### e.files `Array`

List of the files that were uploaded or removed . Each file has:


*   name
*   extension - the file extension
        including the leading dot - ".jpg", ".png", etc.
*   size - the file size in bytes (null if not available)

### complete

Fires when all active uploads have completed either successfully or with errors.



Note: The complete event fires only when the upload is in
[async mode](/getting-started/web/upload/modes#asynchronous-mode).

#### Example

    $("#photos").kendoUpload({
        // ...
        complete: onComplete
    });

    function onComplete(e) {
        // The upload is now idle
    }

### error

Fires when an upload / remove operation has failed.



Note: The error event fires only when the upload is in
[async mode](/getting-started/web/upload/modes#asynchronous-mode).

#### Example

    $("#photos").kendoUpload({
        // ...
        error: onError
    });

    function onError(e) {
        // Array with information about the uploaded files
        var files = e.files;

        if (e.operation == "upload") {
            alert("Failed to uploaded " + files.length + " files");
        }
    }

#### Event Data

##### e.files `Array`

List of the files that were uploaded or removed . Each file has:


*   name
*   extension - the file extension
        including the leading dot - ".jpg", ".png", etc.
*   size - the file size in bytes (null if not available)

##### e.operation `String`

- "upload" or "remove".

##### e.XMLHttpRequest `Object`

This is either the original XHR used for the operation or a stub containing:


*   responseText
*   status
*   statusText
Verify that this is an actual XHR before accessing any other fields.

### progress

Fires when upload progress data is available.


Note: The progress event fires only when the upload is in
[async mode](/getting-started/web/upload/modes#asynchronous-mode).

Note: The progress event is not fired in IE.
See [Supported Browsers](/getting-started/web/upload/supported-browsers)

#### Example

    $("#photos").kendoUpload({
        // ...
        progress: onProgress
    });

    function onProgress(e) {
        // Array with information about the uploaded files
        var files = e.files;

        console.log(e.percentComplete);
    }

#### Event Data

##### e.files `Array`

List of the files that are being uploaded. Each file has:


*   name
*   extension - the file extension
        including the leading dot - ".jpg", ".png", etc.
*   size - the file size in bytes (null if not available)

##### percentComplete `Number`

Upload progress (0 - 100)

### remove

Fires when an uploaded file is about to be removed.
Cancelling the event will prevent the remove.

#### Example

    $("#photos").kendoUpload({
        // ...
        remove: onRemove
    });

    function onRemove(e) {
        // Array with information about the removed files
        var files = e.files;

        // Process the Remove event
        // Optionally cancel the remove operation by calling
        // e.preventDefault()
    }

#### Event Data

##### e.files `Array`

List of the files that were uploaded or removed . Each file has:


*   name
*   extension - the file extension
        including the leading dot - ".jpg", ".png", etc.
*   size - the file size in bytes (null if not available)

##### data `Object`

Optional object that will be
sent to the save handler in the form of key/value pairs.

### select

Triggered when a file(s) is selected. Note: Cancelling this event will prevent the selection from
occurring.

#### Wire-up an event handler that triggered when a user selects a file(s)

    var onSelect = function(e) {
        $.each(e.files, function(index, value) {
            console.log("Name: " + value.name);
            console.log("Size: " + value.size + " bytes");
            console.log("Extension: " + value.extension);
        });
    };

    // initialize and configure an Upload widget with a select event handler
    $("#photos").kendoUpload({
        // ...
        select: onSelect
    });

#### Event Data

##### e `Object`

A custom event object. The event can be cancelled just like when using a standard jQuery event object via `e.preventDefault();`

##### e.files `Array`

An array of the selected files.

*   name - the name of a selected file, including its extension
*   extension - the file extension of a selected file, including the leading dot (i.e. ".jpg")
*   size - the size (in bytes) of a selected file (null, if unavailable)
*   rawFile - an in-memory representation of a selected file

### success

Fires when an upload / remove operation has been completed successfully.



Note: The success event fires only when the upload is in
[async mode](/getting-started/web/upload/modes#asynchronous-mode).

#### Example

    $("#photos").kendoUpload({
        // ...
        success: onSuccess
    });

    function onSuccess(e) {
        // Array with information about the uploaded files
        var files = e.files;

        if (e.operation == "upload") {
            alert("Successfully uploaded " + files.length + " files");
        }
    }

#### Event Data

##### e.files `Array`

List of the files that were uploaded or removed . Each file has:


*   name
*   extension - the file extension
        including the leading dot - ".jpg", ".png", etc.
*   size - the file size in bytes (null if not available)

##### e.operation `String`

"upload" or "remove".

##### e.response `String`

the response object returned by the server.

##### e.XMLHttpRequest `Object`

This is either the original XHR used for the operation or a stub containing:


*   responseText
*   status
*   statusText
Verify that this is an actual XHR before accessing any other fields.

### upload

Fires when one or more files are about to be uploaded.
Cancelling the event will prevent the upload.

Note: The upload event fires only when the upload is in
[async mode](/getting-started/web/upload/modes#asynchronous-mode).

#### Example

    $("#photos").kendoUpload({
        // ...
        upload: onUpload
    });

    function onUpload(e) {
        // Array with information about the uploaded files
        var files = e.files;

        // Check the extension of each file and abort the upload if it is not .jpg
        $.each(files, function() {
            if (this.extension != ".jpg") {
                alert("Only .jpg files can be uploaded")
                e.preventDefault();
            }
        });
    }

#### Example

    $("#photos").kendoUpload({
        // ...
        upload: onUpload
    });

    function onUpload(e) {
        var xhr = e.XMLHttpRequest;
        if (xhr) {
            xhr.addEventListener("readystatechange", function(e) {
                if (xhr.readyState == 1 /* OPENED */) {
                    xhr.setRequestHeader("X-Foo", "Bar");
                }
            });
        }
    }

#### Event Data

##### e.files `Array`

List of the files that will be uploaded. Each file has:


*   name
*   extension - the file extension
        including the leading dot - ".jpg", ".png", etc.
*   size - the file size in bytes (null if not available)

##### data `Object`

Optional object that will be
sent to the save handler in the form of key/value pairs.

##### e.XMLHttpRequest `Object`

Note: Will be *undefined* if the browser does not support File API.

The XMLHttpRequest instance that will be used to carry out the upload.
The request will be in UNSENT state.

