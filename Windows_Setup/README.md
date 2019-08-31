# Windows Development Setup

## Install Chocolatey

[Chocolatey](https://chocolatey.org/) is the package manager for Windows.

1. Search in the Start Button for ***cmd***
2. Rigth Click with the mouse and open as Administrator
3. Accept Dialog Box
4. Paste this code `@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"`

## Install Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/)  is a lightweight but powerful source code editor which runs on your desktop and is available for Windows, macOS and Linux. It comes with built-in support for JavaScript, TypeScript and Node.js and has a rich ecosystem of extensions for other languages (such as C++, C#, Java, Python, PHP, Go) and runtimes (such as .NET and Unity).

1. Open the ***cmd*** as administrator
2. Install with this command: `choco install vscode`
3. Open with Code

## C# Development (.NET Core SDK)

[.NET Core](https://dotnet.microsoft.com) is a cross-platform version of .NET for building websites, services, and console apps. We are going to use it for our C# Development.

1. Open the ***cmd***
2. Install with this command: `choco install dotnetcore-sdk`

## Install NodeJS for JavaScript Development

[Node.js](https://nodejs.org/en/) is a JavaScript runtime built on Chrome's V8 JavaScript engine.

1. Open the ***cmd***
2. Install with this command: `choco install nodejs.install`

## Install Yarn as Package Manager

[Yarn](https://yarnpkg.com/lang/en/) is a  Fast, reliable, and secure dependency management.

1. Open the ***cmd***
2. Install with this command: `choco install yarn`

## Install Git

[Git](https://git-scm.com/) is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. 

1. Open the ***cmd***
2. Install with this command: `choco install git.install`