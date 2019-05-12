# Installer Research

I am [Carlos Peña Hernando](https://www.linkedin.com/in/carlos-pe%C3%B1a-hernando-aa757aaa/), student of the [Bachelor’s Degree in Video Games by UPC at CITM](https://www.citm.upc.edu/ing/estudis/graus-videojocs/). This content is generated for the second year’s subject Project 2, under supervision of lecturer [Ricard Pillosu](https://www.linkedin.com/in/ricardpillosu/?originalSubdomain=es).


## The Origins: The phenomenon of Application Packaging
To put you in context, I would like to talk about the cause at a global level about the existence of application packaging software and therefore about this document that you are reading. Let's start

The maintenance of desktop and notebook systems has become an expensive proposition for many corporate networks due to application management costs. Since then, New application management techniques are being developed to help enterprises administer their existing PC investments more. 

One of them is application packaging that in general terms can help enterprises manage growing volumes of software for desktop and server systems. But what exactly is Application Packaging?

### What is Application Packaging?
Application Packaging is the creation of an executable (or file used by a service) that contains the files, registry and logic to install an application onto a device. This executable or file is known as an installation package.

Therefore, Application packaging involves the preparation of standard, structured software installations targeted for automated deployment. This packages must be prepared and meet the installation requirements for an specific environment (corporate standards for software usage and desktop design, multiple languages, regional issues, etc).

In addition, packages must be prepared for both commercial software and applications developed in-house.

### Packaging Content: Application’s Artifacts

Applications are typically more than a single executable. They often contain:
* Multiple files in different locations
* Shortcuts
* Registry
* Runtime engines
* .NET registration
* Shell integration
* ActiveX controls
* Databases

… and much more

### Application packages Formats

* Application packages include formats such as:
* Microsoft Windows Installer -> Setup.msi
* Legacy executables -> Setup.exe
* Windows store .appx
* Batch/script files -> Install.vbs, Install.ps1, Install.bat
* Loose Files / Raw Files
* Add-in /Plug- in -> .dll / .xla /.xlam / .ppam / .dotm, etc…)


## The Evolution: Microsoft Windows Installer

To enable this level of application management, Microsoft now provides the Microsoft® Windows® Installer (MSI) service as part of its desktop operating systems.

This database-driven service resides on workstations and controls installing, uninstalling, patching, and repairing of software. Input into the Windows Installer is an .msi formatted file as already shown above.

### MSI Application Management

The Windows Installer service was designed to support every phase of the application management life cycle, providing a service to support each step involved in managing a desktop application from deployment through retirement.

To support these functions, the Windows Installer needs to receive instructions from an installation package. 

### Windows Installer Technology

Previously, installation packages took the form of a setup.exe file. Unfortunately, inconsistencies in the way independent software vendors and internal software development groups created these installation files sometimes led to complications when administrators attempted to manage automated installations.

The emerging standard is for Windows Installer to use the msiexec.exe program to process the installation packages at an end user’s PC. 
The packages follow a standardized database structure containing the information that Windows Installer requires to install or uninstall an application and to run the user interface for the setup. 

In overall, The Windows Installer technology is divided into two parts that work in combination; these include a client-side installer service (Msiexec.exe) and a Microsoft Software Installation (MSI) package file. Windows Installer uses information contained in a package file to install the program.

## But Why use Windows Installer?

Windows Installer has many built-in functions that save time and effort. 

* Automatic add/remove, uninstall, reinstall, and repair support. If an application is already installed, Windows Installer will detect it and display a maintenance user interface instead of an application install interface. 

* In maintenance mode, Windows Installer detects which parts of an application are installed and can allow a user to add or remove features or reinstall the application. 

* The repair functionality also appears in maintenance mode, but is also automatically run every time a shortcut for the application is activated in Windows 2000. The repair functionality is particularly useful for administrators whose users like to recklessly clean up disk space. 
 
* Installer's advertising feature. Advertising allows an application to appear to be installed, but files are not actually installed on the system until the application is activated through a shortcut, extension, or COM server. Advertising makes an application available on the desktop, but since it's not installed until it is activated, companies save on licensing fees and disk space. Once a user clicks on a shortcut or double-clicks on a file associated with that application, the application installs automatically.
 
* The same functionality can be written into the application itself. For example, an application may have a particular feature that is rarely used, so it is not installed by default. A developer could put Windows Installer API calls in the code that activates that feature to make it install on demand. Using installation on demand saves disk space and avoids requiring the user to exit the program and rerun the setup to install features that aren't installed by default. 



### MSI files and components

### What is a .msi file?
A file with .msi extension is a simple database file that can be read by Microsoft Windows Installer service contained in all recent versions of Microsoft Windows. The database contains the files, registry and instructions to the Windows Installer service in order to install the application.

### What is a Msiexec.exe ?
The Msiexec.exe program is a component of Windows Installer. When it is called by Setup, Msiexec.exe uses Msi.dll to read the package (.msi) files, apply any transform (.mst) files, and incorporate command-line options supplied by Setup. 

The installer performs all installation-related tasks, including copying files to the hard disk, making registry modifications, creating shortcuts on the desktop, and displaying dialog boxes to prompt for user installation preferences when necessary.

When Windows Installer is installed on a computer, it changes the registered file type of .msi files so that if you double-click an .msi file, Msiexec.exe runs with that file.

### MSI Extensions
Each installation package includes an .msi file containing the installation database, a summary information stream, and data streams for various parts of the installation. The .msi file can also contain one or more transforms, internal source files, and external source files or cabinet files required by the installation

### What MSI Supports?
As a Service, Windows Installer is designed to support software installations as the local Administrator role in locked environments, enhancing the application process. 

Windows Installer can support applications installed from a network share—referred to as an administrative installation—or locally on an end user’s PC. The downside to using a network share can be that systems receive patches or repairs only when they are connected to the network, which may be a consideration for organizations supporting many notebook users.

### Creating MSI files

Creating MSI files To build the installation package in the correct MSI database format, developers must collect information about each application. Items include executable files, installation instructions, configuration parameters, test instructions, and hardware and software dependencies. 

Best practices recommend that installation packages be created by experienced packaging engineers, using **tools** specifically developed for that purpose. 


## Different approaches
 
## Selected approach
 
## Wix Toolset Integration code
 
## Links to more documentation
 
## TODO's and Solutions
 
### TODO1
 * Expected result
 * Solution
### TODO2
  * Expected result
 * Solution
### TODO3
  * Expected result
 * Solution
### TODO4
  * Expected result
 * Solution
### TODO5
  * Expected result
 * Solution
### TODO6
 * Expected result
 * Solution
### TODO7
   * Expected result
 * Solution
### TODO8
   * Expected result
 * Solution
 
## Improvements
 
## Acknowledgements and Webgraphy


