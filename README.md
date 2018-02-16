# Dealing with Files and Directories

`FileAndDirs: ` is a member of the APLTree library: a collection of classes etc. that aim to support the Dyalog APL programmer. 

The members of the APLTree library solve many every-day problems any programmer might run into. All those members are tagged as "dyalog" and "apltree".


## Overview

With version 15.0 Dyalog has introduced several new system functions that make it much easier to write platform independent code when it comes to dealing with files and directories.

However, there are some gaps left: copying and moving files for example, or a recursive directory listing.

`FilesAndDirs` aims to close these gaps: it offers the same functionality for Windows, Linux and Mac OS.

## Slashes and backslashes

Under Windows the backslash `\` character is used as delimiter. Under Linux and Mac OS it is the `/` character. However, Windows is willing to accept the `/` rather than the `\` in most cases. The easiest way therefore seems to be to use `/` everywhere.

Almost. As it turns out there are several occasions when one still has to settle for the `\`: 

 * Calls to third party software.
 * Calls to .NET assemblies.
 * Setting properties like `Directory` in the `FileBox` GUI objects.
 * ... (there are most likely more!)

For that reason since version 1.3 all methods of `FilesAndDirs` accept both the `/` and the `\` characters as directory seperators but when returning a result that is a path name then it will always make sure that the correct separator for the given operating system is used.

That's the reason why the class offers method like `Exists`, `CreateFile`, `DeleteFile` and even `NNAMES` and `NCREATE`: they don't do much more than their system function equivalents except that they normalize any filenames and directory names.

Of course this means that `FilesAndDirs` cannot deal under Linux and Mac OS with names that contain a `\`, but if you try to write platform independent code then you must not do this anyway, and most likely you shouldn't even if you don't.

## Methods 

```
  Cd
  CheckPath
  CopyTo
  CopyTree
  CreateFile
  CurrentSep
  DeleteFile
  Dir
  EnforceBackslash
  EnforceSlash
  Exists
  GetNewLineCharsFor
  GetTempFilename
  GetTempPath
  IsDir
  IsFile
  IsSymbolicLink
  ListDirs
  ListFiles
  MkDir
  MoveTo
  MoveTree
  NCREATE
  NNAMES
  NormalizePath
  PolishCurrentDir
  PWD
  RmDir
  Version
```

`FilesAndDirs` needs version 15.0 Unicode of Dyalog APL, or better.