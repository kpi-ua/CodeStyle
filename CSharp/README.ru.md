# Стиль и конвенции кода C#
[English](README.md) | [Русский](README.ru.md)


### Use PascalCasing for class names and method names

```cs
public class ClientActivity
{
    public void ClearStatistics()
    {
        //...
    }
    public void CalculateStatistics()
    {
        //...
    }
}
```
Почему: consistent with the Microsoft's.NET and easy to read.


### Use camelCasing for method arguments and local variables
```cs
public class UserLog
{
    public void Add(LogEvent logEvent)
    {
        int itemCount = logEvent.Items.Count;
        // ...
    }
}
```
Почему: consistent with the Microsoft's.NET and easy to read.


### Do not use Hungarian notation or any other type identification in identifiers
```cs
// Правильно
int counter;
string name;
 
// Неправильно
int iCounter;
string strName;
```
Почему: consistent with the Microsoft's.NET and Visual Studio IDE makes determining types very easy (via tooltips). In general you want to avoid type indicators in any identifier.

### Do not use Screaming Caps for constants or readonly variables
```cs
// Правильно
public static const string ShippingType = "DropShip";
 
// Неправильно
public static const string SHIPPINGTYPE = "DropShip";
```
Почему: consistent with the Microsoft's.NET. Caps grap too much attention.


### Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri
```cs
// Правильно
UserGroup userGroup;
Assignment employeeAssignment;
 
// Неправильно
UserGroup usrGrp;
Assignment empAssignment;
 
// Exceptions
CustomerId customerId;
XmlDocument xmlDocument;
FtpHelper ftpHelper;
UriPart uriPart;
```
Почему: consistent with the Microsoft's.NET and prevents inconsistent abbreviations.


### Use PascalCasing for abbreviations 3 characters or more (2 chars are both uppercase)
```cs
HtmlHelper htmlHelper;
FtpTransfer ftpTransfer;
UIControl uiControl;
```
Почему: consistent with the Microsoft's.NET. Caps would grap visually too much attention.


### Use Underscores for private class variables
```cs
// Правильно
public DateTime _clientAppointment;
public TimeSpan _timeLeft;
 
// Exceptions
public DateTime client_Appointment;
public TimeSpan timeLeft;
```
Почему: underscore before variable name makes it possible to understand at once that the variable is defined  at the class level.


### Use implicit type var for local variable declarations. Exception: primitive types (int, string,  double, etc) use predefined names
```cs
var stream = File.Create(path);
var customers = new Dictionary();
 
// Exceptions
int index = 100;
string timeSheet;
bool isCompleted;
```
Почему: removes clutter, particularly with complex generic types. Type is easily detected with Visual Studio tooltips.


### Use noun or noun phrases to name a class
```cs
public class Employee
{
}
public class BusinessLocation
{
}
public class DocumentCollection
{
}
```
Почему: consistent with the Microsoft's.NET and easy to remember.


### Prefix interfaces with the letter I.  Interface names are noun (phrases) or adjectives
```cs
public interface IShape
{
}
public interface IShapeCollection
{
}
public interface IGroupable
{
}
```
Почему: consistent with the Microsoft's.NET.


###  Name source files according to their main classes. Exception: file names with partial classes reflect their source or purpose, e.g. designer, generated, and other
```cs
// Located in Task.cs
public partial class Task
{
    //...
}
// Located in Task.generated.cs
public partial class Task
{
    //...
}
```
Почему: consistent with the Microsoft practices. Files are alphabetically sorted and partial classes remain adjacent.


### Organize namespaces with a clearly defined structure
```cs
// Examples
namespace Company.Product.Module.SubModule
namespace Product.Module.Component
namespace Product.Layer.Module.Group
```
Почему: consistent with the Microsoft's.NET. Maintains good organization of your code base.


### Vertically align curly brackets
```cs
// Правильно
class Program
{
    static void Main(string[] args)
    {
    }
}
```
Почему: Microsoft has a different standard, but developers have overwhelmingly preferred vertically aligned brackets.


### Declare all member variables at the top of a class, with static variables at the very top.
```cs
// Правильно
public class Account
{
    public static string BankName;
    public static decimal Reserves;
 
    public string Number {get; set;}
    public DateTime DateOpened {get; set;}
    public DateTime DateClosed {get; set;}
    public decimal Balance {get; set;}
 
    // Constructor
    public Account()
    {
        // ...
    }
}
```
Почему: generally accepted practice that prevents the need to hunt for variable declarations.


### Use singular names for enums. Exception: bit field enums.

```cs
// Правильно
public enum Color
{
    Red,
    Green,
    Blue,
    Yellow,
    Magenta,
    Cyan
}
 
// Exception
[Flags]
public enum Dockings
{
    None = 0,
    Top = 1, 
    Right = 2, 
    Bottom = 4,
    Left = 8
}
```
Почему: consistent with the Microsoft's.NET and makes the code more natural to read. Plural flags because enum can hold multiple values (using bitwise 'OR').


### Do not explicitly specify a type of an enum or values of enums (except bit fields)
```cs
// Неправильно
public enum Direction : long
{
    North = 1,
    East = 2,
    South = 3,
    West = 4
}
 
// Правильно
public enum Direction
{
    North,
    East,
    South,
    West
}
```
Почему: can create confusion when relying on actual types and values.


### Do not suffix enum names with Enum
```cs
// Неправильно
public enum CoinEnum
{
    Penny,
    Nickel,
    Dime,
    Quarter,
    Dollar
}
 
// Правильно
public enum Coin
{
    Penny,
    Nickel,
    Dime,
    Quarter,
    Dollar
}
```
Почему: consistent with the Microsoft's.NET and consistent with prior rule of no type indicators in identifiers.

***
Базируется на [dotfactory C# Coding Standards and Naming Conventions](http://www.dofactory.com/reference/csharp-coding-standards).
