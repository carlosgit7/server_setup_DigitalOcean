# MacOS Development Setup

## Install Homebrew

[Homebrew](https://brew.sh/) is the missing package manager for macOS, we are going to use it to install everythinf in the setup.

1. Open the terminal
  1.1. In Finder (`CMD + Spacebar`), type Terminal
2. Paste this code `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

## Install Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/)  is a lightweight but powerful source code editor which runs on your desktop and is available for Windows, macOS and Linux. It comes with built-in support for JavaScript, TypeScript and Node.js and has a rich ecosystem of extensions for other languages (such as C++, C#, Java, Python, PHP, Go) and runtimes (such as .NET and Unity).

### From Terminal

1. Open the terminal
2. Install with this command: `brew cask install visual-studio-code`
3. Open with `code`

### From Website

Download and install from [here](https://code.visualstudio.com/)

## C# Development (.NET Core SDK)

[.NET Core](https://dotnet.microsoft.com) is a cross-platform version of .NET for building websites, services, and console apps. We are going to use it for our C# Development.

1. Open the terminal
2. Install with this command: `brew cask install dotnet-sdk`

## Install NodeJS for JavaScript Development

[Node.js](https://nodejs.org/en/) is a JavaScript runtime built on Chrome's V8 JavaScript engine.

1. Open the terminal
2. Install NVM with `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash`
3. Install Node.js with this command: `nvm install node`

## Install Yarn as Package Manager

[Yarn](https://yarnpkg.com/lang/en/) is a  Fast, reliable, and secure dependency management.

1. Open the terminal
2. Install with `curl -o- -L https://yarnpkg.com/install.sh | bash -s -- --nightly`