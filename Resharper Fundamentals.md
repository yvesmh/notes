# Resharper Fundamentals

# INTRODUCTION

## Resharper Features
* Code browsing
* Code clean-up
* refactoring
* code assistance
* micro code generation and templating
* grab bag of other useful features

## Learning Tips
* Keep the keymap under your keyboard
* Focus on a few commands at a time
* Don’t be afraid to try a new shortcut
* Keep your hands on the keyboard ( look if there is a shortcut when you want to use the mouse)
* Watch other developers use ReSharper


# CODE BROWSING

## Cheat Sheet

Resharper navigate - 
…

## Moving Between Files

* Go to type - Ctrl-N - Ctrl - T
* Go to File — Ctrl-Shift-N — Ctrl-Shift-T
* Recent Files — Ctrl-E — Ctrl-,
* Related Files — Ctrl-Alt-Shift-G — Ctrl-Alt-F7 

## Moving Within Files

Next/Previous Member — Alt-up/down
Go to file member — Ctrl+F12 — Alt-\
Go to containing declaration — Ctrl-[ —

## Navigating Inheritance

* Go to Derived
* Go to implementation
* Go to Base
* View type hierarchy 

## Navigating Code

* Go to declaration
* Go to type of symbol

## Navigating Usages

* Find Usages
* Highlight Usages
* Next/Previous Usage

## Bookmarks

* Set/Remove Bookmark — Ctrl-Shift-[0-9]
* Go to bookmark — ctrl-[0-9]
* View bookmarks — Ctrl-`

## Search for a symbol

Go to Symbol — Ctrl-Alt-Shift-N — Alt-Shift-T

## Advanced Code Understanding

Inspect This — Ctrl-Alt-Shift-A

# Code Cleanup

## Cheat sheet

* Quick Fix — Ctrl-N — Ctrl-T
* Next highlight
* Previous highlight


## Moving Code Around

* Move Code up/down
* View File Structure

## Formatting Code

* Code Cleanup — 
* Silent Code Cleanup

## Remove Unused Code

* Remove unused code (quick-fix)
* Safe Delete


# REFACTORING

## Cheat Sheet

Refactor this — ctrl-shift-r 
Extend selection — ctrl-w — ctrl-alt-right
Shrink selection — ctrl-shift-w — ctrl-alt-left

## Renames

Rename — F2 or Shift-f6 — ctrl-r, r 

## Variables & Fields

* Introducte Variable
* Introduce Field
* Inline variable/field

## Extracting methods

* Extract Method
* Inline Method
* Inline parameter

## Moves

* Move Static Method

## Static & Instance Methods

* Make Static
* Make Non-Static
* Static -> Extension Method
* Extension method -> Static

(all through refactor this — ctrl-shift-r)

## Refactoring Method Parameters

* Change Signature
* Extract Class from Parameters

## Refactoring a Method to Another Construct  

* Method <-> Property
* Method <-> Indexer

## Refactoring with Properties

* Encapsulate Field
* Property <-> Autoproperty

## Inheritance & Interfaces

* Extract Superclass
* Extract Interface
* Interface <-> Abstract class
* Use Base Type where possible

## Moving members in an inheritance hierarchy

* Pull member up -> move it up in the inheritance hierarchy

## Types

* Copy Type
* Constructor to Factory Method
* Anonymous -> Named Type

## Cleaning Up a Type

* Move to another file
* Move to folder
* Move type to another namespace

## Improved Intellisense

* Symbol code completion
* Smart code completion
* Import symbol completion

Offers code completion for classes that don't exist yet but have used methods locally, good for Test Driven Development

Activate Smart Code Completion with Ctrl-Alt-Space (VS) or Ctrl-Shift-Space (IDEA)

Import Symbol Completion with Ctrl-Shift-Space (VS) or Ctrl-Alt-Space (IDEA)

## Usings & References

* Add Using
* Add Reference

To add reference, it must be one already being used in another project, or a reference to another project in the solution

## Quicker Coding

* Coding backwards
* Complete statement
* Quick fixes

Extract Variable with Ctrl-R,v (VS):

```
new List<string>();
//press ctrl_r,v and resharper adds "var list = "
```

Use statement completion (Ctrl-Shift-Enter) to open and close curly braces and place the cursor between them

## Duplicating & Commenting

* Duplicate line/selection - Ctrl-D
* Comment Line - Ctrl-Alt-/
* Comment Block - Ctrl-Shift-/

Commenting a line brings the cursor to the next line so it's easy to comment one by one.

## Quick Documentation

* Parameter Info - Ctr-Shift-Space
* Quick docs - Ctrl-Shift-F1

## Surrounding

* Remove Braces - Alt-Enter
* Surround with - Ctrl-E,U 

## Moving Code Around

* Split Declaration & Assignment - Alt-Enter
* Move to outer scope - Alt-enter

* Clipboard Ring - only on IDEA Scheme (Ctrl-Shift-V)
* Move Code Up/Down - Ctrl-Alt-Shift-(up/down)
* Move code In/Out - Ctrl-Alft-Shift-(Left/Right)

## Code Analysis

* Parameter Analysis
* Solution wide analysis

