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