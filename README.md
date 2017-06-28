# circular-buffer
NodeJS circular buffer based on native Buffer

## Installation
`npm install circular-buffer --save`

## Example
```
var CircularBuffer = require('circular-buffer');

var buffer = new CircularBuffer(5);

buffer.put(Buffer.from([10,11,12]));
console.log('There is ', buffer.size(), 'elements in the buffer');
console.log('buffer[0]:', buffer[0]); // 12

buffer.put(Buffer.from([13,14,15,16]));
console.log('There is ', buffer.size(), 'elements in the buffer');
console.log('buffer[0]:', buffer[0]); // 12
console.log('buffer[5]:',buffer[5]); // 16

console.log('First three elements of the buffer:', buffer.get(3));
console.log('There is ', buffer.size(), 'elements in the buffer');
console.log('buffer[0]:', buffer[0]); // 12

[1,2,3,4,5,6].forEach(element => buffer.push(element));
console.log('There is ', buffer.size(), 'elements in the buffer');
console.log('buffer[0]:', buffer[0]); // 12
console.log('buffer[5]:',buffer[5]);  // 16

while(buffer.size() > 0) {
    console.log(buffer.pop());
}
console.log('There is ', buffer.size(), 'elements in the buffer');
```
## Documentation
### new CircularBuffer(size)

Constructs a circular buffer.

#### Arguments
- `size` *(Number)*: The initial size of the buffer in bytes. Defaults to 1024.

-----

###  CircularBuffer#capacity()

#### Returns
*(Number)* Returns the maximum storage capacity of the buffer.

-----

###  CircularBuffer#size()

#### Returns
*(Number)* Returns the number of elements in the buffer.

-----

###  CircularBuffer#push(element)

#### Arguments
- `element` *(Number)*: Add a single element at the end of the buffer.

#### Returns
*(Boolean)* true if the element is correctly inserted.

-----

###  CircularBuffer#pop()

#### Returns
*(Number)* Returns the first element of the buffer.

-----

###  CircularBuffer#put(enumerable)

#### Arguments
- `enumerable`: Each element of this enumerable variable is inserted in the buffer.

#### Returns
*(Boolean)* Returns true if the elements are correctly inserted.

-----

###  CircularBuffer#get(size)

#### Arguments
- `size` *(Number)*: The number of elements to retrieve.

#### Returns
*(Buffer)* Returns a new buffer containing the  `size` first elements of the buffer.

-----

###  CircularBuffer#getRawBuffer()

#### Returns
*(Buffer)* Returns the raw Buffer using by the CircularBuffer instance.

-----

###  CircularBuffer#accessor[index]

#### Arguments
- `index` *(Number)*: The index of the element to consult.

#### Returns
*(Number)* Returns the element at the `index` position in the buffer.


