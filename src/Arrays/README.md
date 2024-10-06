# Basic Functions

#### Add Elements
```
.push - It will add element to the end of array
.unshift - It will add element to the beginning of array
```
#### Remove Elements
```
.pop - remove last element
.shift - remove first element
```
**Note - All above operations will modify original array**

#### Create slice & splice
```
.slice - Cut array into pc based on index start from 1
arr.slice(fromIndex, untilIndex)
let str = [1,2,3,4,5,6,7];
console.log(str.slice(2, 5)); // give [3,4,5] // cut from 2 to 5
```
**Note - Do not modify original array**
```
.splice (modify original array) - Add or replace element on index start from 1
arr.splice(startIndex, # of elements need to remove, item_need_to_insert)
var str=['j','u','r','g','e','n'];
str.splice(2, 3); console.log(str) // j,u,n
```
**Note - Modify original array**


