---
title: 2359-bulk-image-uploader-engineering-plan
type: work-item
item_type: task
project: houseplans.net
status: done
created: 2026-04-14
updated:
due: 2026-02-17
url: https://trello.com/c/TCyjX0Mz/2359-bulk-image-uploader-engineering-plan
assignee: Brian M.
---

# 2359-bulk-image-uploader-engineering-plan

## Description

**Server Side**

The main plan is to create a reusable file upload class that will be consumed or extended by the ajax class for each specific image type or image upload ajax endpoint. The customization for each file upload should be handled by the extended class.

- Create ajax endpoint that uses image.class.php to handle upload of specific image types.
    

·       The additional image information should be handled here along with any database related things. Some file uploads may not always interact with the database in future endeavors.

·       Create endpoint for saving of ordering images.

·       Catch exceptions from

Error conditions:

No Caption

Wrong File Type (images only)

Missing additional information for image

**UI Interface**

The ui changes will be handled with htmx. We can handle the image sort order via drag and drop, along with additional information changes. We will want to respond to the user with some sort of success or failure message when reordering images as well. The new images added when images exist should be added to the bottom of the list and then dragged to be reordered.

- The form should be able to support bulk drag and drop of images and setting of form values before upload.  [https://htmx.org/examples/file-upload/](https://htmx.org/examples/file-upload/)
    

·       Need a button to upload dropped images that “blocks” additional images to be added while uploading.

·       Provide UI progress bar updates for the upload action.

·       Disallow upload of incorrect file types before upload.

- Form needs to be able to handle additional options for each image type.
    

·       Caption of the image should always be saved.

·       Also may need display order, default image, etc. The

- Image library needs to be a horizontal with image in one column, and then the specific image info needed for the image to the right of it. We can use a smaller thumbnail size to keep the page shorter.
    
- Allow drag and drop sorting for images for display order [https://htmx.org/examples/sortable/](https://htmx.org/examples/sortable/)
    

·       On animation end update the sort order endpoint.

## Notes

