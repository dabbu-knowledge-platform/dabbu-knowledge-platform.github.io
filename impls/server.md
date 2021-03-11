---
layout: home
title: Dabbu Files API Server
nav_order: 13
parent: Clients and API Implementations
---

# Dabbu Files API Server

The Dabbu Files API Server allows apps abstract access to the user's information stored with multiple providers. It is an implementation of the Dabbu Files API.

## Installation

To install the server on your computer, you can simply download the latest version of it [here](https://github.com/dabbu-knowledge-platform/files-api-server/releases/latest).

## Running the server

> **Note**: It is **recommended** that you move the executable to a separate folder (the servers and CLI can be put in the same folder) and run it from there. This is because the server will create a folder `_dabbu` which contains several important files. When moving the executable anywhere else, make sure you move the `_dabbu` folder as well.

On Windows, simply double click the file to run it (it will be a `.exe`).

On Linux/MacOS, mark the file as an executable by running `chmod u+x path/to/file`. Then simply type in the path to the file in Terminal.

Always ensure the server is running before starting an application that uses it.

If you run into any problems while installing or using the server, feel free to ask [here](https://github.com/dabbu-knowledge-platform/files-api-server/discussions/categories/q-a). We'll only be glad to help :)

## Applications that use the Dabbu Files API

- [Dabbu CLI](./cli)

## Code examples for HTTP requests

> To view the API specification (required URL params, headers, request body fields, etc), go [here](../files_api/index)

### Listing files and folders in a specific folder

**Using cURL:**

```bash
$ curl -i -X GET "http://localhost:8080/files-api/v1/data/<provider id>/<folder path>/?exportType=view" \
  > -H "Authorization: Bearer <access_token>" \ # Only needed if the provider requires authorization
  > -d "field1: value1" -d "field2: value2" # Only needed if the provider requires certain fields
```

**Using NodeJS:**

```js
// The library used to make HTTP requests to the Dabbu Server
// Add it to your project (if you are using nodejs) using `npm install axios`
// For browser, refer to https://github.com/axios/axios#installing
const axios = require('axios').default

// Get the server address, provider ID and URL encode the folder path
let server = 'http://localhost:8080'
let provider = 'hard_drive' || 'google_drive' || 'one_drive' || 'gmail'
let urlEncodedFolderPath = encodeURIComponent('/Downloads')

// The URL to send the request to
let url = `${server}/files-api/v1/data/${provider}/${encodedFolderPath}?exportType=view`
// Send a GET request
let res = await axios.get(url, {
  // Only needed if the provider requires certain fields, else
  // skip the data: {...} part entirely
  data: {
    field1: 'value1',
    field2: 'value2',
  },
  // Only needed if the provider requires authorization, else
  // skip the headers: {...} part entirely
  headers: {
    Authorization: `Bearer ${accessToken}`,
  },
})

// Note: we are not handling errors here as we are using async-await, which
// will throw an error if the server returns an error response.

// Check if there is a response
if (res.data.content.length > 0) {
  // Get the files from the response
  let files = res.data.content
  // Print the files
  console.log(JSON.stringify(files))
} else {
  // Else print out empty folder
  console.log('Empty folder')
}
```

**Using Python:**

```py
# Import the requests library
# Install it using `pip install requests`
# Refer to https://requests.readthedocs.io/en/master/
import requests
# To encode the folder path
import urllib

# The provider ID
providerId = 'hard_drive' or 'google_drive' or 'one_drive' or 'gmail'
# The folder path
folderPath = '/Downloads'

# The URL to send a GET request to
URL = 'http://localhost:8080/files-api/v1/data/{providerId}/{encodedFolderPath}?exportType=view'.format(
  providerId = providerId,
  encodedFolderPath = urllib.parse.quote(folderPath)
)

# Make the GET request
res = requests.get(
  url = URL,
  data = {
    # Only needed if the provider requires certain
    # fields in the request body
    'field1': 'value1'
  },
  headers = {
    # Only needed if the provider requires authorization
    'Authorization': 'Bearer {accessToken}'.format(accessToken = '<access_token>')
  }
)

# Extract the JSON from the response
data = res.json()

# Parse the response and check if there are files
if res.content.length > 0:
  # Print the files
  print(res.content)
else:
  # It is an empty folder
  print('Empty folder')
```

### Retrieving a file's data

**Using cURL:**

```bash
$ curl -i -X GET "http://localhost:8080/files-api/v1/data/<provider_id>/<folder_path>/<file_name>/?exportType=media" \
  > -H "Authorization: Bearer <access_token>" \ # Only needed if the provider requires authorization
  > -d "field1: value1" -d "field2: value2" # Only needed if the provider requires certain fields
```

**Using NodeJS:**

```js
// The library used to make HTTP requests to the Dabbu Server
// Add it to your project (if you are using nodejs) using `npm install axios`
// For browser, refer to https://github.com/axios/axios#installing
const axios = require('axios').default

// Get the server address, provider ID and URL encode the folder path
let server = 'http://localhost:8080'
let provider = 'hard_drive' || 'google_drive' || 'one_drive' || 'gmail'
let urlEncodedFolderPath = encodeURIComponent('/Downloads')
let urlEncodedFileName = encodeURIComponent('dabbu_server_log.txt')

// The URL to send the request to
let url = `${server}/files-api/v1/data/${provider}/${encodedFolderPath}?exportType=media`
// Send a GET request
let res = await axios.get(url, {
  // Only needed if the provider requires certain fields, else
  // skip the data: {...} part entirely
  data: {
    field1: 'value1',
    field2: 'value2',
  },
  // Only needed if the provider requires authorization, else
  // skip the headers: {...} part entirely
  headers: {
    Authorization: `Bearer ${accessToken}`,
  },
})

// Note: we are not handling errors here as we are using async-await, which
// will throw an error if the server returns an error response.

// Check if there is a response
if (res.data.content) {
  // Get the files from the response
  let file = res.data.content
  // Refer to the object description above to get the file data
  // You can fetch the file's content by running another GET
  // request on the file's contentURI (`file.contentURI`)
  console.log(JSON.stringify(file))
} else {
  // Else there was no response from the server or an error was thrown
  console.log(
    'No response from server, error should have been thrown before this'
  )
}
```

**Using Python:**

```py
# Import the requests library
# Install it using `pip install requests`
# Refer to https://requests.readthedocs.io/en/master/
import requests
# To encode the folder path
import urllib

# The provider ID
providerId = 'hard_drive' or 'google_drive' or 'one_drive' or 'gmail'
# The folder path
folderPath = '/Downloads'
# The file name
fileName = 'dabbu_server_log.txt'

# The URL to send a GET request to
URL = 'http://localhost:8080/files-api/v1/data/{providerId}/{encodedFolderPath}/{encodedFileName}?exportType=media'.format(
  providerId = providerId,
  encodedFolderPath = urllib.parse.quote(folderPath),
  encodedFileName = urllib.parse.quote(fileName)
)

# Make the GET request
res = requests.get(
  url = URL,
  data = {
    # Only needed if the provider requires certain
    # fields in the request body
    'field1': 'value1'
  },
  headers = {
    # Only needed if the provider requires authorization
    'Authorization': 'Bearer {accessToken}'.format(accessToken = '<access_token>')
  }
)

# Extract the JSON from the response
data = res.json()

# Parse the response and check if the server returned a file
if res.content != None:
  # Refer to the object description above to get the file data
  # You can fetch the file's content by running another GET
  # request on the file's contentURI (`file.contentURI`)
  print(res.content)
else:
  # An error occurred
  print('An error occurred: {err}'.format(err = res.error))
```

### Creating a new file

**Using cURL:**

```bash
$ curl -i -X POST "http://localhost:8080/files-api/v1/data/<provider_id>/<folder_path>/<file_name>/" \
  > -H "Authorization: Bearer <access_token>" \ # Only needed if the provider requires authorization
  > -F "content=@<path_to_local_file_to_upload>" \ # Required
  > -F "createdAtTime=2021-06-07T07:06:42Z" \ # Optional, if you want to set the createdAtTime of a file
  > -F "lastModifiedTime=2021-06-07T07:06:42Z" \ # Optional, if you want to set the lastModifiedTime of a file
  > -F "field1=value1" -F "field2=value2" # Only needed if the provider requires certain fields
```

**Using NodeJS:**

```js
// The library used to make HTTP requests to the Dabbu Server
// Add it to your project (if you are using nodejs) using `npm install axios`
// For browser, refer to https://github.com/axios/axios#installing
const axios = require('axios').default
// The library used to encode the request body as form data
// Required only in nodejs environments, not browsers
// Add it to your project (if you are using nodejs) using `npm install form-data`
const FormData = require('form-data')
// The file system library, to create a readable stream of a
// file's contents
const fs = require('fs')

// Get the server address, provider ID and URL encode the folder path
let server = 'http://localhost:8080'
let provider = 'hard_drive' || 'google_drive' || 'one_drive' || 'gmail'
let urlEncodedFolderPath = encodeURIComponent('/Downloads')
let urlEncodedFileName = encodeURIComponent('dabbu_server_log.txt')

// The path to a local file to upload
let localFilePath = './dabbu_server_log.txt'

// Make a form data object to upload the file's contents
let formData = new FormData()
// Add the file's data as a readable stream to the content field
formData.append('content', fs.createReadStream(localFilePath), {
  filename: 'dabbu_server_log.txt',
})

// Add whatever fields are required by the provider in the request
// body here
formData.append('field1', 'value1')

// If you want to set the createdAtTime or lastModifiedTime of the
// file while uploading, add that to the body
formData.append('createdAtTime', '2021-06-07T07:06:42Z')
formData.append('lastModifiedTime', '2021-06-07T07:06:42Z')

// Use the headers that the form-data modules sets
let formHeaders = formData.getHeaders()

// The URL to send the request to
let url = `${server}/files-api/v1/data/${provider}/${urlEncodedFolderPath}/${urlEncodedFileName}`
// Send a POST request
let res = await axios.post(url, formData, {
  headers: {
    ...formHeaders, // The form headers
    Authorization: `Bearer ${accessToken}`, // Only needed if the provider requires authorization
  },
})

if (res.status === 201) {
  // File was created
  console.log('File created successfully')
} else {
  // Else there was no response from the server or an error was thrown
  console.log(
    'No response from server, error should have been thrown before this'
  )
}
```

**Using Python:**

```py
# Import the requests library
# Install it using `pip install requests`
# Refer to https://requests.readthedocs.io/en/master/
import requests
# To encode the folder path
import urllib

# The provider ID
providerId = 'hard_drive' or 'google_drive' or 'one_drive' or 'gmail'
# The folder path
folderPath = '/Downloads'
# The file name
fileName = 'dabbu_server_log.txt'

# Open a local file
localFileHandle = open('./dabbu_server_log.txt', 'rb')

# The URL to send a post request to
# If you want to delete a folder, simply omit the file name
URL = 'http://localhost:8080/files-api/v1/data/{providerId}/{encodedFolderPath}/{encodedFileName}'.format(
  providerId = providerId,
  encodedFolderPath = urllib.parse.quote(folderPath),
  encodedFileName = urllib.parse.quote(fileName)
)

# Make the POST request
res = requests.post(
  url = URL,
  files = {
    'content': localFileHandle
  },
  data = {
    # In case you want to set the createdAtTime and
    # lastModifiedTime while uploading the file
    'createdAtTime': '2021-06-07T07:06:42Z',
    'lastModifiedTime': '2021-06-07T07:06:42Z',
    # Any additional fields the provider requires
    'field1': 'value1'
  },
  headers = {
    # Only needed if the provider requires authorization
    'Authorization': 'Bearer {accessToken}'.format(accessToken = '<access_token>')
  }
)

# Extract the JSON from the response
data = res.json()

# Parse the response and check if the server created the file
if res.ok:
  print('File successfully created')
else:
  # An error occurred
  print('An error occurred: {err}'.format(err = res.error))
```

### Updating a file's metadata and/or contents

**Using cURL:**

```bash
$ curl -i -X PUT "http://localhost:8080/files-api/v1/data/<provider_id>/<folder_path>/<file_name>/" \
  > -H "Authorization: Bearer <access_token>" \ # Only needed if the provider requires authorization
  > -F "content=@<path_to_local_file_to_upload>" \ # Optional, if you want to update the file's contents
  > -F "name=new_name" \ # Optional, if you want to rename the file
  > -F "path=/Documents" \ # Optional, if you want to move the file
  > -F "createdAtTime=2021-06-07T07:06:42Z" \ # Optional, if you want to update the createdAtTime of a file
  > -F "lastModifiedTime=2021-06-07T07:06:42Z" \ # Optional, if you want to update the lastModifiedTime of a file
  > -F "field1=value1" -F "field2=value2" # Only needed if the provider requires certain fields
```

**Using NodeJS:**

```js
// The library used to make HTTP requests to the Dabbu Server
// Add it to your project (if you are using nodejs) using `npm install axios`
// For browser, refer to https://github.com/axios/axios#installing
const axios = require('axios').default
// The file system library, to create a readable stream of a
// file's contents (only needed if you want to update the file's
// contents)
const fs = require('fs')

// Get the server address, provider ID and URL encode the folder path
let server = 'http://localhost:8080'
let provider = 'hard_drive' || 'google_drive' || 'one_drive' || 'gmail'
let urlEncodedFolderPath = encodeURIComponent('/Downloads')
let urlEncodedFileName = encodeURIComponent('dabbu_server_log.txt')

// The path to a local file to upload
let localFilePath = './dabbu_server_log.txt'

// Make a form data object to upload the file's contents
let formData = new FormData()
// Add the file's data as a readable stream to the content field
// (only if you want to update the file's contents)
formData.append('content', fs.createReadStream(localFilePath), {
  filename: 'dabbu_server_log.txt',
})

// Add whatever fields are required by the provider in the request
// body here
formData.append('field1', 'value1')

// If you want to update the name, path, createdAtTime or
// lastModifiedTime, add that to the body
formData.append('name', 'new_name')
formData.append('path', '/Documents')
formData.append('createdAtTime', '2021-06-07T07:06:42Z')
formData.append('lastModifiedTime', '2021-06-07T07:06:42Z')

// Use the headers that the form-data modules sets
let formHeaders = formData.getHeaders()

// The URL to send the request to
let url = `${server}/files-api/v1/data/${provider}/${urlEncodedFolderPath}/${urlEncodedFileName}`
// Send a PUT request
let res = await axios.put(url, formData, {
  headers: {
    ...formHeaders, // The form headers
    Authorization: `Bearer ${accessToken}`, // Only needed if the provider requires authorization
  },
})

if (res.status === 200) {
  // File was updated
  console.log('File successfully updated')
} else {
  // Else there was no response from the server or an error was thrown
  console.log(
    'No response from server, error should have been thrown before this'
  )
}
```

**Using Python:**

```py
# Import the requests library
# Install it using `pip install requests`
# Refer to https://requests.readthedocs.io/en/master/
import requests
# To encode the folder path
import urllib

# The provider ID
providerId = 'hard_drive' or 'google_drive' or 'one_drive' or 'gmail'
# The folder path
folderPath = '/Downloads'
# The file name
fileName = 'dabbu_server_log.txt'

# Open a local file
localFileHandle = open('./dabbu_server_log.txt', 'rb')

# The URL to send a put request to
# If you want to delete a folder, simply omit the file name
URL = 'http://localhost:8080/files-api/v1/data/{providerId}/{encodedFolderPath}/{encodedFileName}'.format(
  providerId = providerId,
  encodedFolderPath = urllib.parse.quote(folderPath),
  encodedFileName = urllib.parse.quote(fileName)
)

# Make the PUT request
res = requests.put(
  url = URL,
  files = {
    'content': localFileHandle
  },
  data = {
    # In case you want to update the name, path, createdAtTime or
    # lastModifiedTime, add that to the body
    'name': 'new_name'
    'path': '/Documents'
    'createdAtTime': '2021-06-07T07:06:42Z',
    'lastModifiedTime': '2021-06-07T07:06:42Z',
    # Any additional fields the provider requires
    'field1': 'value1'
  },
  headers = {
    # Only needed if the provider requires authorization
    'Authorization': 'Bearer {accessToken}'.format(accessToken = '<access_token>')
  }
)

# Extract the JSON from the response
data = res.json()

# Parse the response and check if the server updated the file
if res.ok:
  print('File successfully updated')
else:
  # An error occurred
  print('An error occurred: {err}'.format(err = res.error))
```

### Deleting a file or folder

**Using cURL:**

```bash
$ curl -i -X DELETE "http://localhost:8080/files-api/v1/data/<provider_id>/<folder_path>/<file_name>/" \ # omit the file name if you want to delete the folder
  > -H "Authorization: Bearer <access_token>" \ # Only needed if the provider requires authorization
  > -d "field1: value1" -d "field2: value2" # Only needed if the provider requires certain fields
```

**Using NodeJS:**

```js
// The library used to make HTTP requests to the Dabbu Server
// Add it to your project (if you are using nodejs) using `npm install axios`
// For browser, refer to https://github.com/axios/axios#installing
const axios = require('axios').default

// Get the server address, provider ID and URL encode the folder path
let server = 'http://localhost:8080'
let provider = 'hard_drive' || 'google_drive' || 'one_drive' || 'gmail'
let urlEncodedFolderPath = encodeURIComponent('/Downloads')
let urlEncodedFileName = encodeURIComponent('dabbu_server_log.txt')

// The URL to send the request to
let url = `${server}/files-api/v1/data/${provider}/${encodedFolderPath}?exportType=media`
// Send a DELETE request
let res = await axios.delete(url, {
  // Only needed if the provider requires certain fields, else
  // skip the data: {...} part entirely
  data: {
    field1: 'value1',
    field2: 'value2',
  },
  // Only needed if the provider requires authorization, else
  // skip the headers: {...} part entirely
  headers: {
    Authorization: `Bearer ${accessToken}`,
  },
})

// Note: we are not handling errors here as we are using async-await, which
// will throw an error if the server returns an error response.

// Check if there is a response
if (res.data.code === 200) {
  console.log('File deleted successfully')
} else {
  // Else there was no response from the server or an error was thrown
  console.log(
    'No response from server, error should have been thrown before this'
  )
}
```

**Using Python:**

```py
# Import the requests library
# Install it using `pip install requests`
# Refer to https://requests.readthedocs.io/en/master/
import requests
# To encode the folder path
import urllib

# The provider ID
providerId = 'hard_drive' or 'google_drive' or 'one_drive' or 'gmail'
# The folder path
folderPath = '/Downloads'
# The file name
fileName = 'dabbu_server_log.txt'

# The URL to send a DELETE request to
# If you want to delete a folder, simply omit the file name
URL = 'http://localhost:8080/files-api/v1/data/{providerId}/{encodedFolderPath}/{encodedFileName}'.format(
  providerId = providerId,
  encodedFolderPath = urllib.parse.quote(folderPath),
  encodedFileName = urllib.parse.quote(fileName)
)

# Make the DELETE request
res = requests.delete(
  url = URL,
  data = {
    # Only needed if the provider requires certain
    # fields in the request body
    'field1': 'value1'
  },
  headers = {
    # Only needed if the provider requires authorization
    'Authorization': 'Bearer {accessToken}'.format(accessToken = '<access_token>')
  }
)

# Extract the JSON from the response
data = res.json()

# Parse the response and check if the server deleted the file
if res.ok:
  print('File successfully deleted')
else:
  # An error occurred
  print('An error occurred: {err}'.format(err = res.error))
```

### Getting a list of enabled providers on the server

**Using cURL:**

```bash
$ curl -i -X GET "http://localhost:8080/files-api/v1/providers"
```

**Using NodeJS:**

```js
// The library used to make HTTP requests to the Dabbu Server
// Add it to your project (if you are using nodejs) using `npm install axios`
// For browser, refer to https://github.com/axios/axios#installing
const axios = require('axios').default

// Get the server address, provider ID and URL encode the folder path
let server = 'http://localhost:8080'

// The URL to send the request to
let url = `${server}/files-api/v1/providers`
// Send a GET request
let res = await axios.get(url)

// Note: we are not handling errors here as we are using async-await, which
// will throw an error if the server returns an error response.

// Check if there is a response
if (res.data.content.providers.length > 0) {
  // Get the enabled providers from the response
  let enabledProviders = res.data.content.providers
  // Print the enabled providers
  console.log(enabledProviders)
} else {
  // There are no enabled providers
  console.log('No providers enabled')
}
```

**Using Python:**

```py
# Import the requests library
# Install it using `pip install requests`
# Refer to https://requests.readthedocs.io/en/master/
import requests

# The URL to send a GET request to
URL = 'http://localhost:8080/files-api/v1/providers'

# Make the GET request
res = requests.get(url = URL)

# Extract the JSON from the response
data = res.json()

# Parse the response and check if there are any enabled providers
if res.content.providers.length > 0:
  # Print the any enabled providers
  print(res.content.providers)
else:
  # There are no enabled providers
  print('No providers enabled')
```

### Getting a file from cache (INTERNAL)

**GET**: `/internal/cache/:filePath`

- Request parameters: [Compulsory]

  - `filePath`: Path to the file - `string`

- Request body: [Empty]

- Response:

  - Readable stream of file contents

- Errors:
  - `400`: The file path was incorrect - `malformedUrl`
  - `404`: The file was not found - `notFound`
  - `500`: Internal server error, used if an uncaught exception appears - `internalServerError`

**To be used only by provider modules that process file content and deliver it in a different format. For example, the [Gmail provider module](#gmail) converts a thread into a zip file containing messages and attachments and stores it in cache. To allow clients to retrieve it, it creates a URI with the file path within the cache folder.**

## Provider Modules

### Hard drive

**Provider specific fields**:

- Requires a field called `base_path` in every request's body. It is the path to be treated as root by the provider for all paths passed in requests.

### Google Drive

**Provider specific fields**:

- Requires an access token of the format `Bearer <token>` added to the header under the `Authorization` header field in every request. No fields need to be added to the request body.

**Provider specific features**:

- Currently, it is only possible to view and download files and folders shared with you (located in the hidden `/Shared` folder). Files and folders that you have shared with others will appear in their respective paths in your Drive. Sharing files and folders with others is not yet supported through this server module.
- Updating and creating shared files is also not supported.

### One Drive

**Provider specific fields**:

- Requires an access token of the format `Bearer <token>` added to the header under the `Authorization` header field in every request. No fields need to be added to the request body.

**Provider specific features**:

- Currently, it is only possible to view and download files and folders shared with you (located in the hidden `/Shared` folder). Files and folders that you have shared with others will appear in their respective paths in your Drive. Sharing files and folders with others is not yet supported through this server module.
- Updating and creating shared files is also not supported.

### Gmail

**Provider specific fields**:

- Requires an access token of the format `Bearer <token>` added to the header under the `Authorization` header field in every request. No fields need to be added to the request body.

**Provider specific features**:

- Labels are treated as folders
- Multiple labels can be specified (separated by commas) to search for threads with all the mentioned labels
- Threads are files
- The thread ID is used to get a thread and all its messages
- When getting a specific thread, the provider will create a zip file containing all messages in the thread, along with any inline images and attachments. The messages will be converted to markdown if in html.
