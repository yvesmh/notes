Winforms best practices

FlowLayoutPanel for responsive labels
——
Keyboard Navigation
Tab Order with Control.TabIndex and Control.TabStop


Mnemonics: “&Play” Add the & in the Text property.
Form.AcceptButton, Form.CancelButton
override Form.ProcessCmdKey
button.PerformClick() (may introduce bugs)

Menus
MenuItem.ShortcutKeys

——
Familiarity

Use standard controls and dialogs if possible

—
Detect first run with app settings

——
Localization
Resource files for different cultures
Create .resx files <filename>.<culture>.resx

———
Exceptions
Anticipated and Unanticipated

Where to catch:
UI Event Handlers and Non UI Threads for anticipated
Global exception handler for unanticipated

Unhandled exceptions:

UI Thread: Error message
Paint Event Handler: ugly rectangle
Non UI Thread: Application has stopped working

Global Exception Handlers:
Application.SetUnhandledExceptionMode(UnhandledExceptionMode.CatchException);

//catch exceptions on UI thread
Application.ThreadException += ApplicationOnThreadException;
//option to continue or call Application.Exit

//catch exceptions on other threads
AppDomain.CurrentDomain.UnhandledException += CurrentDomainOnUnhandledException;
//application will terminate

Exception Handling Guidelines
 * Don’t use global exception handler for everything, only unanticipated exceptions
 * Handle exceptions ‘locally’ in time and space
 * Catch specific exceptions if you can do something about them
 * Log everything (message, stack trace, inner exception)

Where to handle
 * User initiated actions (eg button clicks)
    - Report the error to user
    - Perform any cleanup
 * Other UI events
   - e.g. Timer, Paint, MouseMove
 * background threads
   - handle for each task

———
Ways to start a background task

myDelegate.BeginInvoke() (Asynchronous Program Model)
Thread.Start()
ThreadPool.QueueUserWorkItem()
backgroundWorker.RunWorkerAsync()
Task.Run() (TPL)
await async

myDelegate.BeginInvoke()
- has been there from the beginning of .NET
- Call EndInvoke to get result and catch exceptions
- can pool for completion iwth IAsyncResult.IsCompleted
- Can be cumberstome

Thread.Start()
- Can be very powerful
- Can set thread name and priority
- Allows us to wait or poll for completion
- Can be overkill and may be appropriate for long-running tasks

ThreadPool.QueueUserWorkItem()
- Runs immediately or queues for available Threadpool thread
- No completion notification or exception handling
- Do not use if you can use TPL

BackgroundWorker
- Notifies us of progress, completion and errors on UI thread
- Built-in cancellation mechanism
- Can encourage undisciplined developers to stop putting business logic in code behind of winforms

Task Parallel Library (TPL)
- Powerful and comprehensive, introduced in .NET 4
- Ability to compose tasks
- Cancellation token system

Async/Await
- async and await keywords part of C# 5, introduced with .NET 4.5
- Can be used with .NET 4
- Synchronous-looking code flow
- Catch exceptions over multiple threads
- Continues on UI thread

Find more info on threads markheath.net/post/starting-threads-in-dotnet has links to more pluralsight videos on threads


———
Updating the User Interface
Background threads cannot update UI

Solutions:
- Control.BeginInvoke
- SynchronizationContext.Post
- Poll with a timer
- BackgroundWorker
- async/await 

——
While a task is running

- Disable any controls to prevent re-entrancy
- Show progress (cursor, progress bar)
- Offer a cancelation option (or automatically timeout)


— — — — — — 
PATTERNS FOR MAINTAINABLE CODE

The problem with monolithic MainForm.cs:
- hard to comprehend
- hard to test (have to manually test)
- hard to reuse - leads to cut-paste

The maintainability solution:
- segregate user interface
- extract business logic from code behind
- create passive views controlled by presenters
- Use the Command Pattern for buttons
- Use an Event Aggregator for messaging

— — 
Segregating UI
 - segregate into user controls early
 
— — 
Model View Presenter

View is entirely passive

Model <- -> Presenter <- -> View

Inject dependencies to Presenter

The command pattern
Create a class to represent each command in your application

PlayCommand
- Execute
- IsEnabled
- IsEnabledChanged
- IsVisible
- Icon

CommandBase
- Exception Handling
- Privileges
- Licensing

Event Publishers and Subscribers

Publisher knows when it happens, subscriber knows what to do about it.

Event Aggregator
When it happens, Publisher tells aggregator, event aggregator passes message to anyone who is interested, and subscriber subscribes to the event aggregator.

Event Aggregator tends to be a singleton used through the application.

Patterns library
- http://pluralsight.com/courses/patterns-library
- Model View Presenter
- Command Pattern
- Event Aggregator

Inversion of Control Containers
 - http://pluralsight.com/courses/inversion-of-control


— — — — — — 
    CREATING CUSTOM CONTROLS

Standard Controls
Third Party Controls
Custom Controls

Can inherit from any existing control
- override behaviour, reuse appearance
- Can’t always fully customize appearance

Some controls offer “owner drawn” mode
- override appearance but reuse behavior

Some controls designed to be base classes
 - Buttonbase inherited by Button, Checkbox, RadioButton
 - TextBoxBase inherited by TextBox, MaskedTextBox, RichTextBox

GDI+ (Graphic Device Interface)

* System.Drawing.Graphics
* Draw shapes and lines
* Pens and brushes
* Draw text and images
* Advanced techniques (anti-aliasing, transparency, transforms and clipping regions)

Handle the Paint event or override OnPaint
PaintEventArgs

Recommendations:
-  Perform all painting in Paint event handler
- Use double buffering (reduces flicker when resizing or scrolling)
- Reuse Brush, Pen, Image and Font resources

Invalidate() makes the control repaint

— — — — — — 
     INTEROPERABILITY

Invoking Windows APIs
Call anny Windows API using Platform Invoke (P/Invoke)

Examine any Windows message
- Override WndProc
- Be nosey

Embedded Web Browser

webBrowser.Document

Hosting WPF content
There are some odd quirks by using a WPF

Incremental Migration
Convert parts of your application to use newer technologies

Can also embed Chrome (awesomium.codeplex.com)

WPF with ElementHost

Benefits of Model View Presenter
reuse Model and Presenter, only need to reimplement view.


Coding Practices
consider the needs of future developers

* Having an exception handling strategy
* Put long-running tasks on background threads
* Name your controls
* Segregate your user interface with user controls
* Keep business logic out of code behind
* Use the Model View Presenter pattern
* Use the Command pattern
* Use Event Aggregators
