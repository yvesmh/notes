# Devensive Coding in C#

## Introduction

### What is Defensive Coding?

...an approach to improve software and source code, in terms of:

* General *Quality* - Reducing the number of software bugs and problems
* Making the source code *comprehensible* - the source code should be readable and understandable so it is approved in a code audit.
* Making the software behave in a *predictable* manner despite unexpected inputs or user actions

#### Quality

Automated code testing

#### Comprehensible

If another developer doesn't understand your intent, they make make incorrect assumptions about the code and make inappropiate code changes.

Comprehensible code requires less time to change.

Build clean code

Refactor to make code easier to understand

#### Predictable

Validation + Exception Handling

### Clean Code

* Improves Comprehension
* Simplifies Maintenance
* Reduces Bugs

Bad code vs Bad Code

Write good code following clean coding techniques

Transform bad code to good code when possible through refactoring

Clean code is:
* Easy to read (for others and future you)
* Clear intent
* Simple - if it is too complex or too "elegant" can be hard to change
* Minimal - each part of the code does one thing and does that thing well, dependencies between code are kept to a minimal.
* Thoughtful - Code location is carefully considered.

### Testable Code and Unit Tests

* Improves Quality
* Confirms Maintenance
* Reduces Bugs

Not only unit tests, but also integration tests

Automated code testing makes it easier to test new code without having to run the whole application and all the steps to get there.

### Predictable Code

* Improves Predictability
* More consistent
* Reduces bugs

Anticipating failure.

Recover from failure

Should the code trust the data it's given?

*Each non-private method that you write is a contract*

Contract:
* Parameters
* Return Type
* Exceptions

Verify:
* Parameters
* Data
* Return Type
* Exceptions

## Defending Your Methods - Part 1

### Clean, Testable and Preditable Methods

**Clear purpose** - should do one thing and do it well, easier to understand, easier to debug and modify without introducing new bugs. Tests are easier to write because they are focused. 

**Good Name** - should clearly identify the purpose, has clear intent on when and why it should be used

**Focused Code** - All of it should be focused on the single purpose, minimizing the need for extensive comments, should not have side effects such as modifying global data, modifying incoming parameters or calling unrelated methods.

**Short Length** - Code that is long suggest method does not have a single purpose

**Testable** - You should be able to call the method from an automated code test.

**Predictable Result** -  The code should not react strangely when provided invalid information or if an unforeseen condition occurs.

A method should do what the name says, and nothing more.

Length matters because you should be able to tell at a glance what a method does.

"Code-behind" is really hard to test

A **Class library** is the best place to put non-UI logic, makes it reusable across different UIs, easier to test in automated tests.

The **Repository Pattern** includes a specific set of classes that handle the data access for the application

## Defending Your Methods - Part 2

### Validating Method Parameters

The first step in making a method predictable, is to check parameters and only allow valid input.

Guard clauses check the value of all incoming parameters, regardless of where the value comes from.

Minimize number of parameters

Consistent parameter ordering:
* From most important to least important. 
* Flags are normally last

Fail Fast technique causes code to fail immediately when it receives something invalid

