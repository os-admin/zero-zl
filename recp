#!/bin/bash
usage(){
   echo "recp [-d] <file list>
          -d   to stdout only"
    exit 0
}

if [ $# -lt 1 ]
then
usage
fi

#system Type
os=`uname -s`
case $os in
#Linux
        Linux)
                addCon="xclip -sel clip"
        ;;
#Macos
        Darwin)
                addCon="pbcopy"
        ;;
        *)
                echo -e "OS '$os' not suppose yet"
                exit 0
esac

#遍历文件打印
for i in $*
do
languageType=${i##*.} #文件类型决定注释
case $languageType in
 py | ruby | sh )
        commentType="#"
        ;;
#like c
  sql)
        commentType="--"
        ;;
   *)
       commentType="//"
        ;;
esac
        echo "$commentType $i"  
        cat $i
        echo -e "\n"
done | $addCon
