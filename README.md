# DDiff
Compares two folders and reports differing files.

## Version
- v1.1 - July 19, 2021
- macOS, Linux, Windows
- [MIT License](LICENSE)
- By Abe Pralle

# Installation
1. Install the [Rogue](https://github.com/AbePralle/Rogue) language.
2. Run `rogo` in this folder to compile **DDiff**.
    - On macOS and Linux a launcher will be created here: `/usr/local/bin/ddiff`.
    - On Windows the build process will print the necessary folder to add to the system PATH environment variable.

# Usage

## Syntax

    ddiff [OPTIONS] <left-folder> <right-folder>

## Options
    --expand, -e
      Show full contents of nested folders that only exist on one path.

    --hidden, -a
      Show hidden files that begin with '.'.

    --help, -h, -?
      Show this help text.

    --left, -l
      Show files that are unique or different in the left folder. If neither
      --left nor --right are specified then differences in both folders are shown.

    --right, -r
      Show files that are unique or different in the right folder. If neither
      --left nor --right are specified then differences in both folders are shown.

## Output

    <   (Filename) - A file that is in the left folder but not the right folder.
      > (Filename) - A file that is in the right folder but not the left folder.
     *  (Filename) - A file that is in both folders but has differing content.

# Example

    Tools> cp -r DDiff/ DDiff2

    Tools> ddiff DDiff DDiff2

    Tools> rm -rf DDiff2/Build
    Tools> echo "# Some change" >> DDiff2/Source/DDiff.rogue
    Tools> echo "New File" > DDiff2/NewFile.txt

    Tools> ddiff DDiff DDiff2
    <   Build/
      > NewFile.txt
     *  Source/DDiff.rogue

    Tools> ddiff DDiff DDiff2 --expand
    <   Build/
    <   Build/DDiff-macOS
    <   Build/DDiff-macOS.cpp
    <   Build/DDiff-macOS.h
      > NewFile.txt
     *  Source/DDiff.rogue

    Tools> ddiff DDiff DDiff2 --right
      > NewFile.txt
     *  Source/DDiff.rogue

