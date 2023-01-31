# memo
SSD=`/bin/df / | /usr/bin/tail -1 | /bin/sed 's/^.* \([0-9]*\)%.*$/\1/'`
HDD=`/bin/df /depot | /usr/bin/tail -1 | /bin/sed 's/^.* \([0-9]*\)%.*$/\1/'`
if [ $SSD -gt 0 ] && [ $HDD -gt 0 ]; then
        echo
        /bin/df -h / | /usr/bin/tail -1 | awk '{print $3"/"$2}' | echo -e "\e[31m[Disk alert] SSD FreeSize : $((100-$SSD))% ($(cat))\e[m"
        /bin/df -h /depot | /usr/bin/tail -1 | awk '{print $3"/"$2}' | echo -e "\e[31m[Disk alert] HDD FreeSize : $((100-$HDD))% ($(cat))\e[m"
        echo
fi

PS1='[\t] \[\e[1;32m\]\u@\h\[\e[0m\]:\[\e[1;34m\]\w\$\[\e[0m\] '
