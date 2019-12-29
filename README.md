# node-red-contrib-send-form
This is a node-red node for posting http(s) requests containing files as multipart formData. Currently a work in progress.

## Installation
run npm -g install node-red-contrib-send-form

## Features
Pulled together using some of the best of parts of other node-red-contrib nodes (particularly node-red-contrib-http-request), and the best parts of stackoverflow.
Currently only sends files. However, there are future plans to handle other types multipart/form-data.

## Usage
Required inputs:
* url (this is specified on the node) 
* file source type:
  - base64 or binary buffer

it is possible to pass the buffer into the node as part of the msg:
  
  ```javascript
  msg.payload = {
    file: {
      field: 'file',
      data: msg.payload,
      type: 'binary',
      name: 'test'
    },
    formOptions: {
      params: '',
    }
  }
```
will be the same as:

```html
  <form method=post enctype=multipart/form-data>
    <input type=textbox name=params value="">
    <input type=file name=file>
  </form>
```

**Source type**

Can be selected within the node from a dropdown menu "type" or passed in "msg.payload.file.type". Payload overrides the dropdown menu.

Currently accepts  
- Base64
- Binary

**Form Fields** as part of payload, will be added to form
```html
<input type=textbox name=params value="test">
```

becoms
  ```javascript
msg.payload.formOptions.params = 'test':
```

## Why this module?
As of december 2019, NodeRed does not yet support sending multipart form-data. This module aims to begin to close that gap.

There is always room for improvement, and new ideas are valued. Feel free to submit pull requests to make this library even better.