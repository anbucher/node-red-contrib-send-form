# node-red-contrib-send-form
This is a node-red node for posting http(s) requests containing files as multipart formData. Currently a work in progress.

## Installation
run npm -g install node-red-contrib-send-form

## Features
Pulled together using some of the best of parts of other node-red-contrib nodes (particularly node-red-contrib-http-request), and the best parts of stackoverflow.
Currently only sends files. However, there are future plans to handle other types multipart/form-data.

## Usage
Required node inputs:
* url (this is specified on the node) 
* file source type:
  - base64 or binary buffer

### File

* **Data**  | *Buffer*   
Needs to be passed in  ``` msg.payload.file.data```
* **Name of file field** | *String*    
Needs to be passed in  ``` msg.payload.file.field```

* **Name of file** | *String*   
Needs to be passed in  ``` msg.payload.file.name```

* **Source type** | *String*   
Can be selected within the node from a dropdown menu "type" or passed in ``` msg.payload.file.type```. Payload overrides the dropdown menu.

   Currently accepts  
   - base64
   - binary

### Form fields

Can be inserted within the node or passed as part of ```msg.payload.formOptions.<name of key>```

```javascript
msg.payload.formOptions.params = 'test':
```
is the same as

```html
<input type=textbox name=params value="test">
```

### Example ```msg.payload```
 
  ```javascript
  msg.payload = {
    file: {
      field: 'file',
      data: msg.payload,
      type: 'binary',
      name: 'file'
    },
    formOptions: {
      params: '',
    }
  }
```
same as:

```html
  <form method=post enctype=multipart/form-data>
    <input type=textbox name=params value="">
    <input type=file name=file>
  </form>
```

## Example flow
Check Node-RED Menu Import -> Examples for available examples 

## Why this module?
As of december 2019, NodeRed does not yet support sending multipart form-data. This module aims to begin to close that gap.

There is always room for improvement, and new ideas are valued. Feel free to submit pull requests to make this library even better.