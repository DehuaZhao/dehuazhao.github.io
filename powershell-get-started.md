## Getting Started with Windows PowerShell

7/28/2016

This article helps you gettting started with Windows PowerShell if you found it acting werid. You probably were missing some steps.



## PowerShell website

https://msdn.microsoft.com/en-us/powershell



## Update PowerShell and help files

check powershell version, you can run

```powershell
$psversiontable
```

or

```powershell
$host
```

If you are on Windows 7 or 8.1, PowerShell v2.0 is pharpas what you have.

What you need to do, is download and install latest supported **Windows Management Framework**.

Visit https://msdn.microsoft.com/en-us/powershell and find **download WMF** button.

As at the time I write this, it would be WMF5.

```
$psversiontable

Name                           Value
----                           -----
PSVersion                      5.0.10586.117
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.10586.117
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

And then update help files

```powershell
update-help
```

P.S. If you tried some common command like `unlock-file .\example.ps1` or `wget [url]`, and error reported:

```powershell
unlock-file : The term 'unlock-file' is not recognized as the name of a cmdlet, function, script file, or operable program.
```

Chances are, you are running an old version.



## Enable script execution

The default execution policy on Windows PowerShell is **Restricted**.

Use **Set-ExecutionPolicy** to change the execution policy to **AllSigned** or **RemoteSigned**.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned
```

Or, you can unblock a script to run it without changing the execution policy:

```powershell
unlock-file .\example.ps1
.\example.ps1
```



## An Example

Right now, a book series called *You Don't Know JS* comes to my interest. And it's avaliable free at github. I want to download it's fist serie (containing 3 chapters) to local disk D:\

You can save the scripts into a *.ps1 file. Or you can type and run these in PS.


```powershell
for ($i=1; $i -le 3; $i++ )
{
    wget https://raw.githubusercontent.com/getify/You-Dont-Know-JS/master/up%20%26%20going/ch$i.md -o D:\YDKJS_I_ch$i.md
}
```

Note that this book series is orginally in plain text with *markdown* syntax marked-up. You might need a markdown reader or someting to read it in good formatting.
