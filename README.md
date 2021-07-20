# DirDiff
Compares two folders and reports differing files.

## Version
- v1.0 - July 19, 2021
- macOS, Linux, Windows
- [MIT License](LICENSE)
- By Abe Pralle

# Installation
1. Install the [Rogue](https://github.com/AbePralle/Rogue) language.
2. Run `rogo` in this folder to compile **DirDiff**.
    - On macOS and Linux a launcher will be created here: `/usr/local/bin/dirdiff`.
    - On Windows the build process will print the necessary folder to add to the system PATH environment variable.

# Usage

## Syntax

    dirdiff [OPTIONS] <Folder-A> <Folder-B>

## Options

    --hidden, -a
      Show hidden files that begin with '.'.

    --help, -h, -?
      Show this help text.

    --expand, -e
      Show full contents of nested folders that only exist on one path.

## Output

    <   (Filename) - A file that is Folder A but not Folder B.
      > (Filename) - A file that is Folder B but not Folder A.
     *  (Filename) - A file that is in both folders but is not the same in both.

# Example

    Tools> cp -r DirDiff/ DirDiff2

    Tools> dirdiff DirDiff DirDiff2

    Tools> rm -rf DirDiff2/Build
    Tools> echo "# Some change" >> DirDiff2/Source/DirDiff.rogue
    Tools> echo "New File" > DirDiff2/NewFile.txt

    Tools> dirdiff DirDiff DirDiff2
    <   Build/
      > NewFile.txt
     *  Source/DirDiff.rogue

    Tools> dirdiff DirDiff DirDiff2 --expand
    <   Build/
    <   Build/DirDiff-macOS
    <   Build/DirDiff-macOS.cpp
    <   Build/DirDiff-macOS.h
      > NewFile.txt
     *  Source/DirDiff.rogue

