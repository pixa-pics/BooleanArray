# Boolean Array (7kB minified & 0 dep.)

## Install

```script
npm install @asaitama/boolean-array
```

## Import

### Browser
```javascript
// First you'll need to import the script;
var BitArray = window.BitArray;
var SetFixed = window.SetFixed;
```

### NodeJS
```javascript
import { BitArray, SetFixed } from "@asaitama/boolean-array";
```

## BitArray
BitArray is a useful data structure that allows you to manipulate an array of bits efficiently. This object is perfect for situations where you need to work with bits directly. For instance, it can be useful in coding problems related to bit manipulation or when dealing with binary data. It provides methods to read, write, clear and set individual bits, as well as other utility functions.

## SetFixed
SetFixed is a set data structure implemented using the BitArray object. This is an efficient and compact data structure for storing non-repeated elements. SetFixed provides a variety of methods to manipulate the set such as adding, deleting, checking for membership, and iterating over the set.

## BitArray Documentation
The BitArray object provides an efficient bit-level manipulation of a typed array. It offers methods for setting, getting and manipulating individual bits within the array.

### Constructor
#### `BitArray(s)`
The constructor function takes a parameter `s`, which represents the size of the BitArray. This is used to initialize the internal Uint32Array. The function also initializes the `M_OR_` and `M_AND_` Uint32Arrays, which are used as masks for setting and clearing bits.

```javascript
let bitArray = new BitArray(64);
```

### Properties

#### `readFourBytes`
This getter function returns a function that reads a block of four bytes starting at index `i`, returning an array of the indices of the bits that are set within this block.

```javascript
let bitArray = new BitArray(64);
let read = bitArray.readFourBytes;
let result = read(4);
```

#### `readBit`
This getter function returns a function that reads the bit at index `i`, returning a boolean indicating whether the bit is set.

```javascript
let bitArray = new BitArray(64);
let read = bitArray.readBit;
let result = read(4);
```

#### `writeBit1`
This getter function returns a function that sets the bit at index `i` to 1.

```javascript
let bitArray = new BitArray(64);
let write = bitArray.writeBit1;
write(4);
```

#### `writeBit0`
This getter function returns a function that sets the bit at index `i` to 0.

```javascript
let bitArray = new BitArray(64);
let write = bitArray.writeBit0;
write(4);
```

#### `clear`
This getter function returns a function that clears all bits in the BitArray.

```javascript
let bitArray = new BitArray(64);
let clear = bitArray.clear;
clear();
```

#### `charge`
This getter function returns a function that sets all bits in the BitArray to 1.

```javascript
let bitArray = new BitArray(64);
let charge = bitArray.charge;
charge();
```

#### `length`
This getter function returns the length of the BitArray.

```javascript
let bitArray = new BitArray(64);
let length = bitArray.length;
console.log(length);
```

Please note that all methods described above are read-only and non-configurable. This means they cannot be re-assigned or changed.

## SetFixed Documentation
The SetFixed object provides a set data structure that allows efficient addition, deletion, and checks for membership. It offers methods for setting, getting and manipulating individual elements within the set.

### Constructor

#### `SetFixed(size)`
The constructor function takes a parameter size, which represents the size of the SetFixed. This is used to initialize the internal BitArray. **If size is an object (presumably an array-like object), then the SetFixed is initialized with those elements**.

```javascript
let setFixed = new SetFixed(64);
```

### Properties
#### `size`
This getter function returns the size of the SetFixed set, which is the number of elements in the set.

```javascript
let setFixed = new SetFixed(64);
let size = setFixed.size;
console.log(size);
```

#### `length`
This getter function returns the length of the BitArray used internally.

```javascript
let setFixed = new SetFixed(64);
let length = setFixed.length;
console.log(length);
```

#### `indexes`
This getter function returns an array of the indices of the bits that are set within the BitArray.

```javascript
let setFixed = new SetFixed(64);
let indexes = setFixed.indexes;
console.log(indexes);
```

#### `has`
This getter function returns a function that checks if a given index i is set within the BitArray.

```javascript
let setFixed = new SetFixed(64);
let has = setFixed.has;
console.log(has(4));
```

#### `add` & `bulkAdd`
This getter function returns a function that adds a given index i to the SetFixed.
If the index given is beyond the capacity of the instance, it will be resized correctly with a margin.
Don't worry about resizing or memory consumption, it is far more efficient than a traditional new Set() instance object if you deal with indexes below 1/4 million (indexes from 0 to 250000 will represent only a few 31kB in memory)

> It is as much as **2-3x faster and 4-6x lighter** for the JS Engine when used for managing pixel art selection state on canvas of 512x512 pixels than "new Set()" but is **limited to entire integer within a range**!!!

```javascript
let setFixed = new SetFixed(64);
let add = setFixed.add;
let bulkAdd = setFixed.bulkAdd;
add(4);
bulkAdd([1, 2, 3, 4, 5]);
```

#### `delete` & `bulkDelete`
This getter function returns a function that deletes a given index i from the SetFixed.

```javascript
let setFixed = new SetFixed(64);
let del = setFixed.delete;
let bulkDel = setFixed.bulkDelete;
del(4);
bulkDel([1, 2, 3, 4, 5]);
```

#### `clear`
This getter function returns a function that clears all elements in the SetFixed.

```javascript
let setFixed = new SetFixed(64);
let clear = setFixed.clear;
clear();
```

#### `charge`
This getter function returns a function that sets all bits in the BitArray to 1.

```javascript
let setFixed = new SetFixed(64);
let charge = setFixed.charge;
charge();
```

#### `invert`
This getter function returns a function that invert all bits in the BitArray.

```javascript
let setFixed = new SetFixed(64);
let invert = setFixed.invert;
invert();
```

#### `forEach`
This getter function returns a function that iterates over the elements in the SetFixed, applying a given function.

```javascript
let setFixed = new SetFixed(64);
let forEach = setFixed.forEach;
forEach(console.log);
```

#### `map`
This getter function returns a function that maps a given function over the elements in the SetFixed.

```javascript
let setFixed = new SetFixed(64);
let map = setFixed.map;
console.log(map(x => x * 2));
```

#### `filter`
This getter function returns a function that filters the elements in the SetFixed based on a given function.

```javascript
let setFixed = new SetFixed(64);
let filter = setFixed.filter;
console.log(filter(x => x % 2 === 0));
```

Please note that all methods described above are read-only and non-configurable. This means they cannot be re-assigned or changed.