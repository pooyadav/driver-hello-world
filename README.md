# databox hello-world-driver
A simple python hello-world-driver which connects with Databox.

The databox container manager install a driver, it reads the SLA associated with the driver and set following Environment Variables:
```
DATABOX_ARBITER_ENDPOINT
DATABOX_LOCAL_NAME
DATABOX_STORE_ENDPOINT
DATABOX_ROOT_CA
Localcontainername_PEM
Localcontainername.pem
Localcontainername_key=ARBITER_TOKEN
```
1. To integrate a driver as a databox driver, driver needs to have access to the keys and token to access stores.
2. Driver reqests a data-store by configuring it in the databox-manifest.json file - template shown below. When container manager install the driver, it also launches a datastore of the requested type.
3. Configure and create data types - template of information which need to provide to the API.
```
 template = {	description: 'Any Driver text',
        	contentType: 'text/json',
        	vendor: 'Databox Inc.',
        	type: 'A column/row description - for example - timeline in twitter',
       		datasourceid: 'Datasourceid',
       	 	storeType: 'store-json'
	   }
```
```
databox.registerDatasource(DATABOX_STORE_ENDPOINT, template)
```
4. Driver fetches data from a data-source and store in the datastore.
4. Then it writes to the datastore by composing a request - it sends arbiter key in the request.
5. In a "store" of type "store-json", following APIs could be called.



### Manifest template 
In the manifest, two important things to notice here are "databox-type" and "resource-requirements" - "store". When the driver is installed, a data store of type mentioned in "store" is launched.

{
	"manifest-version": 1,
	"name": "driver-hello-world",
	"databox-type": "driver",
	"version": "0.1.0",

	"description": "A template Databox driver in Python",
	"author": "Poonam Yadav <p.yadav@acm.org> (http://poonamyadav.net/)",
	"license": "MIT",
	"tags": [
		"template",
		"driver",
		"mock",
		"python"
	],

	"homepage": "https://github.com/me-box/lib-python-databox",
	"repository": {
		"type": "git",
		"url": "git+https://github.com/me-box/lib-python-databox"
	},
   
	"allowed-combinations": [],
	"resource-requirements": {
		"store": "store-json"
	}
}

From app-server, these are the following APIs exposed to SDK, which allows accessing of the databox.

```/api/datasource/list
   /api/installed/list
   /api/:type/list
   /list-apps
   /api/install
```   

