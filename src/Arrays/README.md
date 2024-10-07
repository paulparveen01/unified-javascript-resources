# Basic Functions

#### Add Elements
```javascript
.push - It will add element to the end of array
.unshift - It will add element to the beginning of array
```
#### Remove Elements
```javascript
.pop - remove last element
.shift - remove first element
```
*****Note - All above operations will modify original array**

#### Create slice (It'll not modify original array) & splice (It'll modify original array)
```javascript
.slice - Give you slices by cutting array into pieces based on index
arr.slice(startIndex, endIndex)
const str = [1,2,3,4,5,6,7];
const sliceRes = str.slice(2, 5)); // store result in variable and it will print [3,4,5]
[Examples](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice#return_a_portion_of_an_existing_array)
```

```javascript
.splice - Give you array after addition or replacement of element
splice(startIndex, deleteCount, item1, item2, /* …, */ itemN)
var str=['j','u','r','g','e','n'];
str.splice(2, 3); // no need to store result in var and it will print [j,u,n]
[Examples](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice#remove_0_zero_elements_before_index_2_and_insert_drum)
```

#### Set

# Handson, practical questions, scenario based questions

#### Push 2D array
```javascript
let arry = []
arry.push(["value_1", "value2"],["abc"])
Output - [ [ 'value_1', 'value2' ], [ 'abc' ] ]
```
#### Reverse 1D array elements
```javascript
const arr2 = ["a", "vv", "ty"]
// sol.1
arr2.reverse()
//console.log(arr2)

// sol.2
let newa = [];
for(let i=(arr2.length-1); i >= 0; i--) {
    newa.push(arr2[i])
}
//console.log(newa)
```
#### Reverse 2D array elements
```javascript
const input =[
    ['Work', 9],
    ['Eat', 1],
    ['Commute', 2,5,7],
    ['Play Game', 1],
    ['Sleep', 7]
];

// sol.1
let reversedArr = [];
input.reverse().map((elemArr) => {
    reversedArr.push(elemArr.reverse()) // reverse the inside array element
})
//console.log(reversedArr)

//sol.2
for(let i=(input.length-1); i >=0 ; i--) {
    let subarr = []
    for(let j=(input[i].length-1); j>=0; j--) {
        subarr.push(input[i][j])
    }
    reversedArr.push(subarr)
}
//console.log(reversedArr)
```
#### Convert 1D to 2D array
```javascript
var simpleArr = [1,2,3,4,5,6,7,8,9];

// sol1
var nArr = [];
while(simpleArr.length > 0) {
    // splice needed as it will modify the original array
    nArr.push(simpleArr.splice(0,2)); //second argument will create arrays with 2 elements in it.
}
// console.log(nArr)
```
#### Convert 2D to 1D array, Also know as flattern the array
```javascript
const flattern = []
for(let i=0; i<input.length; i++) {
    if(Array.isArray(input[i])) {
        flattern.push(...input[i])
    } else {
        flattern.push(input[i])
    }
    
}
// console.log(flattern)
```
#### Convert multi-D to 1d (flattern)
```javascript
let multiD = [
    [1, 2],
    [3, 4],
    [5, 6, [7, 8], 9],
    [10, 11, 12]
]

// sol1
let flattened = multiD.flat(2); // you can pass flat level also
// console.log(flattened)

// sol2
function flatMulti(multiD) {
    let flattern = []
    multiD.forEach((elem) => {
        if(!Array.isArray(elem)) {
            flattern.push(elem)
        } else {
            return flattern.push(...flatMulti(elem))
        }
    })
    return flattern
}
// console.log(flatMulti(multiD))
```
#### Flattern the object
```javascript
const multiDArr = {
    a: 1,
    b:2,
    c: {
        d: 6,
        e: 7
    }
}

const flatternObj = {}
Object.entries(multiDArr).forEach(([k,v]) => {
    if(typeof v !== 'object') flatternObj[k] = v
    else {
        Object.assign(flatternObj, v)
    }
})
// console.log(flatternObj)
```
#### Separate num and string from given array
```javascript
const ar = [1,2,3,'a','b',4,'c']

// sol1
const catArr = []
catArr["stringElem"] = []
catArr["numberElem"] = []
for(let i=0; i<ar.length; i++) {
    const currEl = ar[i]
    if(typeof currEl == "string") {
        catArr["stringElem"].push(currEl)
    } else if(typeof currEl == "number") {
        catArr["numberElem"].push(currEl)
    } 
}
// console.log(catArr)

// sol2
const resss = ar.reduce((prev, curr) => {
    (typeof curr == 'number') ? prev["number"].push(curr) : prev["string"].push(curr) 
    return prev; 
}, {"number": [], "string":[]})
// console.log(resss)
```
#### Remove duplicate from array OR find unique
```javascript
const array = [1,3,4,3,5,2,3,4]

// sol1
// console.log([...new Set(arr)]) // best solution

// sol2
let uniqueArr=[]
for(let i=0; i<array.length; i++){
    if(!uniqueArr.includes(array[i])) {
        uniqueArr.push(array[i])
    }
}
// console.log(uniqueArr)

// sol3
const ress= array.filter((elem, index) => array.indexOf(elem) == index)
// console.log(ress)
```
#### Find duplicate from array
```javascript
// sol1
let duplicateArr = []
let seen = []
for(let i=0; i< array.length; i++) {
    if(seen.includes(array[i])) {
        duplicateArr.push(array[i])
    }
    seen.push(array[i])
}
// console.log(duplicateArr)

// sol2
const res= array.filter((elem, index) => array.indexOf(elem) !== index)
// console.log(res)
```
#### Find single number/letter not repeating in array
```javascript
// sol1
const valArr = [3,3,8,3,4,4,5]
const singleUniue = valArr.find((elem) => valArr.indexOf(elem) == valArr.lastIndexOf(elem))
// console.log(singleUniue)

// sol2 - count each char repeatition
let occurr = {}
for(let i=0; i< valArr.length; i++) {
    if(!occurr[valArr[i]]) occurr[valArr[i]] = 1
    else occurr[valArr[i]]++
}
const ressOcc = Object.keys(occurr).find(key => occurr[key] == 1)
// console.log(ressOcc)
```
#### Find min/max element in array (without sorting)
```javascript
let minNum = Infinity
let maxNum = -Infinity
for(let i=0; i<valArr.length; i++) {
    const currVal = valArr[i]
    if(currVal < minNum) minNum = currVal
    if(currVal > maxNum) maxNum = currVal
}
// console.log(minNum+'~~'+maxNum)
```
#### Count occurences of elements in array
```javascript
const valArr = [3,3,8,3,4,4,5]
const occurence = {}
for(let i=0; i<valArr.length; i++) {
    const curElem = valArr[i]
    if(!occurence[curElem]) occurence[curElem] = 1
    else occurence[curElem] += 1
}
// console.log(occurence)
```
#### Move all negative element to end OR move all zero's to end
```javascript
const arrays1 = [1,0,2,3,0,4,0]
const elemNeedToMove = 0

arrays1.sort((a,b) => a-b)
let left = 0
let right = arrays1.length-1
while(left < right) {
    const leftElem = arrays1[left]
    const rightElem = arrays1[right]
    if(rightElem == elemNeedToMove) {
        right--
    } else { // swap element & move left pointer
        arrays1[left] = rightElem
        arrays1[right] = leftElem
        left++
    }
}
// console.log(arrays1)
```
#### Find union of two sorted array with no duplicates
```javascript
const arrayS1 = [1,2,2,3,4,5]
const arrayS2 = [3,0,4,12]

arrayS1.sort((a,b) => a-b)
arrayS2.sort((a,b) => a-b)
const concated = arrayS1.concat(arrayS2)
const unique = new Set(concated)
console.log([...unique])
```
#### Find intersection of two sorted array
```javascript
// sol1
let intersection = []
for(let i=0; i< arrayS1.length; i++) {
    // if elem is present in 2nd array
    if(arrayS2.findIndex((elem) => elem == arrayS1[i]) > -1) {
        intersection.push(arrayS1[i])
    }
}
// console.log(intersection)

// sol2
const intrsc = arrayS1.filter((elem, index) => arrayS2.indexOf(elem) > -1)
// console.log(intrsc)
```
#### Two sum problem (find two elements whose sum is equal to given value)
```javascript
const arraySum = [3, 5, -4, 8, 11, 1, -1, 6];
const targetSum = 10

let leftIndex = 0;
let rightIndex = arraySum.length - 1
const sortedArray = arraySum.sort((a, b) => a-b)
let finalDouble = []
while(leftIndex < rightIndex) {
    const currentSum = arraySum[leftIndex] + arraySum[rightIndex];
    if(currentSum == targetSum) {
        finalDouble.push([arraySum[leftIndex], arraySum[rightIndex]])
        leftIndex++
        rightIndex--
    } else if(currentSum < targetSum) {
        leftIndex++
    } else {
        rightIndex--
    }
}
// console.log(finalDouble)
```
#### Three sum problem (find three elements whose sum is equal to given value)
```javascript
const arrayTs = [12, 3, 1, 2, -6, 5, -8, 6];
const targetTSum = 0
let finalTriplet = []
for (let i = 0; i < arrayTs.length; i++) {
    let left = i+1
    let right = arrayTs.length-1
    while(left < right) {
        const sum = arrayTs[i] + arrayTs[left] + arrayTs[right]
        if(sum == targetTSum) {
            finalTriplet.push([arrayTs[i], arrayTs[left], arrayTs[right]])
            left++
            right--
        } else if(sum < targetTSum) {
            left++
        } else {
            right--
        }
    }
}
// console.log(finalTriplet)
```
#### Rotate array (90 degree clockwise)
```javascript
const inputMatrix =
[
     [1,2,3],
     [4,5,6], 
     [7,8,9]
]
const outputMatrix = inputMatrix[0].map((val, index) => inputMatrix.map(row => row[index]).reverse())  
/*const outputMatrix = [
    [7,4,1]
    [8,5,2]
    [9,6,3]
]*/
```





