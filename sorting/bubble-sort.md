Bubble sort implementation in JavaScript

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