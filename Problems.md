### Maximum Sum Subsequence Non-Adjacent

```
var arr = [5,5,10,100,10,5];
// 110 

function sum(arr){
  var inc = 0;
  var exc = 0;
  for (var i=0; i<arr.length;i++){
    var incNew = exc + arr[i];
    exc = Math.max(exc, inc);
    inc = incNew
  }
  return Math.max(exc,inc)
}
sum(arr)
```

improvement: no need to start from index 0;

```
function sum(arr){
  var inc = arr[1];
  var exc = arr[0];
  for (var i=2; i<arr.length;i++){
    var incNew = exc + arr[i];
    exc = Math.max(exc, inc);
    inc = incNew
  }
  return Math.max(exc,inc)
}
```


### Pair of elements from array whose sum equals given number

```
// it uses hash, each given number used only once.
var sample_data = [0, 1, 100, 99, 0, 10, 90, 30, 55, 33, 55, 75, 50, 51,
        49, 50, 51, 49, 51];
    var n = 100;
    findPair(sample_data, n)

    function findPair(arr,n){
        var found = {};
        var results = [];

        for (var k=0; k<arr.length; k++){
            if (!found[arr[k]]) {
                found[arr[k]] = [true];
            } else {
                found[arr[k]].push(true)
            }
        }

        for (var i=0; i<arr.length; i++){
            var first = found[n-arr[i]];
            var second = found[arr[i]];
            if (first && first.length && second && second.length) {
                results.push({
                    a: arr[i],
                    b: n-arr[i]
                });
                first.pop();
                second.pop();
            }
        }
        return results
    }
```


### Longest Palindrome

```
function isPalindrome(s) {
  var rev = s.split("").reverse().join("");
  return s == rev;
}

function longestPalind(s){
	maxp = '';	
  for(var i=0; i < s.length; i++) {
  	var subs = s.substr(i, s.length);
  	for(var j=subs.length; j>=0; j--) {
  	  var sub_subs = subs.substr(0, j);
      if (sub_subs.length > maxp.length && isPalindrome(sub_subs)) {
    		if (sub_subs.length > maxp.length) {
    			maxp = sub_subs;
    		}
	    }
    }
  }
  return maxp;
}

console.log(longestPalind("abcxyzyxabcdaaa"));

// xyzyx
```

### Given an array of non-negative numbers, find continuous subarray with sum to S.


```
var arr = [1, 4, 20, 3, 10, 5], n = 33;

function sumFind(arr,sum){
  var curr_sum = 0;
  var start =0;
  for (var i=0; i<arr.length; i++){
    while(curr_sum > sum){
      curr_sum = curr_sum - arr[start];
      start++;
    }
    if(curr_sum===sum){
      return {start: start, end: i-1}
    }
    curr_sum += arr[i]
  }
}

sumFind(arr,n)
```

### Anagram Substring Search (Or Search for all permutations)

```
var str = "BACDGABCDA";
var pat = "ABCD";

function createFr(text){
  var fre = {};
  for (var i=0; i<text.length; i++){
    if (fre[text[i]]) {
      fre[text[i]]++
    } else {
      fre[text[i]] = 1;
    }
  }
  return fre;
}

function anagram(str,pat){
  var arr = [];
  var patFre = createFr(pat);
  for (var i=0; i<str.length; i++){
    var strFre = createFr(str.slice(i, pat.length+i));
    console.log(strFre)
    var isAnagram = Object.keys(patFre).every(function(item){
      return patFre[item] === strFre[item];
    });
    if (isAnagram){
      arr.push(i)
    }
  }
  return arr
}

anagram(str,pat)
```
