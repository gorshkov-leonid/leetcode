5. Longest Palindromic Substring


Stupid n^3
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

DP n^2
https://www.youtube.com/watch?v=UflHuQj6MVA
```js
var longestPalindrome = function(s) {

   const n = s.length;
   const M = new Array(n).fill(false).map(v => new Array(n).fill(false));
   let maxLength = 1;
   let start = 0;
   let end = 0;
   for(let j = 0; j < n; j++){
      M[j][j] = true;
      for(let i = 0; i < j; i++){
 		  if(j - i === 1) {
              M[i][j] = s.charAt(i) === s.charAt(j);
          } else {
              M[i][j] = M[i+1][j-1] && s.charAt(i) === s.charAt(j);
          }
		  const length = j - i + 1;
		  if(M[i][j] && (length > maxLength)){
		      maxLength = length;
			  start = i;
			  end = j;
		  }
      }
   }
   return s.slice(start, end + 1);
}
```
