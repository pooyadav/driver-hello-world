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
2. Fetch data from outside and store in the datastore.
3. First to write data, it checks Arbiter for all datastores.
4. Then it writes to the datastore by composing a request - it sends arbiter key in the request.

when a datastore gets a request from a driver to read/write - (what does it do?)
### Manifest template 
In the manifest, two important things to notice here are "databox-type" and "resource-requirements" - "store".

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


```index.js fetches manifest from appstore ->  main.js - > server.js -> container-manager.js 
```

```/api/datasource/list
   /api/installed/list
   /api/:type/list
   /list-apps
   /api/install
```   

