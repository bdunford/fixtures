#Fixtures

For quickly adding data to a node project. Ideal for mock or testing data.  Fixtures serve up json files as a data source.

Requires Nodejs http://nodejs.org


##Installing

__From the Command Line__<br />
npm install git+https://github.com/bdunford/fixtures.git

__package.json as a dependency__<br />
add "fixtures": "git+https://github.com/bdunford/fixtures.git" to dependencies <br />
```
{
    "name": "your-app",
    "version": "0.0.0",
    "private": true,
    "description": "just another node app",
    "dependencies": {
        "helpers": "git+https://github.com/bdunford/fixtures.git"
    }
}

```
__Raw__<br />
```git clone https://github.com/bdunford/fixtures```
<br />
_Be sure to run npm install from with in the __fixtures__ directory_


##Usage

Require fixtures in your javascript

```javascript
var fixtures = require('fixtures');

```

###Methods
__store__ returns an instance of Store for the matching JSON file found with in the fixtures directory If you had the following JSON file in your directory ```fixtures/cusomters.json```
```javascript
    fixtures.store('customers'); //will return
    {
        file: 'fixtures/customers.json',
        all: [Function],
        find: [Function]
    }
```
__stores__ returns an object containing all of the stores (JSON files) found with in the fixtures folder in you project.  If you had the following JSON files in your directory ```fixtures/cusomters.json``` and ```fixtures/orders.json```
```javascript
    fixtures.stores(); //will return
    {
        customers: {
            file: 'fixtures/customers.json',
            all: [Function],
            find: [Function] },
        orders: {
            file: 'spec/fixtures/orders.json',
            all: [Function],
            find: [Function] }
        }
    }
```

__Store.all__ returns the contents of the JSON file parsed to an object or array of objects for that store. If you had the following JSON file in your directory ```fixtures/cusomters.json```
```javascript
    fixtures.store('customers').all();
    //will return the content of "fixtures/cusomters.json" parsed to an array of objects
```

__Store.find__ returns the contents of the JSON file matching the filter object passed to in you had the following JSON file in your directory ```fixtures/cusomters.json```
```javascript
   fixtures.store("customers").find({lastName: "smith"});
//will return the content of "fixtures/cusomters.json" parsed to an array where the customers had a lastName of smith.
```
###Properties

__location__ can be set on fixtures to control the location of the JSON files. The default location is fixtures/
```javascript
fixtures.location = "./db/fixtures";
//would make fixtures look for JSON files in db/fixtures/ instead of fixtures/
```
