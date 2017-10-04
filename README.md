# cyclic-buffer
NodeJS ciclyc (circular/ring) buffer based on native NodeJS Buffer.

## Installation
`npm install cyclic-buffer --save`

## Example
```
var CyclicBuffer = require('cyclic-buffer').default;

var buffer = new CyclicBuffer(5);

buffer.put(Buffer.from([10,11,12]));
console.log('There is ', buffer.size(), 'elements in the buffer');
console.log('buffer[0]:', buffer[0]); // 10
console.log('buffer[2]:', buffer[2]); // 12

buffer.put(Buffer.from([13,14,15,16]));
console.log('There is ', buffer.size(), 'elements in the buffer');
console.log('buffer[0]:', buffer[0]); // 12
console.log('buffer[4]:',buffer[4]); // 16
console.log('buffer[5]:',buffer[5]); // 12

console.log('First three elements of the buffer:', buffer.get(3));
console.log('There is ', buffer.size(), 'elements in the buffer');
console.log('buffer[0]:', buffer[0]); // 15

[1,2,3,4,5,6].forEach(element => buffer.push(element));
console.log('There is ', buffer.size(), 'elements in the buffer');
console.log('buffer[0]:', buffer[0]); // 2
console.log('buffer[4]:',buffer[4]);  // 6

while(buffer.size() > 0) {
    console.log(buffer.shift());
}
console.log('There is ', buffer.size(), 'elements in the buffer');
```
## Documentation
### new CyclicBuffer(size)

Constructs a ring buffer.

#### Arguments
- `size` *(Number)*: The initial size of the buffer in bytes. Defaults to 1024.

-----

###  CyclicBuffer#capacity()

#### Returns
*(Number)* Returns the maximum storage capacity of the buffer.

-----

###  CyclicBuffer#size()

#### Returns
*(Number)* Returns the number of elements in the buffer.

-----

###  CyclicBuffer#push(element)

#### Arguments
- `element` *(Number)*: Add a single element at the end of the buffer.

#### Returns
*(Boolean)* true if the element is correctly inserted.

-----

###  CyclicBuffer#shift()

Remove the first element of the buffer

#### Returns
*(Number)* Returns the first element of the buffer.

-----

###  CyclicBuffer#put(enumerable)

#### Arguments
- `enumerable`: Each element of this enumerable variable is inserted in the buffer.

#### Returns
*(Boolean)* Returns true if the elements are correctly inserted.

-----

###  CyclicBuffer#get(size)

Get a new buffer containing the  `${size}` first elements of the buffer without removing them from the cyclic buffer.

#### Arguments
- `size` *(Number)*: The number of elements to retrieve.

#### Returns
*(Buffer)* Returns a new buffer containing the  `${size}` first elements of the buffer.

-----

###  CyclicBuffer#reset()

Empty the buffer.

-----

###  CyclicBuffer#getRawBuffer()

#### Returns
*(Buffer)* Returns a reference to the raw Buffer using by the CyclicBuffer instance.

*Warning* : If you modify the raw buffer, this will modify your cyclic buffer.

-----

###  CyclicBuffer#accessor[index]

#### Arguments
- `index` *(Number)*: The index of the element to consult.

#### Returns
*(Number)* Returns the element at the `index` position in the buffer without removing it drom the buffer.


