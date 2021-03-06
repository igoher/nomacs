# Releasing 🍸

## Windows

- Update Version Number (in `CMakeLists.txt` *and* `nomacs.rc`)
- Update translations
- Tag commit - Title: version (e.g. 3.2)
- Add changelog to Release on https://github.com/nomacs/nomacs/releases
- Batch build
  - nomacs x64
  - nomacs x86
  - nomacs-plugins x64
  - nomacs-plugins x86
- Run _INSTALL -> Project Only -> `Build only INSTALL`_ for every solution
- you need the WiX toolset [1]
- clean plugin folders in nomacs.x64 and nomacs.x86 (i.e. remove OpenCV dlls)
- increment installer version number in `nomacs-setup.wxs`: <?define ProductVersion = "3.7.5"?>
- double-click `make-installer.bat`
- check if the newly created installer `noamcs-setup.msi` is signed
- upload `nomacs-setup.msi` to http://download.nomacs.org/htdocs/

### nomacs portable

- copy the installer/nomacs.x64/ folder to projects/nomacs/releases and name it `nomacs-3.x.x`
- copy all files from portable-files to this new folder
- zip the `nomacs-3.x.x folder`
- back-up the installer folder to the release folder
- upload the `nomacs-3.x.x.zip` to http://download.nomacs.org/htdocs/portable
- update the index.html accordingly
- update http://download.nomacs.org/htdocs/versions/index.html

## READ release

- Update Version Number in ReadFramework (in CMakeLists.txt and rdf.rc)
- Update version number in json for updated module in ReadModule

### nomacs

- make-installer.bat rename `nomacs-setup.msi` to `ReadFramework.msi`
- nomacs-setup.wxs comment default nomacs, uncomment read build
- nomacs-setup.wxs update ProductVersion

- make-installer.bat: Check TU-code-signng.p12 path
- for code signing add /p pwd
- upload the repository folder to \\hermes\ftp\staff\read

- alternative version: use signtool sign /n "Technische Universität Wien"  /t http://timestamp.digicert.com .\ReadFramework.msi
- encoding must be Central European OEM852
- save certificate in certificate store

## Links
[1] http://wixtoolset.org/releases/
