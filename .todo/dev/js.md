
# Focus

Check if element is visible in DOM

https://stackoverflow.com/questions/19669786/check-if-element-is-visible-in-dom


console.log(...)
console.dir(...)
console.table(...)

parseFloat vs Number

    parseFloat('3.23abc'); //=> 3.23
    Number('3.23abc'); //=> NaN
    In both conversions, the input string is trimmed, by the way:

    parseFloat('  3.23abc '); //=> 3.23
    Number('   3.23 '); //=> 3.23