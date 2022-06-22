---

title: Roman Numeral Converter
---


# --description--

Convert the given number into a roman numeral.

| Roman numerals | Arabic numerals |
|----------------|-----------------|
| M              | 1000            |
| CM             | 900             |
| D              | 500             |
| CD             | 400             |
| C              | 100             |
| XC             | 90              |
| L              | 50              |
| XL             | 40              |
| X              | 10              |
| IX             | 9               |
| V              | 5               |
| IV             | 4               |
| I              | 1               |

All roman numerals answers should be provided in upper-case.

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
