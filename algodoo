#!/bin/bash

progName="algodoo"
progRealPath="/usr/share/$progName/app"
progHome="$HOME/.$progName"
progBin="Algodoo.exe"

unset WINEPREFIX
if [ ! -d $progHome ] ; then
   mkdir -p $progHome

   # User folders
   find $progRealPath -maxdepth 1 -type d -exec cp -r {} $progHome/ \;

   # User configs
   find $progRealPath -maxdepth 1 -type f -name "*.cfg" -exec cp {} $progHome/ \;

   # Read only files
   ln -s $progRealPath/*.{txt,dll,exe} $progHome
fi

# msvcp90 MUST be overriden https://www.reddit.com/r/linuxquestions/comments/6g077y/wine_error_class_not_registered/dqn9c8k/
export WINEDLLOVERRIDES="msvcp90=n,b"
wine $progHome/$progBin "$@"

