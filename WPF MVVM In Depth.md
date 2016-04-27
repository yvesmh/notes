WPF MVVM In Depth

Model View View-Model

Trying to achieve Separation Of Concerns

MVVM Goals/Benefits

* Maintainability
* Testability
* Extensibility

Comes from Model-View-Controller
Then Model-View-Presenter
Then MVVM

Ongoing interaction between View and ViewModel

Data flow and communication primarily through data binding

MVVM can be used across other platforms (not just WPF)

* WPF
* Silverlight
* Windows 8/ WinRT
* HTML5 (knockout/angular)
* Xamarin/Mobile Apps
* Windows 10

Model Responsibilities:
* Contain the client data
* Expose relationships between model objects
* Computed properties
* Raise change notifications (INotifyPropertyChanged)
* Validation (INotifyDataErrorInfo)

View Responsibilities:
* Structural definition of what the user sees on the screen
* Goal: “No code behind”
* Reality: Sometimes need some code behind. (Animations, sometimes cant use data binding)

ViewModel Responsibilities
* Expose data to the view for presentation and manipulation
* Encapsulate interaction logic
    * Calls to business/data layer/service
    * Navigation logic
    * State transformation logic


ViewModel Data:

public Customer Customer { get; set; }
public bool ShowCustomerAlert { get; set; }
public ObservableCollection<OrderItem> Orders { get; set; }
public bool LoggedIn { get; set; }

Client Services / Repositories

* Shared functionality or data access
* Consumed by one or more ViewModels
* Decouples ViewModels from external dependencies
    * Data Storage
    * Service access
    * Client environment
* Can act as data caching container

Fundamental equation of MVVM:

View.DataContext = ViewModel

“Marrying the view and viewmodel”

View-ViewModel Instantiation

View-First vs ViewModel-First

View-First:
* View is constructed first
* XAML kicks off construction
* ViewModel gets constructed and attached to DataContext via View

ViewModel-First
* ViewModel is constructed first
* View is constructed as a consequence of ViewModel being added to UI

— — — 
A word on Async

* Client apps live in async world
* No longer acceptable to show spinner cursor
* Task-based async and async/await are the norm in .NET
* ViewModels often need to wait for async completion of external work or calls
* Client Services / Repositories often expose async methods

Data binding lays the groundwork for MVVM
MVVM moves the data management and interaction logic into the ViewModel
View-First construction from XAML works great for static child views
Several forms of communication exist between View and ViewModel

— — — — — 
Hooking up Views and ViewModels in MVVM

View-First in XAML

InitializeComponent() runs ->

<UserControl x:Class=“ZzaDashboard.Customers.CustomerEditView” Width=“400” Loaded=“OnLoaded”
… >

   <UserControl.DataContext>
     <local:CustomerEditViewModel />
  </UserControl.DataContext>
….
</UserControl>


View-First in Code-Behind

public partial class CustomerListView: UserControl
{
  public CustomerListview()
  {
    this.DataContext = new CustomerListViewModel();
    InitializeComponent();
  }
}

View-First using ViewModelLocator

ViewModelLocator Process

* Figures out which View is being constructed
* If there is a convention for naming, ViewModelLocator knows which ViewModel needs to be constructed
* Constructs the ViewModel
* Sets the DataContext


ViewModel-First with DataTemplates

<ContentControl Content=“{Binding CurrentViewModel}” />

<DataTemplate DataType=“{x:Type local:CustomersOrderTreeViewModel}”>
  <local:CustomersOrderTreeView />
</DataTemplate>

Use DataTemplate by setting ItemTemplate property on the Control

No One’s On First
May have other code in control of constructing both View and ViewModel
Order does not matter
Set DataContext after constructing both

Don’t worry about ViewModel-First or View-First, as long as they’re decoupled and DataContext is set, it should be fine.

— — — 

View/ViewModel Communication in WPF

Command Pattern:

Based on classic Command design pattern

Invoker - View control
Receiver - ViewModel

Use delegating command implementation

Invoker -> ICommand -> Receiver

Use abstraction.

XAML:
<Button Content=“Delete”
   Command=“{Binding DeleteCommand}”
  />

ViewModel:

public class CustomerListViewModel
{
   public ICommand DeleteCommand { get; private set; }

  public Customer SelectedCustomer
  {
     get { return _selectedCustomer; }
    set 
    {
       _selectedCustomer = value;
      DeleteCommand.RaiseCanExecuteChanged();
    }
  }

  public CustomerListViewModel()
  {
     DeleteCommand = new RelayCommand(OnDelete, CanDelete);
  }

  public void OnDelete()
  {
     Customers.Remove(SelectedCustomer);
  }

  public bool CanDelete()
  {
      return SelectedCustomer != null;
  }

}

Add keyboard shortcuts:

<UserControl.InputBindings>
  <KeyBinding 
      Key=“D” 
      Modifiers=“Control” 
      Command=“{Binding DeleteCommand}” />
</UserControl.InputBindings>

— — 
Attached Properties / Behaviors

* Attached Properties form the basis of Behaviors
* Behaviors
* Blend SDK is preferred way
    * Uses attached properties itself to attach Blend SDK-based Behaviors to elements.
* Behaviors can form a communication bridge between View and ViewModel
    * Events /property changes in View trigger commands or method calls into ViewModel
    * Behavior in View can listen for events / property changes from ViewModel and modify UI accordingly


Using {Binding} without specifying anything binds to the DataContext

— — — 
Property Change Notifications

Property Change Notifications are essential to data binding

Two options:
* DependencyProperties
* INotifyPropertyChanged 

INotifyPropertyChanged is more appropriate for ViewModels and Models

public event PropertyChangedEventHandler PropertyChanged = delegate { }; // trick that makes sure it isn’t null

— — — — 

MVVM Pattern

There are no correct names, only good or bad ones in the eye of the beholder.

What matters is having a pattern and using it consistently.

View Naming Guidance

Typically named “<Name>View”
May have other name suffixes (i.e. Window, Page, Dialog)
Recommendation: Don’t include “View” in the type name unless it has a ViewModel

ViewModel Naming Guidance

If the View name ends in “View”, append “Model” (CustomerEditView / CustomerEditViewModel) 
If the View name does not end in “View”, append “ViewModel” (MainWindow / MainWindowViewModel)
The rest of the ViewModel name should match the View name

Locating Components

By Type (ViewModels, Views go in folders called ViewModels and Views)
By Feature (ViewModels and Views go inside same folders, and the folder name is the feature)

By type can be bad for large apps

— — — 
   DEPENDENCY INJECTION /IoC Containers

* Inversion of Control (IoC) and Dependency Injection (DI) are closely related
* A container is infrastructure code that does both for you
* The Container is responsible for:
    * Constructing an object when asked
    * Determining what that object depends on
    * Constructing those dependencies
    * Injecting them into the objects being constructed
    * Recursively doing this process
* There are many containers to choose from:
    * Unity
    * AutoFac
    * Ninject
    * StructureMap

MVVM Toolkit / Framework

* Prism
* MVVM Light
* Caliburn

Implicit DataTemplates is key mechanism to swapping Views in a container as a means to navigate to another View

A reason to construct ViewModel in code behind is when the ViewModel has a parameterized constructor that requires dependencies to be injected into it


