
# redis-lock

  Node redis lock implementation for locking with a TTL.

## Installation

```
$ npm install segmentio/redis-lock
```

## Example

```js
var redis = require('redis').createClient();
var lock = require('redis-lock')({ redis: redis });

setInterval(function(){
  var id = Math.random() * 50 | 0;
  lock(id, '10s', function(err, locked){
    if (err) throw err;
    if (locked) return;
    console.log('%s - process', id);
  });
}, 10);
```

# License

  MIT