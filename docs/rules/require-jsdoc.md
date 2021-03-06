---
title: require-jsdoc - Rules
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# require JSDoc comments (require-jsdoc)

[JSDoc](http://usejsdoc.org) is a JavaScript API documentation generator. It uses specially-formatted comments inside of code to generate API documentation automatically. For example, this is what a JSDoc comment looks like for a function:

```js
/**
 * Adds two numbers together.
 * @param {int} num1 The first number.
 * @param {int} num2 The second number.
 * @returns {int} The sum of the two numbers.
 */
function sum(num1, num2) {
    return num1 + num2;
}
```

Some style guides require JSDoc comments for all functions as a way of explaining function behavior.

## Rule Details

This rule requires JSDoc comments for specified nodes. Supported nodes:

* `"FunctionDeclaration"`
* `"ClassDeclaration"`
* `"MethodDefinition"`

## Options

This rule has a single object option:

* `"require"` requires JSDoc comments for the specified nodes

Default option settings are:

```json
{
    "require-jsdoc": ["error", {
        "require": {
            "FunctionDeclaration": true,
            "MethodDefinition": false,
            "ClassDeclaration": false
        }
    }]
}
```

### require

Examples of **incorrect** code for this rule with the `{ "require": { "FunctionDeclaration": true, "MethodDefinition": true, "ClassDeclaration": true } }` option:

```js
/*eslint "require-jsdoc": ["error", {
    "require": {
        "FunctionDeclaration": true,
        "MethodDefinition": true,
        "ClassDeclaration": true
    }
}]*/

function foo() {
    return 10;
}

class Test{
    getDate(){}
}
```

Examples of **correct** code for this rule with the `{ "require": { "FunctionDeclaration": true, "MethodDefinition": true, "ClassDeclaration": true } }` option:

```js
/*eslint "require-jsdoc": ["error", {
    "require": {
        "FunctionDeclaration": true,
        "MethodDefinition": true,
        "ClassDeclaration": true
    }
}]*/

/**
 * It returns 10
 */
function foo() {
    return 10;
}

/**
 * It returns 10
 */
var foo = function() {
    return 10;
}

var array = [1,2,3];
array.filter(function(item) {
    return item > 2;
});

/**
 * It returns 10
 */
class Test{
    /**
    * returns the date
    */
    getDate(){}
}
```

## When Not To Use It

If you do not require JSDoc for your functions, then you can leave this rule off.

## Related Rules

* [valid-jsdoc](valid-jsdoc)

## Version

This rule was introduced in ESLint 1.4.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/require-jsdoc.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/require-jsdoc.md)
