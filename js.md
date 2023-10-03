# Javascript cheatsheets

## Value

- Number
- String
- Boolean
- Null
- Undefined
- Symbol
- BigInt

### Number

- Positive
- Negative
- Integer
- Decimal

#### NaN

- Not a number
- `0/0 = NaN`
- `1 + NaN = NaN`

#### Infinity

- `1/0`
- `-1/0`
- `-0`

#### Number object function

- `parseInt('')`
  - `parseInt('20days')` -> `20`
  - `parseInt('$20')` -> `NaN`
- `parseFloat('')`
  - `parseFloat('$15.20')` -> `'NaN`

### String

- String immutable

#### String Method

- `str.toUpperCase()`
  - Return uppercase letter
- `str.toLowerCase()`
  - Return lowercase letter
- `str.trim()`
  - Return removed leading & whitespace
- `str.indexOf('')`
  - Find exact string
  - Return index number
  - Return `-1` not found
  - Case sensitive
- `str.slice(start idx, [last idx])`
  - Return from start index
  - If had last index, return from start to last index
- `str.replace('to_replace', 'what_to_replace)`
  - Find first occurrence
  - Replace word, and return new string
  - With replaced word
- `str.split([" "], [Number])`
  - Empty args, return one string in one array
  - First argument, thing we want to remove
  - For example space `(" ")`
  - Each word will become one item in array
  - `'hello world'.split(' ')` -> `['hello', 'world']`
  - Second args is how many item we want to return
  - `'hello world good morning'.split(' ', 2)` -> `['hello', 'world']`
- `str.join([' '])`
  - Empty args, default delimiter is `,`
  - Convert array to string
  - Each word will have delimiter
  - Can set delimiter to any character
  - Return new string

#### String Escape Character

- `\n` new line
- `\'` single quote
- `\"` double quote
- `\\` backslash
- `\t` tab

#### String Template Literal

- `` `${expression/variable/anything dynamic}`   ``

### Boolean

#### Double Equal comparison

- `==` `!=`
- Convert same type and compare
- Unexpected result `0 == null` return true
- Both falsy value

#### Triple Equal Comparison

- `===` `!==`
- Compare value and type
- Precise and specific

### Null & Undefined

- `let i = null` -> Null
- `let i; -> Undefined`

## Variable

- `let` mutable
  - Record
  - Update
- `const` immutable
  - Variable value cannot change
- `const array/object`
  - Reference immutable
  - Item/property mutatable

## Math Object

- `Math.PI`
  - Return PI number
- `Math.round(num)`
  - Return int rounded number
- `Math.abs(num)`
  - Return absolute number (always positive)
- `Math.pow(num, power)`
  - Power is how many time multiple by it self
  - `Math.(5, 3)` -> `125`
- `Math.floor()`
  - Remove decimal
  - `Math.floor(1.88)` -> `1`
- `Math.random()`
  - `Math.floor(Math.random() * number) + 1` -> range from 1 to number

## Operator

### Typeof

- `typeof variableName/expresssion`
- Note: `typeof null` return object (js bug)

### Boolean Operator

- All comparison: true/false
- `>`
- `<`
- `>=`
- `<=`
- `==`
- `!=`
- `===`
- `!==`

### Logical Operator

- `&&` both truthy
- `||` atleat one truthy
  - `0 === undefined` both falsy -> false
- `!` reverse expression
  - `!null` -> true

### Operator Precedence

- `()` wil trump everything
- `!` higher than `&&` and `||`
- `&&` higher than `||`

## Condition Statement

### If Statement

- `if (expession)` -> if true run if statement
- `else if(expression)` -> else if condition true run else if statement
- `else` expression false, run else statement

#### Nesting Condition

- Nest as much as you want

```js
if (expression) {
  if (expression) {
    // statement
  } else {
    // statement
  }
} else {
  // statement
}
```

### Switch Stamentement

- Expected output

```js
let day = 3;
switch (day) {
  case 1:
  case 2:
  case 3:
  case 4:
  case 5:
    console.log("Work Day");
    break;
  case 6:
  case 7:
    console.log("Public Holiday");
    break;
  default:
    console.log("Invalid days");
}
```

- If one case true, break.
- If not, it wil run all statement after true

### Ternary Operator

- If else turn into single code

```js
let lang = "Js";

let preference = lang === "Js" ? "Web Dev" : "Data Scientist";
```

### Truthy & Falsy Expression

- All number truthy except, `0` is falsy
- String is truth, empty sting `('')` is falsy
- `NaN` and `Undefined` and `0/0` is falsy

## Array

### Create Array

- const arrName = []

```js
const string = ['hello', 'world'];
const integer = [1, 3, 4];
const float = [32.2 2.3];
const bool = [true, false, true]
const collection = [[1, 3, 4], 'hello', true, NaN]
```

### Array Indices

- `const arrary[index number]`
- `.length` property

### Modify Array

- `const arr[index] = newValue`

```js
const buy = ["milk", "chicken"];
const buy[0] = 'banana';
const but[buy.length] = 'cheese'; // append to end
```

### Array Method

- `arr.pop()`
  - return deleted item
- `arr.push(...item)`
  - return int length
- `arr.shift()`
  - return deleted item
- `arr.unshift(...item)`
  - return int length
- `arr1.concat(...arr2)`
  - return new array
- `arr.includes(item, [idx])`
  - return boolean
- `arr.indexOf(item, [idx])`
  - return number of index
  - return `-1` if not found
- `arr.reverse()`
  - Modified original array
  - return reversed array
- `arr.join('separator')`
  - Default saperator `,`
  - Return string with separator
- `arr.slice(startIdx, beforeEndIdx)`
  - Return new sliced index
  - `arr.slice(idx)`
    - Return idx to end
  - `arr.slice(-1)`
    - Return last index
    - if `(-3)` return last 3 index
  - `arr.slice()`
    - Copy entire array
