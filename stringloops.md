# Intermediate String Loops

## Uncompress
Write a function that takes in a 'compressed' string as an arg. The function should return the uncompressed version of the string.

```javascript
function uncompress(str) {
    // Initialise an empty string to store the uncompressed result
    let newStr = '';

    // Iterate through the compressed string, incrementing by 2 to process pairs
    for (let i = 0; i < str.length; i += 2) {
        // get the character at the current position
        let char = str[i];

        // Get the numeric string representing the number of repititions
        let num = Number(str[i + 1]);

        // Use a nested loop to repeat the character the specified number of times
        for (let times = 0; times < num; times += 1) {
            // Append the character to the new string for every repitition
            newStr += char;
        }
    }
    // Return the uncompressed string
    return newStr;
};

console.log(uncompress('x3y4z2')); // 'xxxyyyyzz'
console.log(uncompress('a5b2c4z1')); // 'aaaaabbccccz'
console.log(uncompress('b1o2t1')); // 'boot'
```

## Triplet True
The function checks for the presence of triplets (three consecutive identical characters in the input string). It iterates through the string, compares each character with the next two characters, and returns and returns 'true' if a triplet is found. If no triplet is found after the loop, the function returns 'false'.

```javascript
let tripletTrue = function(str) {
    // Iterate through the characters of the string, stopping 2 characters before the end (to ensure there are enough characters to check for the triplet)
    for (let i = 0; i < str.length - 2; i++) {
        // Check if the current character and the next two characters are the same
        if (str[i] === str[i + 1] && str[i + 1] === str[i + 2]) {
            // If a triplet is found, return true and exit the function
            return true;
        }
    }
    // If no triplet is found after iterating through the string, return false
    return false;
}

console.log(tripletTrue('terrrrrible'));   // true
console.log(tripletTrue('runninggg'));     // true
console.log(tripletTrue('bootcamp'));      // false
```

## More Dot Less Dash
The function counts the number of dots and dashes in the input string and returns 'true' if there are more dots than dashes, and 'false; otherwise.

```javascript
function moreDotLessDash(str) {
    // Initialise counters for dots and dashes
    let dotCount = 0;
    let dashCount = 0;

    // Iterate through the characters of the string
    for (let i = 0; i < str.length; i++) {
        // Check if the current character is a dot
        if (str[i] === '.') {
            // Increment the dotCount if a dot is found
            dotCount++;
        } else if (str[i] === '-') {
            // Increment the dashCount if a dash is found
            dashCount++;
        }
    }
// Return true if there are more dots than dashes, otherwise return false
return dotCount > dashCount;
}

console.log(moreDotLessDash('.... . -.--'));                            // true
console.log(moreDotLessDash('.--. .-. --- --. .-. .- -- -- . .-.'));    // false
```

## Last Index
Searches for the last occurance of a specified character in the input string. It returns the index of the last occurance of the specified character.

```javascript
function lastIndex(str, char) {
    // Start iterating from the last character to the first
    for (let i = str.length - 1; i >= 0; i--) {
        // Check if the current character is equal to the specified character
        if (str[i] === char) {
            // Return the index of the last occurance of the character
            return i;
        }
    }
}

console.log(lastIndex("abca", "a"))        // 3
console.log(lastIndex("mississipi", "i"))  // 9
console.log(lastIndex("octagon", "o"))     // 5
```

## Caesar Cipher
implements a basic Caesar cipher by shifting each character in the input string by a specified number of positions in the alphabet. The resulting encrypted string is then returned.

```javascript
function caesarCipher (string, num) {
    // define the alphabet as a constant string
    const alphabet = "abcdefghijklmnopqrstuvwxyz";

    // Initialise an empty string to store the encrypted result
    let newString = "";

    // Iterate through each character in the input string
    for (let i = 0; i < string.length; i++) {
        // Get the current character
        let char = string[i];

        // Find the index of the current character in the alphabet
        let oldIdx = alphabet.indexOf(char);

        // Calculate the new index after shifting by the specified number
        let newIdx = oldIdx + num;

        // Handle wrapping around the alphabet (modulo operation)
        let newChar = alphabet[newIdz % alphabet.length];

        // Append the encrypted character to the new string
        newString += newChar;
    }
    // Return the encrypted string
    return newString;
}

console.log(caesarCipher("apple", 1)); // "bqqmf"
console.log(caesarCipher("bootcamp", 2)); // "dqqvecor"
console.log(caesarCipher("zebra", 4)); // "difve"
```
> If the new index goes beyond the end of the alphabet, it starts counting from the beginning again. this is essential to handle cases where shifting by the specified number of moves beyond the end of the alphabet, allowing the Caesar cipher to "wrap around" and continue from the beginning.
