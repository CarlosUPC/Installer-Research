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

 Application packages include formats such as:
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

**.msi file** : A file with .msi extension is a simple database file that can be read by Microsoft Windows Installer service contained in all recent versions of Microsoft Windows. The database contains the files, registry and instructions to the Windows Installer service in order to install the application.

 **Msiexec.exe** : The Msiexec.exe program is a component of Windows Installer. When it is called by Setup, Msiexec.exe uses Msi.dll to read the package (.msi) files, apply any transform (.mst) files, and incorporate command-line options supplied by Setup. 

The installer performs all installation-related tasks, including copying files to the hard disk, making registry modifications, creating shortcuts on the desktop, and displaying dialog boxes to prompt for user installation preferences when necessary.

When Windows Installer is installed on a computer, it changes the registered file type of .msi files so that if you double-click an .msi file, Msiexec.exe runs with that file.

**MSI Extensions** : Each installation package includes an .msi file containing the installation database, a summary information stream, and data streams for various parts of the installation. The .msi file can also contain one or more transforms, internal source files, and external source files or cabinet files required by the installation

### What MSI Supports?
 
Windows Installer can support applications installed from a network share—referred to as an administrative installation—or locally on an end user’s PC. The downside to using a network share can be that systems receive patches or repairs only when they are connected to the network, which may be a consideration for organizations supporting many notebook users.

### MSI Packaging and Deployment Tools

Creating MSI files To build the installation package in the correct MSI database format, developers must collect information about each application. Items include executable files, installation instructions, configuration parameters, test instructions, and hardware and software dependencies. 

Best practices recommend that installation packages be created by experienced packaging engineers, using **tools** specifically developed for that purpose. 

Industry leaders for MSI creation are generally **Advanced Installer**, **Installshield** and the open source solution **WiX**  - which you seem somewhat familiar with.

## MSI packaging tool selected: WIX Toolset

WiX
* The big plus is the text source files. There is no need to store the source as a binary where it is almost impossible to track changes and do proper version control.

    * Proper text sources make all the difference for development teams in terms of branching, versioning and merging. It is a quantum leap (in my opinion particularly for in-house development in large corporations - where process is complex, turnaround is quick and there are many developers).
    * The need for and use of text source files was central to the creation of the WiX toolkit. 
    *  Some deployment tools that store the installer as binaries could end up in situations where the binary source would exhibit mysterious problems that could never be tracked down properly.
 
* Rock solid, very few significant bugs.
    * For those who have struggled with long-standing, intermittent, unexplainable bugs in other tools, this is a godsend. {War stories removed}.
    * And even better: problems actually seem to get fixed in WiX, sometimes with community help - as is appropriate for an open source toolkit. Most of the time it seems the core team takes care of it though.
 
* Very feature rich, but somewhat hard to use at times.
    * Takes time to get used to, and even when you are used to it things can be "fiddly" to get right (particularly if you don't use the included helper tools properly).
    * It helps to use the dark.exe decompiler tool to decompile existing MSI files to WiX XML. This allows you to study the WiX source without knowing too much about it beforehand.
    * Exceptional customizability for complex things such as IIS, COM+, SQL Server, permissioning, firewall rules, etc... "Everything" is possible, but somewhat involved at times.
    * WiX effectively "extends Windows Installer" with new and much needed functionality. This is a massive benefit for everyone who previously had to "roll their own" solutions - often for things that seemed trivial (but was still very error prone).
    * The power of these extensions can not be overstated. You can get rid of a lot of self-written, complex custom actions in favor of tested solutions. With proper rollback support! (a much neglected feature in vendor setups - in my experience almost all of them - causing unclean system state after aborted setups).
    * I have personal experience writing a C++ dll with custom actions for common tasks with proper rollback support, and the amount of work was staggering - especially the QA of the actual rollback feature.

* A remarkable lack of GUI tools and very few good samples available - particularly for WiX 4.
* Full integration in Visual Studio, with IntelliSense.
* It's free (!). Every developer can build the setup. Someone must own it though(!). Really ;-).
* It is Open Source too. The "community":[https://github.com/wixtoolset](https://github.com/wixtoolset). 


## Purpose of Application Packaging

Before we talked about the cause of the existence of application packaging in a global and generic way but that concrete purposes and benefits are sought in their use?
* Only the simplest applications can work with a simple file copy, and even then you need to have a convenient way to actually download and do the copying of the files to the right location

* The setup is also a marketing tool that can be used for branding and consistency across products as well as allowing installation of a trial version of the product

* a setup provides upgrade and patching features for new versions as well as uninstall and cleanup of the system when the user wants to remove your software

* A good setup may also be signed with digital certificates to ensure the file can not be hampered with in transit, and that the vendor is certifiable and hence serious

* A solid setup and deployment prevents piracy 

## The Complexity of Deployment
Deployment is a simple concept, with a complicated mix of variables that can cause the most mysterious errors. In this section it will discuss the most common and important problems generated by the deployment of software and applications.

* Errors in deployment are cumulative in the sense that once you have a deployed error, you generally have no access to the machine in question for debugging - and the fix could easily do more damage. You are managing a delivery process, not just debugging code and binaries. 

* Deployment (setups) is therefore the complex process of migrating any computer from one stable state to another. This requires a disciplined approach. The setup should install all required files and settings and ensure the product is configured for first launch or ready to be configured upon launch without failure.

* The list of things a setup may need to do is growing all the time, and for every new versions of Windows it seems new obstacles are put in place to make deployment harder (UAC prompts, self-repair lockdown on terminal servers, changed core MSI caching behavior, new folder redirects,etc)

## Deployment Tasks

The tasks and features needed in a setup range from the very fundamental and basic with built-in Windows Installer or third party tool support, to the highly customized tasks called **“custom actions”** where you have to actually code something yourself to deal with unique deployment requirements.

### Set up basics
All third party tools provide good support for these setup fundamentals, but there are some differences. The installation of prerequisites may be the area where third party tools and free frameworks like WiX differ the most in terms of ease of use. The following list shows the fundamentals which all setup must built-in. 

* Check if the system is suitable for installation for the package in question.

* Scan for presence and if necessary install prerequisites and runtimes.

* Provide a GUI suitable for input of required settings from the user.

* Allow installation in silent mode for corporate use.

### Custom Actions
When there is no built-in support for a certain operation or task in Windows Installer itself, or in any of the various third party tools available, you are left having to implement the feature yourself.

When you use Windows Installer, this involves running custom actions of various types (Windows Installer's mechanism for running executable, custom installation logic during installation).

Custom actions are purpose built executables (binaries: dll, exe) and scripts capable of making advanced modifications to the system during installation that are not supported by Windows installer natively or by the deployment tool in use (WiX, Installshield, Advanced Installer, etc...).

There are different custom action types: implemented as scripts (JavaScript, VBScript), .NET binaries (C#, VB.NET, DTF,...), PowerShell scripts, etc.

Custom actions that make modifications to the system run with elevated rights so that changes can be made to the system even if the logged on user does not have admin rights. There is essentially no limit to what these custom actions can do. They are armed and dangerous.

Custom actions are the leading causes of deployment errors and failure.

Most of the custom functionalities mentioned above are now available in the WiX framework as a custom C++ dll - and other tools have some similar, custom features.

## Signing an Application Packaging
Before starting to explain about signing app packages, it is important to understand the meaning of the digital signature. A digital signature is a mathematical scheme based on an algorithm for verifying the authenticity of digital messages or documents. 

Digital signatures are a standard element of most cryptographic protocol suites, and are commonly used for software distribution, financial transactions, contract management software, and in other cases where it is important to detect forgery or tampering.

Signing an application package provides the user with verification that the application data has not been modified after being signed, while confirming the identity of the user or the company that signed it. Therefore, signing an Application Packaging files is an important thing since you help ensure that tampered files are not installed on end-user computers.

### SignTool.exe
There are many methods and ways to approach this topic. Since we are making use of .msi files for the deployment of applications, the best option at the moment is SignTool.exe, SignTool is a command line tool that is used to sign an application package or a batch of applications with a certificate. 

The tool is installed in the \ Bin folder of the Microsoft Windows Software Development Kit (SDK) installation path. Then we need Microsoft Windows SDK to be able to work with SignTool.exe

### How to sign an Application Package (.msi)
* On the development computer, install the certificate that you want to sign the file with.

* Open a Visual Studio command prompt.

* Change to the directory that contains the .msi file.

* Sign the .msi file by using the following command:

```cpp
signtool sign /sha1 CertificateHash SetupNameFile.msi
```

Also, WiX provides internal tools for inscribing an MSI with the digital signatures like "Insignia". You can obtain more information about it [here](http://wixtoolset.org/documentation/manual/v3/overview/insignia.html)

## Wix Toolset Integration code
 
### Project files and components fragment:
 ```cpp

<Fragment>
       <DirectoryRef Id="INSTALLFOLDER">
            <Component Id="Motor_2D.exe" Guid="4b886816-febd-4e5c-a87f-923960027d5c">
                <File Id="Motor_2D.exe" Source="..\Release\Motor 2D.exe" KeyPath="yes" Checksum="yes" />
            </Component> 
       </DirectoryRef>
</Fragment>

 ```
 
### Directory System fragment:
  ```cpp
  
 <Fragment>
		<Directory Id="TARGETDIR" Name="SourceDir">
			<Directory Id="ProgramFilesFolder">
				<Directory Id="INSTALLFOLDER" Name="My UPC Game" />
        
      
         <Directory Id="ProgramMenuFolder">
                <Directory Id="ApplicationProgramsFolder" Name="My UPC Name"/>
         </Directory>
      
      
        <Directory Id="DesktopFolder" Name="My UPC Game" />
      
			</Directory>
		</Directory>
 ```
 
### Shortcut Components fragment:
  ```cpp
 <Fragment>
  
   <DirectoryRef Id="ApplicationProgramsFolder">
       <Component Id="StartMenuShortcut" Guid="19769afe-ec61-4fdc-9538-42c25a6e8fc8">
          <Shortcut Id="ApplicationStartMenuShortcut" 
                 Name="My UPC Game" 
                 Description="My UPC Game Description"
                 Target="[#Motor_2D.exe]"
                 WorkingDirectory="INSTALLFOLDER"
                 Icon = "icon.ico"/>  
          <RemoveFolder Id="RemoveProgramsFolder" On="uninstall"/>
          <RegistryValue Root="HKCU" Key="Software\MyCompany\MyApplicationName" Name="installed" Type="integer" Value="1" KeyPath="yes"/>
       </Component>
   </DirectoryRef>
   
  <DirectoryRef Id="DesktopFolder">
       <Component Id="DesktopShortcut" Guid="5694ea64-2b00-4584-a671-d26134c1de38">
          <Shortcut Id="ApplicationDesktopShortcut" 
                 Name="My UPC Game" 
                 Description="My UPC Game Description"
                 Target="[#Motor_2D.exe]"
                 WorkingDirectory="INSTALLFOLDER"
                 Icon = "icon.ico"/>  
          <RemoveFolder Id="RemoveDesktopFolder" On="uninstall"/>
          <RegistryValue Root="HKCU" Key="Software\MyCompany\MyApplicationName" Name="installed" Type="integer" Value="1" KeyPath="yes"/>
       </Component>
   </DirectoryRef>

 </Fragment>
      
 ```
 
### Icon section:
  ```cpp
  
<Icon Id="icon.ico" SourceFile="assets\iconTwitter.ico" />
    <Property Id="ARPPRODUCTICON" Value="icon.ico" />
    
 ```
### UI Dialog section:
  
   ```cpp
  
    <Property Id="WIXUI_INSTALLDIR" Value="INSTALLFOLDER" />
    <UIRef Id="WixUI_InstallDir" />
   
    
    <WixVariable Id="WixUIBannerBmp" Value="assets\ui_background.bmp" />
    <WixVariable Id="WixUIDialogBmp" Value="assets\ui_background.bmp" />
    <WixVariable Id="WixUILicenseRtf" Value="assets\License.rtf" />
   ``` 
    
### UI Dialog section:
 
  ```cpp
 <Feature Id="ProductFeature" Title="WIX_Setup" Level="1">
      <ComponentRef Id="Motor_2D.exe"/>
      <ComponentRef Id="StartMenuShortcut" />
      <ComponentRef Id="DesktopShortcut" />
      <ComponentGroupRef Id="HeatGenerated" />
		</Feature>
 ```
 
## TODO's and Solutions
In order to perform the following exercises, it is highly recommended to spend some time reading the documentation / user manual provided by the Wix Toolset framework. You can access directly by clicking [here](http://wixtoolset.org/documentation/).

### TODO1 : Customize product features + mapping exe project file

#### Explication:
You have to add the .exe file of the project by creating a "component" element in the appropriate fragment. Once created, you must add the required attributes (ID and GUID) and create as your child a "File" element where you have to add your path as an attribute. You must use the "DirectoryRef" element to reference the folder where you want the .exe file to be copied and use the "ComponentRef" element in the feature section to tell the framework to execute said action.
#### Test:
If you run the .msi file generated after build WIX Setup project, the executable will be installed silently on your computer. You can find it both in the **ProgramFilesFolder** directory in its corresponding folder and in the **Control Panel**.

#### Solution:
Into Component fragment:
```cpp
<DirectoryRef Id="INSTALLFOLDER">
            <Component Id="Motor_2D.exe" Guid="4b886816-febd-4e5c-a87f-923960027d5c">
                <File Id="Motor_2D.exe" Source="..\Release\Motor 2D.exe" KeyPath="yes" Checksum="yes" />
            </Component> 
       </DirectoryRef>

```
Into Feature fragment:
 ```cpp
 <ComponentRef Id="Motor_2D.exe"/>
 ```
 
 
### TODO2 : Add Start Menu Shortcut
#### Explication:
You have to add in the directory system the "ProgramsMenuFolder" directory and inside it create the directory where to instantiate the shortcut of the start menu. Then you must create it as a "component" element following the directrizes used in the previous TODO and add as a child the "Shortcut" element where you should indicate the .exe that you want the shortcut to point to. Finally, use the "ComponentRef" element to warn the framework to execute the instruction.
#### Test:
If you run the .msi file generated after build WIX Setup project, the executable will be installed silently on your computer and the start menu shortcut will be instanced in the start menu of your computer. You can also find the folder where the shortcut is in the **"ProgramMenuFolder"** directory

#### Solution:

Into Directory System fragment:
 ```cpp
<Directory Id="ProgramMenuFolder">
                <Directory Id="ApplicationProgramsFolder" Name="My UPC Name"/>
         </Directory>
   ```       
Into Shortcut Component fragment:
   ```cpp      
 <DirectoryRef Id="ApplicationProgramsFolder">
       <Component Id="StartMenuShortcut" Guid="19769afe-ec61-4fdc-9538-42c25a6e8fc8">
          <Shortcut Id="ApplicationStartMenuShortcut" 
                 Name="My UPC Game" 
                 Description="My UPC Game Description"
                 Target="[#Motor_2D.exe]"
                 WorkingDirectory="INSTALLFOLDER"
                 Icon = "icon.ico"/>  <!-- TODO 4: Implement Control Panel Icon + Shortcut Icons. -->
          <RemoveFolder Id="RemoveProgramsFolder" On="uninstall"/>
          <RegistryValue Root="HKCU" Key="Software\MyCompany\MyApplicationName" Name="installed" Type="integer" Value="1" KeyPath="yes"/>
       </Component>
   </DirectoryRef>
   
   ```
 Into Feature fragment:
   ```cpp
   <ComponentRef Id="StartMenuShortcut" />   
   ```
   
         
### TODO3 : Add Desktop Shortcut
#### Explication: 
Do the same as in the previous TODO, with the difference that the folder where the desktop shortcut will be instantiated does not need any extra directory.
#### Test:
If you run the .msi file generated after build WIX Setup project, the executable will be installed silently on your computer and the Desktop shortcut will be instanciated on your Computer Desktop.
#### Solution:

Into Directory System fragment:
 ```cpp
 <Directory Id="DesktopFolder" Name="My UPC Game" />
 
 ```
 Into Shortcut Component fragment:
 ```cpp
 <DirectoryRef Id="DesktopFolder">
       <Component Id="DesktopShortcut" Guid="5694ea64-2b00-4584-a671-d26134c1de38">
          <Shortcut Id="ApplicationDesktopShortcut" 
                 Name="My UPC Game" 
                 Description="My UPC Game Description"
                 Target="[#Motor_2D.exe]"
                 WorkingDirectory="INSTALLFOLDER"
                 Icon = "icon.ico"/>  <!-- TODO 4: Implement Control Panel Icon + Shortcut Icons. -->
          <RemoveFolder Id="RemoveDesktopFolder" On="uninstall"/>
          <RegistryValue Root="HKCU" Key="Software\MyCompany\MyApplicationName" Name="installed" Type="integer" Value="1" KeyPath="yes"/>
       </Component>
   </DirectoryRef>
   ```
 Into Feature fragment:  
```cpp
<ComponentRef Id="DesktopShortcut" />
```


### TODO4 : Implement control panel icon + exe project icon (shortcuts)
#### Explication:
For shortcut icons, you just need to modify shortcut components you created before adding the attribute "Icon" inside Shortcut element. For control panel icon, you need to import the icon.ico using the "Icon" element and adding a property to work property with the control panel of your computer.
#### Test:
If you run the .msi file generated after build WIX Setup project, the executable will be installed silently on your computer and you will find all the shortcuts and control panel with icon.
#### Solution:
 
 Into product fragment:
 ```cpp
 <Icon Id="icon.ico" SourceFile="assets\iconTwitter.ico" />
    <Property Id="ARPPRODUCTICON" Value="icon.ico" />
 ```
 Into Shortcuts fragment:
 ```cpp
 Icon = "icon.ico"/>
  ```
### TODO5 : Add UI Dialog theme (installDir)
#### Explication:
First, you have to add to the wixsetup project as a reference the "WixUIExtension" dll provided by Wix Toolset and once imported, you have to use the external element "UIRef" with the appropriate property to generate the chosen dialog theme (in this case, will use the InstallDir).
#### Test:
If you run the .msi file generated after build WIX Setup project, for the first time the dialog boxes will be executed and the user will be able to interact with the installer and its characteristics, such as the path where to install the program, accept the license, etc.
#### Solution:
Into product fragment:
 ```cpp
    <Property Id="WIXUI_INSTALLDIR" Value="INSTALLFOLDER" />
    <UIRef Id="WixUI_InstallDir" />
  ```
  
### TODO6 : Customize UI Dialog theme with bmp files
#### Explication:
You have to use the "WixVariable" element to be able to import the path of the bitmap files with the correct ID.
#### Test:
If you run the .msi file generated after build WIX Setup project, the dialog boxes will have been customized with the imported bitmap files.
#### Solution:
 Into product fragment:
 ```cpp
 <WixVariable Id="WixUIBannerBmp" Value="assets\ui_background.bmp" />
    <WixVariable Id="WixUIDialogBmp" Value="assets\ui_background.bmp" />
  ```
  
### TODO7 : Add Windows License into UI Dialog
#### Explication:
You need to do the same as previous TODO using "WixVariable" element and import License.rtf file
#### Test:
If you run the .msi file generated after build WIX Setup project, the dialog box where displays the Lore Ipsum language will be changed to the License you imported.
#### Solution:
Into product fragment:
 ```cpp
  <WixVariable Id="WixUILicenseRtf" Value="assets\License.rtf" />
 ```
### TODO8 : Uncomment game components (dll, assets. etc)
#### Explication:
Uncomment ComponentGroupRef to make enable the game components and dll's and enjoy the awesome game you have installed
#### Test:
If you run the .msi file generated after build WIX Setup project, the executable will work property.
#### Solution:
Into product fragment:
 ```cpp
  <ComponentGroupRef Id="HeatGenerated" />
   ```
   
 
## Acknowledgements and Webgraphy

[Application Packaging: Basics and Benefits](https://www.symantec.com/connect/articles/application-packaging-basics-and-benefits)

[Installation (computer programs)](https://en.wikipedia.org/wiki/Installation_(computer_programs))

[What are the benefits of a MSI installer over a standard setup.exe?](https://stackoverflow.com/questions/3976241/what-are-the-benefits-of-a-msi-installer-over-a-standard-setup-exe)

[What is the benefit and real purpose of program installation?
](https://stackoverflow.com/questions/22733889/what-is-the-benefit-and-real-purpose-of-program-installation)

[What installation product to use? InstallShield, WiX, Wise, Advanced Installer, etc
](https://stackoverflow.com/questions/1544292/what-installation-product-to-use-installshield-wix-wise-advanced-installer/1546941#1546941)

[Windows Installer](https://docs.microsoft.com/es-es/windows/desktop/Msi/windows-installer-portal)

[The Basics of Application Packaging:
Best Practices for Enabling Reduced Software Management Costs](https://www.dell.com/downloads/global/power/ps4q05-20050175-Kouletsis.pdf)

[Wix Resources](https://www.firegiant.com/wix/)

[WiX Toolset Manual Table of Contents](http://wixtoolset.org/documentation/manual/v3/)

[Wix Toolset 3.11 github](https://github.com/wixtoolset/wix3)

[Free software for Windows installers: NSIS vs. WiX? 
](https://stackoverflow.com/questions/458900/free-software-for-windows-installers-nsis-vs-wix)

[stackoverflow wix tags](https://stackoverflow.com/questions/tagged/wix?sort=newest)

[Free software for Windows installers: NSIS vs. WiX?
](https://www.add-in-express.com/creating-addins-blog/tag/wix/)

[What is MSI Installer?](https://smallbusiness.chron.com/msi-installer-56267.html)

[Windows Installer Wikipedia](https://en.wikipedia.org/wiki/Windows_Installer)

[MSI Format](https://whatis.techtarget.com/fileformat/MSI-Installer-package-Microsoft-Windows)

[Overview of the Windows Installer Technology](https://support.microsoft.com/en-ca/help/310598/overview-of-the-windows-installer-technology)

[What is the difference between client application and service application?](https://www.quora.com/What-is-the-difference-between-client-application-and-service-application)

[About the Windows Installer Service](http://www.installsite.org/pages/en/w2k_aboutmsi.htm)

[Application Packaging Training- AdminStudio, InstallShield Course](https://www.udemy.com/application-packaging-training-adminstudio-installshield/)

[Installation and Maintenance of Games](https://docs.microsoft.com/en-us/windows/desktop/dxtecharts/installation-and-maintenance-of-games)

[Windows Installer for Game Developers](https://docs.microsoft.com/en-us/windows/desktop/dxtecharts/windows-installer-for-game-developers)
