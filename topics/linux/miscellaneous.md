## Topics
1. [Rsync](#rsync)
2. [Watch](#watch)

## **Rsync**
- Transfer files across different servers
- syntax: `rsync <other server>:<path from other server> <path from current server>`
    - `<server>`: kgcfddf043.india.machine.ti.com
    - `<path from other server>`: /home/abhinav/file1.txt
    - `<path in current server>`: /home/abhinav/folder1/file2.txt

## **Watch**
- watch command in Linux is used to execute a program periodically, showing output in fullscreen. 
- syntax: `watch -n 5 <command>`: watch the <command> output with interval of 5 seconds
- default frequency: 3 seconds
