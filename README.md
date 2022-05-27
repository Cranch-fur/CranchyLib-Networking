# CranchyLib-Networking
### Small & Useful C# Library For Basic Networking :diamond_shape_with_a_dot_inside:
**Platform:** .NET Framework 4.8
> :grey_question: DLL Can Be Moved To Older Versions Of .NET Framework If Needed!

**License:** General Public License
> :white_check_mark: Feel Free To Share & Edit This Library, There's No Restrictions! 

____

## Documentation & Examples
### 1) Compile / [Download Precompiled DLL](https://github.com/Cranch-fur/CranchyLib-Networking/releases/tag/Release) & Include It in To .NET Framework Project
### 2) Add "using" statement in to your .cs file
```c#
using CranchyLib.Networking;
```

### CranchyLib-Networking - List Of What You Can Use
**Different Types Determination:**
- [X] 👽 → Extension
- [X] :star: → Function
- [X] :star2: → Async Function

**Main Class:** Networking
- `IsJson` 👽[string]
- `IsBase64` 👽[string]
- `E_StatusCode`
- `SE_ContentType`
- `SE_UserAgent`
- **Request**
    - `Get` :star:
    - `Get_Async` :star2:
    - `Post` :star:
    - `Post_Async` :star2:
    - `Download` :star:
    - `Download_Async` :star2:
- **Utilities**
    - **Hashing**
        - `E_HashAlgorithm`
        - `GetByteArrayHash` :star:
        - `GetStringHash` :star:
    - **Windows**
        - `SE_WinGuides`
        - `SE_WinFolder`
        - `GetFolderPathFromGuide` :star:

____

### Simple GET Request
```c#
string[] headers = new string[]
{
    $"User-Agent: {Networking.SE_UserAgent.Opera_Windows}",
    "Custom-Header: Example"
};

var request = Networking.Request.Get_Async("https://google.com", headers);
Console.WriteLine($"Status Code: {(int)request.Result.Item1} [{request.Result.Item1}]\n" +
                  $"Content-Type: {request.Result.Item2.Get("Content-Type")}\n" +
                  $"Content: {request.Result.Item3}");
```
**REQUEST HEADERS:**

![GETRequest_Headers](https://i.imgur.com/EQFgqOq.png "GETRequest_Headers")

**RESULT:**
```cmd
Status Code: 200 [OK]
Content-Type: text/html; charset=UTF-8
Content: <!doctype html>...
```

____

### Downloading The Files
```c#
var download = Networking.Request.Download_Async("https://i.imgur.com/nfnaz4M.jpeg",
                                                 Networking.Utilities.Windows.SE_WinFolder.Downloads);

Console.WriteLine($"Success?: {download.Result.Item1}\n" +
                  $"Downloaded File Path: {download.Result.Item2}");
```

**RESULT:**
```cmd
Success?: True
Downloaded File Path: C:\Users\Cranch\Downloads\nfnaz4M.jpeg
```

____

### Validating That String is JSON
```c#
string json = ...
Console.WriteLine( json.IsJson() );
```

**RESULT: True**
```json 
{"Name": "Johny"}
``` 

**RESULT: True**
```json
["Cookie", "Jar"]
```

**RESULT: False**
```json
{"Name": "Johny"}}
```

**RESULT: False**
```json
{Lorem Ipsum}
```

____

### Hashing The String / Byte Array
```c#
string text = "Hello, World!";
Console.WriteLine($"SHA512 (Default): {Networking.Utilities.Hashing.GetStringHash(text)}\n" +
                  $"MD5: {Networking.Utilities.Hashing.GetStringHash(text, Networking.Utilities.Hashing.E_HashAlgorithm.MD5)}");
```

**RESULT**
```
SHA512 (Default): N015SpXNz9izWZMYX++bo2jxYNja9DLQi6nx7R5avmzGkpHg+i/gAGpSVw7xjBne9OYXwzzlLvCm5fvjGMsDhw==
MD5: ZajifYh5KDgxtmS9i38K1A==
```
