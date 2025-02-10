This branch tries to use `default.run.shell` to setup the whole environment, which would erase the need to call vcvarsall.bat every time it needs.

However, during the trial, I have no idea how to handle special characters like spaces and quotes in cmd correctly.

I bypass this problem by migrating to pwsh across all steps, which is an aggresive step.

This fortunately bypass the problem, but it builds fail.

~~For future trials, if one knows how to deal with escaping special characters in cmd, it might be a chance to decouple the problem from pwsh.~~
~~Until then, the only problem needs to be solved would only be failures of building.~~

For a full log, the workflow URL is here: https://github.com/damnkiwi6120/winget-build/actions/runs/13126102506

### 2025/02/10 Update: It's concluded that this branch is abandoned.

The work to use default.run.shell and migrate to Powershell should be done together.  
The reason I want to use default.run.shell is that I don't have to run the script in every step.  
Powershell alone won't solve this problem if it's not used at default.run.shell.  
However, in the current state, it seems not possible due to the reason described [here](https://dotnetdevaddict.co.za/2016/03/17/powershell-vcvars-batch/), which is a blog written by [@mattleibow](https://github.com/mattleibow).

Using Powershell leads to fail builds, but using cmd to run the batch first and call pwsh afterwards does not work either.  
Either this is not supported, or I simply didn't figure out how to escape characters.  
No matter which answer is true, they all leads to unneccessarily poor readability.

If I want to. there's actually a solution, which is the action [ilammy/msvc-dev-cmd](https://github.com/marketplace/actions/enable-developer-command-prompt).  
Though, since I prefer first party solutions and there's [only actually three line to minimize](https://github.com/damnkiwi6120/winget-build/commit/5789f8780edd644e66d51af037d161053578f069), I decide to not use it.

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
