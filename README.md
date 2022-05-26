# CranchyLib-Networking
### Small & Useful C# Library For Basic Networking :diamond_shape_with_a_dot_inside:
**Platform:** .NET Framework 4.8
> :grey_question: DLL Can Be Moved To Older Versions Of .NET Framework If Needed!

**License:** General Public License
> :white_check_mark: Feel Free To Share & Edit This Library, There's No Restrictions! 

____

## Documentation & Examples
### 1) Compile / [Download Precompiled DLL](https://google.com) & Include It in To .NET Framework Project
### 2) Add "using" statement in to your .cs file
```c#
using static CranchyLib.Networking.Main;
```

### CranchyLib-Networking - List Of What You Can Use
- `IsJson`
- `IsBase64`
- **Networking**
    - `E_StatusCode`
    - `SE_ContentType`
    - `SE_UserAgent`
    - **Request**
        - `Get` 
        - `Get_Async`
        - `Post`
        - `Post_Async`
        - `Download`
        - `Download_Async`
- **Utilities**
    - **Windows**
        - `SE_WinGuides`
        - `SE_WinFolder`
        - `GetFolderPathFromGuide` 

____

### Sample GET Request
```c#
string[] headers = new string[]
            {
                $"User-Agent: {Networking.SE_UserAgent.Opera_Windows}",
                "Custom-Header: Example"
            };
            
var request = Networking.Request.Get_Async("https://google.com", headers);
Console.WriteLine($"Status Code: {(int)request.Result.Item1}\n\n" +
                  $"Content-Type: {request.Result.Item2.Get("Content-Type")} \n\n" +
                  $"Content: {request.Result.Item3}");
```
#### How our Request Looks In Fiddler (Web Debugging Tool)
![GET_Fiddler](https://cranchpalace.info/github/assets/cranchylib/networking/GET_Fiddler.png "GET_Fiddler")
#### What Do We See In Our Program (Content Stripped From Screenshot)
![GET_ConsoleOutput](https://cranchpalace.info/github/assets/cranchylib/networking/GET_ConsoleOutput.png "GET_ConsoleOutput")

____

### Check if String is JSON
```c#
string example = "{\"Name\": \"Johny\"}";
Console.WriteLine(example.IsJson());
```
**RESULT:** True | This is default JObject
```c#
string example = "[\"Cookie\", \"Jar\"]";
Console.WriteLine(example.IsJson());
```
**RESULT:** True | This is default JArray
```c#
string example = "{\"Name\": \"Johny\"}}";
Console.WriteLine(example.IsJson());
```
**RESULT:** False | There's 2 brackets at the end!

____

### Let's Download A File!
```c#
var download = Networking.Request.Download_Async("https://cranchpalace.info/github/assets/cranchylib/networking/DOWNLOAD_Cozy.png", Utilities.Windows.SE_WinFolder.Downloads);
Console.WriteLine(download.Result);
```
![DOWNLOAD_Result01](https://cranchpalace.info/github/assets/cranchylib/networking/DOWNLOAD_Result01.png "DOWNLOAD_Result01")
![DOWNLOAD_Result02](https://cranchpalace.info/github/assets/cranchylib/networking/DOWNLOAD_Result02.png "DOWNLOAD_Result02")
