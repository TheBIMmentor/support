# support
Guides and Boilerplate code for starting your Revit Addins
1. boiler-plate contains code to get your first Revit Addin started
2. manifest-file has code you should copy and paste into your .addin file


See Instructions Below for a quick setup for your First Revit Addin
# Guides and Boilerplate code for starting your Revit Addins
1. Launch Visual Studio

2. Create a New Project
	Search for Class Library (.NET Framework), C# version in the templates.
	Set the .NET Framework to the latest version (e.g., 4.8.1).
	Click Create.
3. Add Revit References
	Right-click References → Add Reference.
	Add these files from your Revit install folder:
	RevitAPI.dll
	RevitAPIUI.dll
	Right-click each added Reference (or Alt + Enter on PC) → Properties → Set Copy Local to False.
4. Add Boilerplate Code
	Right-click your project → Add → Class → Name it.
	Copy and paste code from boilerplate-code

5. Set Debug and Build Settings
	Right-click your project → Properties.
	//Add to Post-Build Event Command Line (For Revit 2023)// 
	Copy "$(TargetDir)"."" "$(AppData)\Autodesk\Revit\Addins\2023\"

	Under Debug Settings >> Start External Program:
	C:\Program Files\Autodesk\Revit 2023\Revit.exe

6. Create an Add-In Manifest File
	Create a .addin file (New >> Application Manifest File >> NewFileName.addin) and paste this content:
	Copy and Paste code from Manifest-File

7. Build and Test
Build your project.
Open Revit, and your add-in should appear.
