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
