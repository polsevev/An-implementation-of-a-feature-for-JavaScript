# **8.0** Test262

This module will discuss the official testing suite for Ecma262 titled [Test262](https://github.com/tc39/test262). You will learn how to write tests for a proposal. 


# **8.1** Why a shared testing suite?

The goal of Test262 is to provide test material that covers every observable behavior specified in the ECMA-414 Standards Suite. It is the largest testing suite available for EcmaScript to date.

Using a shared testing suite has a lot of advantages. It allows the developers to see what engine is most compliant with the specification, what features are supported and what is currently unsupported. 

As stated in Module 4, test262 has a website where the compliance of each engine can be viewed. 

[Test262 compliance](https://test262.report/)


# **8.2** Writign tests for Test262

The official guidelines for contributing to Test262 state that an [acceptable test](https://github.com/tc39/test262/blob/main/CONTRIBUTING.md#acceptable-tests) is the following:

`Any test that exercises observable grammar or semantics, originating with citable, normative text in the latest draft of the ECMAScript Language Specification, the ECMAScript Internationalization API Specification, the The JSON Data Interchange Syntax, a Stage 3 proposal or a Pull Request which makes a normative change to any of those specifications.`


This states we can write tests for any observable grammar or semantic that originates from our specification (ECMAScript Language Specification). This is what we will be doing in this module. 

In order to fully test our implementation, we have to test every "testable" line in the specification. 

A "testable" line is when the behavior of the specification is observable to the user with a specific input. An example of a easily "testable" line in the specification is step 3:
```
3. If IsCallable(callbackfn) is false, throw a TypeError exception.
```

The test for this line of the specification should look something like this:
```js
assert.throws(TypeError, function() {
  [].group(null)
}, "null callback throws TypeError");
```

The `assert` object is part of the Test262 suite, in this usecase we assert that `[].group(null)` throws and error.

All the different functions on the assert object can be found in [CONTRIBUTING.md](https://github.com/tc39/test262/blob/main/CONTRIBUTING.md#test-environment) in the official test262 github repository. 

## **Task 8.2.1** What lines are testable?

View all lines in the specification of _Array grouping_ proposal. What parts of the specification are "testable"? 

Write down what lines are testable and compare them with the document provided [here](LINK TO Solution!)

# **8.3** Standard tests for all new functions

All new functions added to JavaScript have to use the correct properties. That means setting the following properties correctly: `length`, `name`. Each of these properties have accessor descriptors that has to be set correctly.

Examples of accessor descriptors which have to be set:

`Enumerable`: An enumerable property will show up in enumeration of the object. 

`Writable`: If true, the property can be changed with an assignment operator (=)

More about properties and their accessor descriptors can be found [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)

View the tests of the feature `Array.prototype.filter` to see an example of how these can be tested. 

# **Task 8.2.1** Writing some test

Your task is to write tests for 3-4 of the lines you specified in [task 8.2.1](#task-821-what-lines-are-testable).

The tests should ensure that both `groupBy` and `groupByToMap` adhere to the [specification](../../Specification/Specification_Array_Grouping.md)

When you have implemented your tests, compare them to the official tests in Test262 for this proposal. 

- The official tests for `groupBy` (now named `group`) can be found [here](https://github.com/tc39/test262/pull/3354)

- The official tests for `groupByToMap` (now named `groupToMap`) can be found [here](https://github.com/tc39/test262/pull/3353)

## [<--](../Module%207/Module7.md) [-->](../Module%209/Module9.md) 