Recall that the Greatest Common Divisor (GCD) of two integers A and B is the largest integer that divides both A and B. 
### The Euclidean Algorithm
```
function gcd(a,b){
  if ( !a || !b) {
    return !a ? b : a;
  }
  if (a > b){
    var newA = a%b;
   return gcd(newA, b)
  }
  var newB = b%a;
  return  gcd(a, newB)
}

gcd(1701,3768)
```
