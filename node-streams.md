# node streams

## multistream

<https://github.com/feross/multistream>

> A stream that emits multiple other streams one after another (streams2)

Handy for concating several files together, eg.

```js
const fs = require('fs')
const multistream = require('multistream')

// concat file1.txt and file2.txt, and write the result to all.txt
const streams = ['file1.txt', 'file2.txt'].map(filename => fs.createReadStream(filename))
multistream(streams)
  .pipe(fs.createWriteStream('all.txt'))
```
