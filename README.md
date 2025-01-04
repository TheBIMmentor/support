# support
Guides and Boilerplate code for starting your Revit Addins
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
	
 
 //Copy and paste this code into the class file//
 
using Autodesk.Revit.Attributes;
using Autodesk.Revit.DB;
using Autodesk.Revit.UI;
using Autodesk.Revit.UI.Selection;

namespace YourProjectName
{
    [Transaction(TransactionMode.Manual]
    public class ClassName : IExternalCommand
    {
        public Result Execute(ExternalCommandData commandData, ref string message, ElementSet elements)
        {
            UIApplication uiApp = commandData.Application;
            UIDocument uiDoc = uiApp.ActiveUIDocument;
            Document doc = uiDoc.Document;
            // Your code here
            return Result.Succeeded;
        }
    }
}


5. Set Debug and Build Settings
	Right-click your project → Properties.
	//Add to Post-Build Event Command Line (For Revit 2023)// 
	Copy "$(TargetDir)"."" "$(AppData)\Autodesk\Revit\Addins\2023\"

	Under Debug Settings >> Start External Program:
	C:\Program Files\Autodesk\Revit 2023\Revit.exe

6. Create an Add-In Manifest File
	Create a .addin file (New >> Application Manifest File >> NewFileName.addin) and paste this content:
	//Addin Manifest File//

	<?xml version="1.0" encoding="utf-16" standalone="no"?>
<RevitAddIns>
<<AddIn Type="Command">
	<Assembly>PrrojectName.dll</Assembly>
	<AddInId>UNIQUE-GU1D</AddInId>
	<FullClassName>ProjectName.ClassName</FullClassName>
	<Text>DescribeCommand</Text>
	<VendorId>CompanyName</VendorId>
	<VendorDescription>Company Details</VendorDescription>
</AddIn>
</RevitAddIns>

Replace placeholders (e.g., ProjectName, ClassName) with your details.


7. Build and Test
Build your project.
Open Revit, and your add-in should appear.
