# merge-stream

Merge (interleave) a bunch of streams.

[![build status](https://secure.travis-ci.org/grncdr/merge-stream.svg?branch=master)](http://travis-ci.org/grncdr/merge-stream)

## Synopsis

```javascript
var stream1 = new Stream();
var stream2 = new Stream();

var merged = mergeStream(stream1, stream2);

var stream3 = new Stream();
merged.add(stream3);
merged.isEmpty();
//=> false
```

## Description

This is adapted from [event-stream](https://github.com/dominictarr/event-stream) separated into a new module, using Streams3.

## API

`merged.add`

A method to dynamically add more sources to the stream. The argument supplied to `add` can be either a source or an array of sources.

`merged.isEmpty`

A method that tells you if the merged stream is empty.

When a stream is "empty" (aka. no sources were added), it could not be returned to a gulp task.

So, we could do something like this:

```js
stream = require('merge-stream')();
// Something like a loop to add some streams to the merge stream
// stream.add(streamA);
// stream.add(streamB);
return stream.isEmpty() ? null : stream;
```

## License

MIT
