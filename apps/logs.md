grep DEBUG console-main.log | grep -oP '[a-z\.]+\.[A-Z][a-zA-Z0-9]*' | sort | uniq -c

grep INFO console-main.log | grep -oP '[a-z\.]+\.[A-Z][a-zA-Z0-9]*' | sort | uniq -c

grep INFO console-main.log | grep -oP '[a-z\.]+\.[A-Z][a-zA-Z0-9]*' | sort | uniq -c
