
# --description--

Design a cash register drawer function `checkCashRegister()` that accepts purchase price as the first argument (`price`), payment as the second argument (`cash`), and cash-in-drawer (`cid`) as the third argument.

`cid` is a 2D array listing available currency.

The `checkCashRegister()` function should always return an object with a `status` key and a `change` key.

Return `{status: "INSUFFICIENT_FUNDS", change: []}` if cash-in-drawer is less than the change due, or if you cannot return the exact change.

Return `{status: "CLOSED", change: [...]}` with cash-in-drawer as the value for the key `change` if it is equal to the change due.

Otherwise, return `{status: "OPEN", change: [...]}`, with the change due in coins and bills, sorted in highest to lowest order, as the value of the `change` key.

<table class='table table-striped'><tbody><tr><th>Currency Unit</th><th>Amount</th></tr><tr><td>Penny</td><td>$0.01 (PENNY)</td></tr><tr><td>Nickel</td><td>$0.05 (NICKEL)</td></tr><tr><td>Dime</td><td>$0.1 (DIME)</td></tr><tr><td>Quarter</td><td>$0.25 (QUARTER)</td></tr><tr><td>Dollar</td><td>$1 (ONE)</td></tr><tr><td>Five Dollars</td><td>$5 (FIVE)</td></tr><tr><td>Ten Dollars</td><td>$10 (TEN)</td></tr><tr><td>Twenty Dollars</td><td>$20 (TWENTY)</td></tr><tr><td>One-hundred Dollars</td><td>$100 (ONE HUNDRED)</td></tr></tbody></table>

See below for an example of a cash-in-drawer array:

```js
[
  ["PENNY", 1.01],
  ["NICKEL", 2.05],
  ["DIME", 3.1],
  ["QUARTER", 4.25],
  ["ONE", 90],
  ["FIVE", 55],
  ["TEN", 20],
  ["TWENTY", 60],
  ["ONE HUNDRED", 100]
]
```

# --seed--

## --seed-contents--

```js
function checkCashRegister(price, cash, cid) {
  let change;
  return change;
}

checkCashRegister(19.5, 20, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]);
```

# --solutions--

```js
function float2int (value) {
    return value | 0;
}
function checkCashRegister(price, cash, cid) {
    let currancy = {
        "penny": 0.01,
        "nickel": 0.05,
        "dime": 0.1,
        "quarter": 0.25,
        "one": 1,
        "five": 5,
        "ten": 10,
        "twenty": 20,
        "one hundred": 100
    }
    let change=cash-price;
let addedVal=0;
    let changeObj=[];
    let countofcacher=0;
    let status;
    cid=cid.reverse();
    cid.forEach(item => {
        countofcacher+=item[1];
        if((currancy[item[0].toLowerCase()] <change)&&item[1]!=0){
            let curancycount=item[1]/(currancy[item[0].toLowerCase()]);
            let changecount=change/(currancy[item[0].toLowerCase()]);
         
            
         if(curancycount<=changecount){
changeObj.push([item[0],item[1]]);
change-=item[1];
change=change.toFixed(2);
addedVal+=item[1];
         }else {
let val=(currancy[item[0].toLowerCase()])*(float2int(changecount));
change-=val;
change=change.toFixed(2);
addedVal+=val;
changeObj.push([item[0],val]);
         }
        }else  {
            if(item[1]==0)  changeObj.push([item[0],0]);
        }
    
    });
    if(addedVal<(cash-price)){
status="INSUFFICIENT_FUNDS";
changeObj=[];
    }
    else {
        if(countofcacher>(cash-price)){
            status="OPEN";
        }else if (countofcacher==(cash-price)) {
status="CLOSED";
        }
    }
    changeObj=changeObj.reverse();
    changeObj.sort(function(a,b){
        return b[1]-a[1]
      })
    return { status: status, change: changeObj };
}
```
