
# --description--

Return `true` if the given string is a palindrome. Otherwise, return `false`.

A <dfn>palindrome</dfn> is a word or sentence that's spelled the same way both forward and backward, ignoring punctuation, case, and spacing.

**Note:** You'll need to remove **all non-alphanumeric characters** (punctuation, spaces and symbols) and turn everything into the same case (lower or upper case) in order to check for palindromes.

We'll pass strings with varying formats, such as `racecar`, `RaceCar`, and `race CAR` among others.

We'll also pass strings with special symbols, such as `2A3*3a2`, `2A3 3a2`, and `2_A3*3#A2`.

# --seed--

## --seed-contents--

```js
function palindrome(str) {
  return true;
}

palindrome("eye");
```

# --solutions--

```js
function palindrome(str) {
  let newStr="";
  let j=0;
  for (let i=0;i<str.length;i++){
if((str.charAt(i)>='a' && str.charAt(i)<='z')||(str.charAt(i)>="A"&&str.charAt(i)<="Z" )||(str.charAt(i)>='0'&&str.charAt(i)<='9')){
newStr+=str.charAt(i).toLowerCase();
}
 }
  let l=0,r=newStr.length-1;
while (l<r) {
  if(newStr.charAt(l)!==newStr.charAt(r)) return false;
  else {
    l++;
    r--;
  }
}
 
  return true;
}
```
