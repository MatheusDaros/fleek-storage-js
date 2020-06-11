# Fleek Storage Js
Fleek Storage Js is an SDK to interact with Fleek Storage.

# Installation
The package is installed through npm.

`npm install fleek-storage-js`

The SDK can be imported after installation.

`import fleekStorage from 'fleek-storage-js'`

or...

`const fleekStorage = require('fleek-storage-js')`

# Getting Api Keys


The api key and secret can be generated on the Fleek Web app or from the Fleek CLI.
See [Getting an Api Key](https://docs.fleek.co/StorageSDK/GettingApiKeys)

# Methods
## get
The `get` method is for fetching individual files, either the content or related data such as the key, hash and publicUrl.

Example of usage:

```
cont myFile = await fleekStorage.get({
  apiKey: 'my-key',
  apiSecret: 'my-secret',
  key: 'my-file-key',
  getOptions: [
    'data',
    'bucket',
    'key',
    'hash',
    'publicUrl'
  ],
})
```

### Input parameters of get

|param  	|type  	|description  	|
|-:	|-	|-	|
| apiKey 	| String 	|  The api key used for authentication	|
| apiSecret 	| String 	|  The api secret used for authentication	|
| key 	|  String	| The key identifying the requested file in the bucket  	|
| bucket 	| String, optional, defaults to the default account bucket 	|  The name of the bucket containing the file. A bucket is created by default with every Fleek accounts	|
| getOptions 	| Array, optional, defaults to ['data'] 	| An array specifying what type of information to retrieve concerning the file.	Possible values for the array includes `data`, `bucket`, `hash`, `key`, `publicUrl`|


## upload

The `upload` method uploads a file, identified by a key, to a bucket.
The function returns the IPFS hash of the file.

Example of usage:

```
const uploadedFile = await fleekStorage.upload({
  apiKey: 'my-key',
  apiSecret: 'my-secret',
  key: 'my-file-key',
  data: fileContent,
})
```

### Input parameters of upload

|param  	|type  	|description  	|
|-:	|-	|-	|
| apiKey 	| String 	|  The api key used for authentication	|
| apiSecret 	| String 	|  The api secret used for authentication	|
| key 	|  String	| The key identifying the requested file in the bucket  	|
| bucket 	| String, optional, defaults to the default account bucket 	|  The name of the bucket containing the file. A bucket is created by default with every Fleek accounts	|
| data 	| Any 	| The data of the file to be uploaded |


## listFiles
The `listFiles` method is for fetching information about all files in a bucket such as the key, hash and publicUrl.

Example of usage:

```
const files = await fleekStorage.listFiles({
  apiKey: 'my-key',
  apiSecret: 'my-secret',
  getOptions: [
    'bucket',
    'key',
    'hash',
    'publicUrl'
  ],
})
```

### Input parameters of listFiles

|param  	|type  	|description  	|
|-:	|-	|-	|
| apiKey 	| String 	|  The api key used for authentication	|
| apiSecret 	| String 	|  The api secret used for authentication	|
| bucket 	| String, optional, defaults to the default account bucket 	|  The name of the bucket containing the file. A bucket is created by default with every Fleek accounts	|
| getOptions 	| Array, optional, defaults to ['key', 'bucket', 'publicUrl'] 	| An array specifying what type of information to retrieve concerning the file.	Possible values for the array includes `bucket`, `hash`, `key`, `publicUrl`|


## listBuckets
The `listBuckets` method returns an array of bucket names associated with the api key's account.

Example of usage:

```
const buckets = await fleekStorage.listBuckets({
  apiKey: 'my-key',
  apiSecret: 'my-secret',
})
```

### Input parameters of listFiles

|param  	|type  	|description  	|
|-:	|-	|-	|
| apiKey 	| String 	|  The api key used for authentication	|
| apiSecret 	| String 	|  The api secret used for authentication	|


## getFileFromHash

`getFileFromHash` is a utility function that downloads a file's data from Fleek's IPFS gateway using the hash. The key and secret is not required since the gateway is publicly available.

Example of usage:

```
const myFile = await fleekStorage.getFileFromHash({
  hash: 'bafybeige4bhzjvrptn7fdz7mqgigzoczcliqpuo7km4jm7vgjg2pbmuhna',
})
```

### Input parameters of getFileFromHash

|param  	|type  	|description  	|
|-:	|-	|-	|
| hash 	| String 	|  The hash of the requested file	|
