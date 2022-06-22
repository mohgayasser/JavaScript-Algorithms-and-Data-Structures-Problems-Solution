
# --description--

One of the simplest and most widely known <dfn>ciphers</dfn> is a <dfn>Caesar cipher</dfn>, also known as a <dfn>shift cipher</dfn>. In a shift cipher the meanings of the letters are shifted by some set amount.

A common modern use is the <a href="https://www.freecodecamp.org/news/how-to-code-the-caesar-cipher-an-introduction-to-basic-encryption-3bf77b4e19f7/" target="_blank" rel="noopener noreferrer nofollow">ROT13</a> cipher, where the values of the letters are shifted by 13 places. Thus `A ↔ N`, `B ↔ O` and so on.

Write a function which takes a <a href="https://www.freecodecamp.org/news/how-to-code-the-caesar-cipher-an-introduction-to-basic-encryption-3bf77b4e19f7/" target="_blank" rel="noopener noreferrer nofollow">ROT13</a> encoded string as input and returns a decoded string.

All letters will be uppercase. Do not transform any non-alphabetic character (i.e. spaces, punctuation), but do pass them on.


# --seed--

## --seed-contents--

```js
function rot13(str) {
  return str;
}

rot13("SERR PBQR PNZC");
```

# --solutions--
```js
function rot13(str) {
    let newStr = [...str].map((L, indx) => {
        if (L >= "A" && L <= "Z") {
            if ((str.charCodeAt(indx) + 13) > "Z".charCodeAt(0)) {
                let addval = (str.charCodeAt(indx) + 13) - "Z".charCodeAt(0);
                L = "A".charCodeAt(0) + addval - 1;
            } else {
                L = str.charCodeAt(indx) + 13;
            }
            return String.fromCodePoint(L);

        } else {
            return L;
        }
    })

    return newStr.join("");
}

```
