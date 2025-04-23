# Example PDM multipackage repo

A simple repo demonstrating how sources can be used to handle multiple packages.

## Structure

- master-package - the main package we are bulding depending on package1 and package2
- package1 - another package we are building depending on package2
- package2 - another package we are building 
- packages - the folder for our artifacts


## How it works

- In the root folder pyproject definition we add a source for the folder packages
- We also add 2 scripts to build package 1 and 2 and then also add a pre-hook on build and install to call them
- A local source/index is a wheel filled folder

Notes: 
- git automatically detects binaries so .gitattributes should not be needed for the .whl 
- git also handles well a few MBs so git-lfs is not needed for the .whl (those are not "large files at all")

### Testing
- install PDM >= 2.22.3

- go into master-package and do `pdm install` which will build the packages and install master-package

### Updating when package1 or package2 were changed
- change version of package1 or package2
- `pdm update`

## TODO 
- find out if we can skip building the distro files and just use the folder 

