### Bubble sort implementation in JavaScript

```
function bubbleSort(arr){
  for( var i = 0; i < arr.length; i++){
    for( var k = 0; k < arr.length; k++){
      if( arr[k] > arr[k + 1]) {
        var tmp = arr[k];
        arr[k] = arr[k + 1];
        arr[k + 1] = tmp;
      }
    }
  }
  return arr
}
```

improvement: flag avoids iteration if already sorted

```
function bubbleSort (arr) {
  for(var i = 0; i < arr.length; i++) {
    var flag = false;
    for(var k = 0; k < arr.length - i - 1; k++) {
      if(arr[k] > arr[k + 1]) {
        var tmp = arr[k];
        arr[k] = arr[k + 1];
        arr[k + 1] = tmp;
        flag = true;
      }
    }
    if(!flag) {
      break;
    }
  }
  return arr
}
```

Complexity of Bubble Sort is **O(n2)**

Space complexity for Bubble Sort is **O(1)**

Advantage:
* simplicity
