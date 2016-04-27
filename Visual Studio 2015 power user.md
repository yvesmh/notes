Visual Studio 2015 power user

Folders and Subfolders

Solution -> Project(s) -> bin

Use Defaults

Experienced developers know where everything is kept
Visual Studio will help you find anything
Visual Studio lets you change almost everything, but sticking to the usual defaults makes life simpler for the rest of your team.

Inside the files

Nothing is hardcoded
You edit with Visual Studio, changes go into the .sln and .proj files
Other tools can read the same files (like MSBuild or Blend)

Architecture

Design your solution first
Think about references.
Get the structure in place before the code

Toolbars

Over thirty Visual Studio toolbars
They appear depending on the context
Can turn on more toolbars
Can add commands
Menus remind toolbar symbol, keyboard shortcut
Toolbars remind name, keyboard shortcut


— — — 
EXPLORING RELATIONSHIPS IN CODE

Class View

* Looks at your code as classes
* See inheritance hierarchies
* See methods, properties, etc
* Easy to navigate to code
* View is customizable
* Can even do some code changes

Seeing code your code calls

Go to definition
Peek

Call hierarchy, find all references

Call hierarchy - Who calls this function?
Find all references

Back and Forward

Navigate back and forward just like a browser
Will even scroll you if you’re within the same file
Bookmarks, use Bookmarks window and give them names

Enhanced Scrollbar

* Blue - current line
* Green - recent changes
* Yellow - unsaved changes
* Orange - find results
* Dark red - breakpoints
* Black - bookmarks
* Red - Error and warnings

Tools -> options -> Text Editor -> C# -> scroll bars -> Show annotations over vertical scroll bar to enable/disable. Map Mode for sublime text-like navigation.

— — — — 

USING SEARCH AND FIND EFFECTIVELY

* Find dialog
* Scope, case, whole word
* F3 to go to next occurrence
* Shift+F3 to go back to previous occurrence
* Crl+F3 - select a string and search for this string
* Find in files - search across multiple files
* Navigate to -> knows about symbols

Navigate to - using spaces treats it as AND

Searching in Tool Windows

Filter tool windows to show selected entries
Searches the content the window normally shows
Many tool windows have a search box

Available in:
* solution explorer
* toolbox
* etc

Output and Errors

Error view is a grid
Output view is more of a “stream of consciousness”


— — — — — 
LETTING VISUAL STUDIO HELP YOU

Visual Studio Will Fix Your Errors

Visual Studio knows when to add “usings”

Snippets
Really worth discovering
Common pieces of the language you use regularly
And especially those you don’t use often
Very considerate
Tab key navigates between snippet fields

To discover snippets:
Right click -> Insert Snippet -> C#

Work with IntelliSense

Not getting suggestions means something is wrong
Add the reference before trying to use it
Declare functions and variables early
Stay in flow and type as little as possible

Refactoring
Move blocks of code into functions
Generate properties from variables, variables from expressions, and back again
Surround blocks of code with tests or loops

Select text -> surround with -> (if, for, etc)
Select text -> quick actions -> extract into method

Fix indentation:
Edit -> Advanced -> Format Document or Ctrl+E, D
Formats the file with the options set in Tools -> Options -> Text Editor -> C# -> Tabs

Move to local variable:
Ctrl+. -> Introduce local variable x 
To undo: select variable -> ctrl+. -> Inline temporary variable

Help
Visual Studio has help
It’s actually pretty good
Online and Offline
Samples Gallery
Search Options and other tools
Quick Launch helps find commands. Really makes a big difference.

Pressing F1 on the current cursor makes a contextual search on either msdn or bing.

Quick launch located at top right - kinda like Ctrl+shift-P in Sublime Text

— — — — — 
BASIC DEBUGGING FEATURES

Build configurations
Gathering of settings related to building your project
Debug and Release are automatically created

If build configuration not available: Tools -> Options -> Projects and Solutions -> Check “show advanced build configuration”

Where are the files?

bin/Debug and bin/Release
Can run exe from those folders
Can copy files for a deployment

Important Concepts
Breakpoint - when code reaches this line, stop
Call stack - how you got to where you are
Step over - execute one line and pause again. if it is a function, it runs it without stepping into it
Step into - steps into a function
Step out - steps out of a function until after the call was done
Continue - keep running (until next breakpoint)


Keyboard shortcut: Toggle breakpoint - F9

Locals window shows the values of variables within scope
Call stack window shows.

— — — — — — 
ADDITIONAL DEBUGGING FEATURES

Data Tips, Visualizers and Watchers
Hover over a variable to see its value
Pin a tip
Autos and Locals
Watches - allows you to just look at a handful of expressions of interest to you

Autos window - like locals but shows less: shows variables that were involved in the previous line as well as anything in the line about to run. More focused

When you hover over a variable and start to go deep into the properties (for classes like DateTime or DataTable etc), press and hold ctrl to make the tooltip window more transparent. let go to bring it back

More complicated values

Quickwatch
Command Window
Immediate Window

Immediate window
prepend with “?” to get values of expression
If not available, Debug -> Windows -> Immediate

Command Window
Issue commands to Visual Studio
* ?? - brings up quickwatch
* of - opens file

Start typing to get autocomplete suggestions

Don’t Break Too soon or Step too much

Run without pausing to narrow in on the problem
Use conditional breakpoints
Use tracepoint - like breakpoint but doesn’t break

Conditional breakpoints
Hover over breakpoint, click on settings to bring UI -> Check conditions -> Conditional expression

Tracepoint
Hover over breakpoint, click on settings -> Check Actions -> 

Beyond “Step Over”
Run to Cursor - alternative to setting a temporary breakpoint to get to a line while debugging
Set Next Statement 
Change a value
Change your code

Run to cursor (Ctrl+F10)
When debugging, right click on a line -> Run to Cursor 

Set Next Statement
Skips through lines

— — — — 
WORKING WITH DESIGNERS

Building User Interfaces in Visual Studio
Different UIs for Windows, Web, Phones, Plugins

Fundamentals
Toolbox window has all kinds of controls
Edit handlers
Edit designer code

Change the name before adding handlers because it can be painful to change later

Properties
Type values for properties with more precision than drag-drop and mouse manipulation

double-clicking a boolean property toggles the value

Look for:
* Smart tags
* … button in Properties

— — — — — 
USEFUL EXTENSIONS

Extensibility
Code can change Visual Studio behavior
Any and all parts of the UI
New tool windows and dialogs
Easy install

Visual Studio Gallery
http://visualstudiogallery.com
* Browse, filter, search
* Many can be installed right from the page
* Read reviews, Q&A, etc

Tools-> Extensions and updates -> Online

* Spell Checker
    * Checks in strings, identifiers.
* VSColorOutput
    * Adds color to the output window
    * Easier to find errors and warnings
    * Can customize with regular expressions
* Productivity Power tools
    * Dozens of extensions gathered together
    * Some highlights:
        * Peek help
        * Block highlighting
        * Double click maximize
        * Ctrl+click peek (or go to definition)
    * Showcase for possible new Visual Studio Features

Tabs of different colors depending on project they’re in.
Add “customize” to tab dropdown

Block structure highlighting follows a bracket from start to finish. Mousing over the line shows what started the block.

Peek help (Ctrl + F1) displays a small embedded browser.

Shows red underline for files, projects, solutions that aren’t compiling

Press ctrl + click on a method or symbol to “go to” definition or peek. Change between “go to” and “peek” tools -> options -> productivity power tools -> other extensions -> 

Tools -> options -> Productivity Power Tools -> PowerCommands:
* Format documents on save
* Remove and sort “usings” on save



Other Kinds of Extensions

New Snippets for particular styles or platforms
New project types
New languages

Controlling Extensions

Extensions that were deployed with VSIX can be enabled/re-enabled

If they were installed with exe or msi, can be uninstalled via regular “uninstall program”

File location - delete it from magical location

— — — — — 
IntelliTrace and Code Maps

IntelliTrace Basics
One of the reasons people pay for “Enterprise”
Saves a trace file
Low performance impact

IntelliTrace for Time Travel
Start by debugging
Run past the problem
Break the program
Move back and forth in time

If you get “no source available”  do a “Step into”

IntelliTrace Between Computers

Save a trace file
Developer uses the trace file.
Helps fix “works on my machine” bugs

Code Map
Also only available on Enterprise Edition
Builds diagram as you debug
Can tweak and annotate
Share

You need to add breakpoints for CodeMap to work.