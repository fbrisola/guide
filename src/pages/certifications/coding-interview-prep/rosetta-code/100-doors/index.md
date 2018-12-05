---
title: 100 doors
---
## 100 doors

### Method:
- First we create an array with numDoors elements
- In the first time through all doors will be toggled to 'opened'
- Then we increment the step and toggle every nth door
- After the nth visit, we have the array with all doors marked as 'opened' or 'closed'
- We mark all 'opened' with its index+1 (remember an array starts with 0, so the nth array element corresponds to the (n+1)th door
- We mark all 'closed' doors with -1
- Then filter all positive numbers ('opened' doors)
- Return the final array

### Solution:
```js
function getFinalOpenedDoors (numDoors) {

  let doorsArray = [];

  for (var i = 0; i < numDoors; i++) {
    doorsArray.push('opened');
  }

  for (var j = 2; j <= numDoors; j++) {
    for (var k = j; k <= numDoors; k += j) {
      if (doorsArray[k-1] == 'opened') {
        doorsArray[k-1] = 'closed';
      }
      else {
        doorsArray[k-1] = 'opened';
      }
    }
  }

  return doorsArray.map((value, index) => {
    if (value == 'opened') {
      return index+1;
    } 
    else {
      return -1;
    }
  }).filter(value => value >= 0);
}
```

### Reference:
- map, filter
