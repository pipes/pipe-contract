[![Build Status](https://travis-ci.org/KevinGrandon/pipe-contract.svg?branch=master)](https://travis-ci.org/KevinGrandon/pipe-contract)

# pipe-contract

Pipe contract is a library which validates pipe methods and arguments. This protects developers and helps control API methods.

## Get the code
```
bower install KevinGrandon/pipe-contract
```

## Example Usage

**Include pipe-contract.js in your page**
```html
<script defer src="/bower_components/pipe-core/pipe.js"></script>
<script defer src="/bower_components/pipe-contract/pipe-contract.js"></script>
```

**Usage**

```js
var pipe = new Pipe();
PipeContract.implement(pipe, contract);
```

**Or if using a worker**
```js
importScripts('/bower_components/pipe-core/pipe.js');
importScripts('/bower_components/pipe-core/pipe-contract.js');

var pipe = new Pipe();
PipeContract.implement(pipe, contract);
```


**Example Contract Syntax**

```js
/**
 * Each contract object maps an available event to a definition. If a message does not
 * pass validation an error will be thrown.
 * 
 * context -
 * The context key filters on available contexts. This means the contract
 * will not allow the method in other contexts than those specified.
 *
 * args -
 * You can validate each key of the params object when requesting data based on type.
 */
var contract = {
  getAll: {
    args: {
      filter: Object
    },
    context: 'SharedWorker'
  },
  getOne: {
    args: {
      id: Number
    },
    context: 'Worker'
  },
  save: {
    args: {
      id: Number,
      name: String
    },
    context: 'SharedWorker'
  },
  cacheInfo: {
    args: {
      id: String
    },
    context: 'ServiceWorker'
  }
};
```
