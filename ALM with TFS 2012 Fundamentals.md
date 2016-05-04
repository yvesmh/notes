# ALM With TFS 2012 Fundamentals

## Microsoft ALM Overview

### If you learn only one thing

TFS is more than just version control

### What is ALM?

ALM = Application Lifecycle Management

Microsoft's view of ALM

* Plan and Track
* Design
* Develop
* Automated Build
* Testing
* Test Lab Management

Not sucking wind when you develop your application

Not losing a couple million $$ writing software.

Not just for large projects

Software best practices for Development, Management and Testing

TFS is a bit of a "catch-all".


TFS != ALM

A lot of Visual Studio features needs TFS or work better with it.

### TFS Can help

TFS streamlines ALM best practices

TFS alone won't save you

(Almost everything in software is a people problem.)

TFS will help to...

* Streamline project management
* Streamline development best practices
* Add traceability
* Gain "situational awareness"

### TFS and ALM is not just for small teams

Small companies might need ALM more than big companies

### The big picture and TFS

* Version Control
* Requirements
* Agile Planning
* Automated build
* Testing & defect tracking
* Feedback
* Lab management
* Reporting

### Team Foundation Server

The glue that holds the ALM stack together

* Standard configuration
	- Installed on Windows Server 2008, Windows Server 2008 R2, or Windows Server 8
	- SQL Server 2008, SQL server 2008 R2, or SQL Server 2012
	- SQL Server Reporting Services
	- SharePoint
	- Single or multiple server

* Basic compiguration
	- Installed on Windows 7 or Windows 8
	- Installs quickly on a single box
	- No SharePoint and no SSRS


### How to connect to TFS

* Visual Studio 2012 via Team Explorer
* TFS via Web Access (more for management and planners) gives read-only access to source control
* Microsoft Office:
	- Excel, Project, PowerPoint, Outlook
	- SharePoint
* Command line
* Team Explorer Everywhere (TEE)
	- Command line
	- Eclipse plugin

### Version control

* Not SourceSafe
* Enterprise-quality source control
	- Transactional & Atomic check-in
	- Stored in SQL server
* Features
	- Check-in/check-out
	- Branch/merge
	- Label
	- Shelvesets
* Check-ins can be associated to work items (great for traceability)

### Requirements management

#### Requirements: Work Items

* TFS Work Items
	- Scrum: Product Backlog items
	- Agile: user stories
* Contain the details for a requirement
	- Including who it's assigned to
* Can be associated to
	- Storyboards
	- QA Test cases
	- Implementation tasks
	- Check-ins
	- Builds

#### Requirements: PowerPoint Storyboards

* Lightweight requirements
* You don't have to be a genius to use PowerPoint. Let non-technical stakeholders create screen mocks
* Faster to create PowerPoint than working UI
	- Iterate and tweek until everyone agrees 

### Agile Planning

* Work Items
	- Product Backlog Items, User stories
	- Tasks
* Product Backlog Management
	- List of everything to do
	- Priority
	- Velocity forecasting
* Sprint Planning
	- Decompose PBIs into Tasks
	- Capacity planning
* Scrum Board
	- Run the daily scrum
	- View and update task status
* Burndown Chart
	- How much work is left?
	- Updates in real-time

### Automated Build

* Prevents the "works on my box" problem
* Prove you can build your app.
* Neutral 3rd party machine
* Makes integration second nature -> Continuous integration
* Basis of your release process
	- Versions of code are now traceable to builds
	- QA testing and defect tracking against builds rather than guesses

### Testing and defect tracking

#### Testing types

* Developer Testing
	- Visual Studio 2012
	- Unit testing at the API level
	- Coded UI Testing - Testing a running user interface
* Performance testing
	- Load Testing your application
	- WEb applications or unit tests
* QA Testing
	- aka "manual testing"
	- Microsoft Test Manager (MTM)
	- Test plans & test cases
	- Exploratory testing
	- Defect Tracking
	- Plugs into Lab Management
	- 

### Feedback

* Collaborate with customers & stakeholders
* PowerPoint storyboardings
	- Lightweight requirements
	- Built it AFTER there's some agreement
* Feedback Manager
	- Request feedback via TFS (rather than e-mail)
	- Track whether you got feedback
	- Track the feedback

#### The Feedback Process

Create a Feedback Request

* What do you want feedback on?
	- Web Application URL
	- Remote machine
	- Client Application
* What questions do you want answered?
* Request is emailed

User reviews the application

* User installs the feedback client
* Can record audio & video
* Screenshots
* Text

You get the Feedback response as a Work Item

### Lab Management

* Deploying builds onto test machines is a pain
* Managing test machines is a pain
* Lab Management streamlines this with virtualization
	- Hyper-V
	- System Center Virtual Machine Manager

Lab Management Build type

Configurable deploy script for each machine in the environment

The steps:

1. Run a compilation build
2. Deploy the build
3. Run Coded UI tests (optional)

After It's deployed:

* Do nothing
* Run MTM Test Cases
* MTM Exploratory Testing

### Reporting

* TFS gathers a lot of data
* Use this data to:
	- Track what's going on
	- Answer questions about quality
	- Answer questions about progress

#### About TFS Reporting

* Stored in a relational database
* Stored in a data warehouse
	- SQL Server Analysis Services
* SQL Server Reporting Services (SSRS) Reports
	- Canned, "out of the box" reports
	- Create your own
* Microsoft Excel reports
	- Ad hoc reports

## Basic Setup and Configuration

### The core pieces of TFS

* TFS Application Tier
	- IIS, Web Services
	- Visual Studio Team Foundation Background Job Agent
* SQL Server
* SQL Server Reporting Services
* SQL Server Analysis Services
* SharePoint (or SharePoint Services)

### Other pieces of TFS

* Team Build Service
	- Automated build server
	- Controller & Agent
* TFS Proxy Server
	- Version control proxy
	- Local version control cachin
	- Nice for teams with slow connections to TFS
* TFS Agents
	- Load Testing Agents
	- Lab Agents
	- Controller & Agent


### Stuff that bolts on to TFS

* System Center Virtual Machine Manager
	- Enables Lab Management
* Microsoft Project Server
	- Replicate data to/from TFS and Project Server
	- Enterprise Project Planning
	- Enterprise Resource Management
	- Do you like Waterfall? Do you have a PMO? You want this.
* Pre-emptive analytics
	- Errors in production -> Work items in TFS


### Configurations

* Basic
	- Windows 7 or Windows 8
	- TFS +SQL Server Express
	- Installs fast
	- Think "replacement for SourceSafe"
* Standard, Single Server
	- Windows 2008, Windows 2008 R2, Windows Server 8
	- SQL Server 2008, SQL Server 2008 R2, or SQL Server 2012
	- SSRS
	- SharePoint
* Dual Server
	- TFS "app tier", SSRS, and SharePoint on one server
	- SQL Server on another server

### Fancy TFS configurations

* Split apart as you see fit
	- TFS App tier
	- SQL Server Reporting Services
	- SQL Server & SQL Server Analysis Services
	- SharePoint
* Clustered SQL Servers
* Clustered TFS App Tiers

### TFS hardware capacity planning

Install guide says:
 * For less than 500 users
 * Dual core, 2.13 GHz processor
 * 4 GB of RAM
 * 300 GB hard disk
 * No SharePoint

 Author's preference:
 * Hyper-V
 * Dual Processor
 * Dynamic Memory
 	- Start at 1 GB
 	- Max at 8 GB
 * 160 GB dynamically expanding hard disk
 * Install SharePoint Foundation 2010

### TFS pre-requisites

* Install SharePoint Foundation 2010
* Install SQL Server Reporting Services
* This stuff is optional but don't be lazy
* Install & configure them when you install TFS
* It's a hassle to add later

* Windows Server
* .NET Framework 3.5
* SQL Server
* SharePoint

### Installing TFS

*Screaming-Fast Install Guide*

* Create a fresh install of Windows 2008 R2 x64
	- Go to Windows Update
	- Install Microsoft Update
	- Install all the Service Packs and patches
* Install SQL Server 2008 R2 Standard
	- Database Engine Services
	- Full-Text Search
	- Reporting Services
	- Analysis Services
* Go to Windows Update and patch SQL Server
* Install Team Foundation Server 2012

### Team Project & Team Project Collections

Team Project is:
* Bucket that contains everything related to a software development effort
* Has a Name & Process Template

Team Project Collection:
* Collection of Team Projects
* Gets its own database
* Backup & Restore

### Process Templates
* Define the initial structure of a new Team Project
* Microsoft Visual Studio Scrum 2.0
* MSF for Agile Software Development 6.0
* MSF for CMMI Process Improvement 6.0

### Permissions & Security

Security is administered at multiple levels:

* Team Project Collection
* Team Project
* Within a Team Project
	- Source Control
	- Work Item Tracking
* SQL Server Reporting Services
* SharePoint

### A simple backup plan for TFS

If everything is on one box, backup is easy

Create a Maintenance Plan in SQL Server

Backup your SQL Server Reporting Services Encryption Key

Best Practice is to move backups to somewhere else

## Version Control Basics

### TFS Version Control

Transactional. Either all files succeed or all fail during check-ins.

Shelvesets are temporary check-ins.

### How to access Version Control

* Visual Studio
	- Source Control Explorer
	- Solution Explorer
* Web Access
	- Read-only
* Command-line
	- TF.exe
* Team Explorer everywhere
	- Cross-platform
	- Eclipse plugin
	- Command-line

### Workspaces

Mapping between TFS and your computer

Folders in TFS get mapped to folders on your computer

Workspace types:
* Server 
* Local

Workspace Permissions:
* Private
* Public
* Limited Public

File time
* Check-in
* Current

Workspace mapping can sometimes get messed up

If something isn't doing what you expect, *go to the workspace editor* 

Workspace Editor located in Source Control Explorer. May be hidden on small screens if the team explorer is docked to the right.

### Workspaces: Server vs Local

Server
* TFS tracks the state of your workspace
* Really likes network connectivity
* If your workspace is huge, use this
* Compatible with Visual Studio 2010 and earlier

Local
* Visual Studio 2012+
* Works nicely offline
* You'll probably want this unless:
	- Your workspace is huge
	- You're a control freak


### Configure Version Control for a New Project

Create a folder off of the root (main or trunk or whatever)

Never add any files to the root (in case you ever want to branch)

### Keep it simple

If you can't do a "Get Latest" then compile and then run unit tests... you're doing something wrong.

* Workspace mappings should be simple
* No crazy copying of DLLs or config around
* Does it take you hours every day to get the app running?
* Does it take new employees a couple days to get the app running?
* Constant problems with missing DLLs?


### Version Control Operations

* Pending changes are batched.
	- Until you check-in, it only exists on your machine (except labels)
* Check-ins become a changeset
	- Changeset number
	- Can be associated to a work item
* Change types:
	- Add
	- Edit
	- Rename
	- Delete / Undelete
	- Branch / Merge

## Version Control beyond the basics

### Local Workspace: Offline Features

Things you can do offline:
* Add
* Edit
* Rename
* Delete
* Undo
* Compare

You can't do offline check-in

### Free yourself from the read-only bit

* Local workspaces don't use the read-only bit
* Pending changes window is now smarter
* Included Changes
* Excluded Changes
* Detected Changes

### Locks

Check-in Lock
* Anyone can edit locally
* Can't check-in until you check in or the lock is released

Check-out Lock
* No one can modify the file (aka "pend a change")
* Local workspaces makes this unenforceable
* Not available if "Asynchronous Checkout" is enabled

Can be overridden if you have the "UnlockOther" permission

### Shelving and Shelvesets

Temporary chec-ins

No one sees it unless they look for it

Used for:
* Code Reviews
* Gated Check-in builds
* My Work's Suspend & Resume
* Sharing your work with someone else
* Backing up your work

To unshelf:
First go to Source Control Explorer -> Choose something and then click on File -> source control -> find -> find shelvesets

### Branching & Merging

Branch = Work on multiple versions of a similar code base simultaneously

Merge = Move changes between these versions.

Best practices:
* Merges are difficult
*Don't branch unless you have to
* Understand what a "release" means

http://vsarbranchingguide.codeplex.com
