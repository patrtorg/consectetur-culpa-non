# @patrtorg/consectetur-culpa-non

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![Build](https://github.com/patrtorg/consectetur-culpa-non/workflows/Npm%20deploy/badge.svg)
![Version](https://img.shields.io/npm/v/@patrtorg/consectetur-culpa-non.svg)
[![Known Vulnerabilities](https://snyk.io/test/npm/@patrtorg/consectetur-culpa-non/badge.svg)](https://snyk.io/test/npm/@patrtorg/consectetur-culpa-non)
![GitHub last commit (branch)](https://img.shields.io/github/last-commit/cosimochellini/@patrtorg/consectetur-culpa-non)
![npm](https://img.shields.io/npm/dw/@patrtorg/consectetur-culpa-non)
![npm total](https://img.shields.io/npm/dt/@patrtorg/consectetur-culpa-non.svg)
[![codecov](https://codecov.io/gh/cosimochellini/@patrtorg/consectetur-culpa-non/branch/master/graph/badge.svg)](https://codecov.io/gh/cosimochellini/@patrtorg/consectetur-culpa-non)

## Blazing fast, tree-shakeable, type-safe, modern utility library to sort any type of array

## Docs : https://@patrtorg/consectetur-culpa-non.netlify.com/

# Getting started

## installation

The library is available as a [npm package](https://www.npmjs.com/package/@patrtorg/consectetur-culpa-non).
To install the package, run:

```
npm install @patrtorg/consectetur-culpa-non
# or
yarn add @patrtorg/consectetur-culpa-non
```

Start using:

```typescript
import {byString} from '@patrtorg/consectetur-culpa-non'

const unsorted = ["xxx", "bbbb", "zzz", "cccc", "aaa"];
const sorted = unsorted.sort(byString());

console.log(sorted); //(5) ["aaa", "bbbb", "cccc", "xxx", "zzz"]
```

Use directly in the browser

```html

<script src='https://cdn.jsdelivr.net/npm/@patrtorg/consectetur-culpa-non/dist/index.umd.js'></script>
<script>
  const unsorted = ["xxx", "bbbb", "zzz", "cccc", "aaa"];
  const sorted = unsorted.sort(sort.byString());

  console.log(sorted); //(5) ["aaa", "bbbb", "cccc", "xxx", "zzz"]
</script>

//or via browser modules

<script type='module'>
  import {byString} from 'https://cdn.jsdelivr.net/npm/@patrtorg/consectetur-culpa-non/dist/index.mjs'

  const unsorted = ["xxx", "bbbb", "zzz", "cccc", "aaa"];
  const sorted = unsorted.sort(byString());

  console.log(sorted); //(5) ["aaa", "bbbb", "cccc", "xxx", "zzz"]
</script>
```

## Some mind-blowing example

**sort by a single property**

```typescript
//js or ts file
import {byValue, byNumber, byString} from '@patrtorg/consectetur-culpa-non'

const arrayUnsorted = [
  {prop: "xxx", foo: 34},
  {prop: "aaa", foo: 325},
  {prop: "zzz", foo: 15},
  {prop: "ccc", foo: 340},
  {prop: "bbb", foo: 0}
];

//this sort by the foo property ascending
const sortedByFoo = arrayUnsorted.sort(byValue((i) => i.foo, byNumber()));
console.log(sortedByFoo); //(5) [{prop: "bbb", foo : 0}, {prop: "zzz", foo: 15}, .....];

//this sort by the prop property descending
const sortedByProp = arrayUnsorted.sort(byValue((i) => i.prop, byString({desc: true})));
console.log(sortedByProp); //(5) [{prop: "zzz", foo : 15}, {prop: "xxx", foo: 34}, .....];
```

**sort by a multiple property**

```javascript
//js or ts file
import {byNumber, byString, byValues} from "@patrtorg/consectetur-culpa-non";

const objsToSort = [
  {id: 2, name: 'teresa'},
  {id: 3, name: 'roberto'},
  {id: 2, name: 'roberto'}
];

//i sort by THEIR NAMES and THEN by their ids
const sortedObject = objsToSort.sort(byValues([
  [(x) => x.name, byString()],
  [(x) => x.id, byNumber()]
]));

console.log(sortedObject); //[{roberto, 2}, {roberto, 3}, {teresa, 2}];

//i sort by THEIR IDS and THEN by their names
const sortedObject2 = objsToSort.sort(byValues([
  [(x) => x.id, byNumber()],
  [(x) => x.name, byString()]
]));
console.log(sortedObject2); //[{roberto, 2}, {teresa, 2}, {roberto, 3}];

//i sort by THEIR IDS and THEN by their names DESCENDING
const sortedObject3 = objsToSort.sort(byValues([
  [(x) => x.id, byNumber()],
  [(x) => x.name, byString({desc: true})],
]));
console.log(sortedObject3); //[{teresa, 2}, {roberto, 2}, {roberto, 3}];

```

**typescript types check**

```typescript
//ts file
import {byValue, byNumber, byString} from '@patrtorg/consectetur-culpa-non'

const objsArray = [{numbProp: 2, stringProp: 'a'}, {numbProp: 3, stringProp: 'f'}];

//Incorrect sort property 
const incorrectSortedArray = objsArray.sort(byValue(i => i.numbProp, byString()));
//ts check error : Type 'number' is not assignable to type 'string'.

//Correct sort type
const sortedArray = objsArray.sort(byValue(i => i.numbProp, byNumber()))
//ts check ok

```

## See full Docs

### [**@patrtorg/consectetur-culpa-non.netlify.com**](https://@patrtorg/consectetur-culpa-non.netlify.com)

# License

MIT © Cosimo chellini
