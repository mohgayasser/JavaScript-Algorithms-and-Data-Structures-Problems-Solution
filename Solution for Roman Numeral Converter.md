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
function convertToRoman(num) {
    let Newnum="";
    let Rom=[
    ["M",1000],["CM",900],["D",500],["CD",400],["C",100],["XC",90],["L",50],["XL",40],["X",10],["IX",9],["V",5],["IV",4],["I",1]
    ]
 Rom.forEach(item=>{
    if(item[1]<=num){

    let val =(num/item[1])| 0;
    num-=(item[1]*val)
    Newnum+=item[0].repeat(val);

    }
 })
    return Newnum;
   }


```
