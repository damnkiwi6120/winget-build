This branch is a trial of running on the runner Windows 2025, and it is currently abandoned due to no idea how to solve "UAP.props 10.0.22000 could not be located" proplem.  

For a full log, the workflow URL is here:
https://github.com/damnkiwi6120/winget-build/actions/runs/13083474874

---

# winget-build

Original: [jedieaston/winget-build](https://github.com/jedieaston/winget-build)  
This hard fork merges [PR#6, created by @cadwal](https://github.com/jedieaston/winget-build/pull/6), from that repo and adds my own changes.  

---

[![build-it](https://github.com/damnkiwi6120/winget-build/actions/workflows/build.yml/badge.svg)](https://github.com/damnkiwi6120/winget-build/actions/workflows/build.yml)

Fresh, nightly builds of winget.

Want to see what the latest cool feature is on the [winget](https://github.com/microsoft/winget-cli) master branch? This repository compiles a daily build for you to use. Stability is not guaranteed, although I can guarantee you won't get support from MS ;)

To use it, download the [latest](https://github.com/damnkiwi6120/winget-build/releases/latest) copy of wingetdev.zip, extract it, and run `wingetdev.exe`! Note that all of the files in that folder have to stay together, so if you have a .bin folder you like to put loose executables in, keep them together.

Or, if you're feeling speedy, just use the quick script inside this repo from PowerShell: `iwr -useb https://github.com/damnkiwi6120/winget-build/raw/main/Install.ps1 | iex`

No dependencies should be necessary outside of the 2015-2019 Visual Studio Redistributables, which you probably have. If you don't have them, just run `winget install -s winget Microsoft.VC++2015-2019Redist-x64`.


winget is [licensed under the MIT license](https://github.com/microsoft/winget-cli/blob/master/LICENSE). 
