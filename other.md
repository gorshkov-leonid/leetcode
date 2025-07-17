5. Longest Palindromic Substring


Stupid
```js
var longestPalindrome = function(s) {
  if(!s.length){
    return null;
  }

  const n = s.length;
  for(let m = n; m > 1; m--){
	 for(let k = 0; k < n - m + 1; k++){
		if(isPalindrom(s, k, k + m - 1)){
            return s.slice(k, k+m);
        }
     }
  } 
  return  s.charAt(0);
};

function isPalindrom(s, a, b) {
  const n = Math.trunc((b - a + 1) / 2);
  for(let i = 0; i < n; i++){
     if(s.charAt(a + i) !== s.charAt(b - i)) {
		return false;
     }
  }    
  return true;
}


```
