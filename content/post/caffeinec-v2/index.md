---
title: "CaffeineC v2"
description: The first major update to CaffeineC
date: 2023-12-21T14:02:30+01:00
draft: true
image: cover.png
categories:
  - CaffeineC
tags:
  - programming
  - caffeinec
---

## Breaking changes
### Packages
Each CaffeineC file now has to start with the a the package name declaration.
```cffc
package somename;
```

## Most notable upgrades
### Fully working auto-install scripts
For MacOS and Linux systems you can use this simple command to install CaffeineC and any tools it might need:
```bash
curl https://raw.githubusercontent.com/vyPal/CaffeineC/master/install.bash | bash
```
For Windows, you can use this powershell script:
```ps1
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/vyPal/CaffeineC/master/install.ps1'))
```
### LLC and GCC swapped out for clang
The original versions of CaffeineC used the `llc` command from the llvm toolchain to compile llvm intermediate representation (LLVM-IR) to a object file, which was then linked by `gcc`. This approach worked well on linux, but wasnt ideal on windows, because llc had to be bundled with the compiler which took up a lot of storage. In v2.0.9 `llc` and `gcc` were replace by `clang` on windows only. In v2.0.11 `clang` adopted on linux and mcos as well.

### Projects
While not fully functional yet, CaffeineC now supports its own projects to more easily manage larger codebases. You can initialize a new project by running `CaffeineC init prjectname` which will create a new direcotry and some example files in it.

### MacOS builds
The GitHub Actions workflow that is used to build the linux and windows binaries also now builds a macos binary file, which can be installed using the same bash script as is used for linux.

### Imports
CaffeineC now supports easy importing of functions and classes from other CaffeineC files. For a function or class to be able to be imported from another file, you must prefix the decleration with the `export` keyword. This does not make any change in the functionality of the code. Then from another file you can use the `import` statement whith the relative or absolute path to the package.