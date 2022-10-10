## **Topics**
1. [FHS](#fhs)
2. [ls, cp & mv Commands](#ls-cp--mv-commands)
3. [Creating & Deleting files](#creating--deleting-files)
4. [cat, head, tails, less](#cat-head-tail-less)
5. [chmod](#chmod)

## **FHS**

- The file system in Linux follows a standard called File System Hierarchy (FSH). All kernels follow this standard.
- /root: topmost hierarchy, everything comes under this
- /home: each user has a folder under this folder where things like Documents, Downloads etc will be there
- /etc: system configuration files

### **Absolute & Relative paths:**

- abs path start with '/' (root)
- ~ is replaced by home abs path of home directory. Hence ~ is also abs

## **ls, cp & mv commands**

### **ls command**

- `ls` : list all files and dir
- `ls -l`: long listing (including file permissions, size, owner information as well)
- `ls -R`: recursively list all files and dir
- `ls -a`: list all files including hidden files (files starting with ‘.’)

### **cp command**

- Copy file
    - `cp /path/to/original/file /path/to/target_dir/<file_name>`
    - If you omit the `file_name` at the end the original file will be copied to `target_dir` with same name
    - If you give a `file_name` at the end, it will be copied with that name
    - advised to have trailing slash for the target path so as to make sure that is is a directory
- Copy folder
    - `cp -r /path/to/original_dir /path/to/target_dir/`
    - Here -r is required to copy all subfolders and files inside
    - advised to have trailing slash for the destination path so as to make sure that is is a directory
    - advised to not have a trailing slash for source path as the source could be a hardlink (which is not a directory and thus would give an error)
    - if `target_dir` exists, then `original_dir` will be copied inside `target_dir`: `target_dir` → `original_dir`
    - if `target_dir` does not exist, then `original_dir` contents will be copied inside `target_dir`: `target_dir` → contents of `original_dir`
    - if `target_dir` exists and you want the contents of `original_dir` to be copied, intead of whole directory, then:
        - `cp -r /path/to/original_dir/* /path/to/target_dir/`

### **mv command**

- Move file
    - `mv /path/to/original/file /path/to/target_dir/<file_name>`
    - If you omit the `file_name` at the end the original file will be moved to `target_dir` with same name
    - If you give a `file_name` at the end, it will be moved and renamed with that name
    - advised to have trailing slash for the target path so as to make sure that is is a directory
- Move folder
    - `mv /path/to/original_dir /path/to/target_dir/`
    - Here -r is not required
    - advised to have trailing slash for the destination path so as to make sure that is is a directory
    - advised to not have a trailing slash for source path as the source could be a hardlink (which is not a directory and thus would give an error)
    - if `target_dir` exists, then `original_dir` will be moved inside `target_dir`: `target_dir` → `original_dir`
    - if `target_dir` does not exist, then `original_dir` contents will be moved inside `target_dir`: `target_dir` → contents of `original_dir`
    - if `target_dir` exists and you want the contents of `original_dir` to be moved, intead of whole directory, then:
        - `mv /path/to/original_dir/* /path/to/target_dir/`
- Rename file/folder
    - `mv /home/user/file_or_dir /home/user/new_name_of_file_or_dir`

## **Creating & Deleting files**

### **Remove files and folders**

- `rmdir /path/to/dir`: This will delete the directory if it is emtpy only
- `rm /path/to/file`: delete file
- `rm -r /path/to/dir`: This will delete the directory even if not empty

### **Creating files & folders**

- `touch filename.ext`: creates file
- `mkdir /path/to/new/dir`: create directory

### **file & stat**

- `file /path/to/file`: tells the type of file
- `stat /path/to/file`: gives more info of file

## **cat, head, tail, less**

- `cat /path/to/file`: will print contents of file
    - `cat -n /path/to/file`: print line numbers on left
    - `cat file1 file2 > new_file`: concatentate contents of file1 & file2 to new_file
- `head -n5 /path/to/file`: print first 5 lines of file
- `tail -n5 /path/to/file`: print last 5 lines of file
- `less /path/to/file`: will display content page by page:
    - `f/space bar`: move forward one page
    - `b`: move backward one page
    - `up arrow`: move forward one line
    - `down arrow`: move downward one line
    - `q`: to quit
    - `/<pattern>`: search string pattern

## **chmod**

- file permissions are displayed in format: `[dl-]rwxrwxrwx`
    - if d at the start → directory, if l at the start → link, if - at the start → file
    - r → read, w → write, x → execute
    - first set of rwx: user permissions
    - second set: group permissions
    - third set: others permissions
- changing file permissions:
    - each rwx is in binary format: r(4), w(2), x(1): Hence rwx is 7, rw- is 6, r-x is 5, r-- is 4
    - `chmod 777 /path/to/file` rwx to user, group & others
    - `chmod 755 /path/to/file`: rwx to user, rx to group & others
    - `chmod u+rx /path/to/file`: add rx permission to user
    - `chmod g-x /path/to/file`: remove x permission for group
    - `chmod o=rx /path/to/file`: assign rx permission to others
    - `chmod a=rx /path/to/file`: assign rx permission to all