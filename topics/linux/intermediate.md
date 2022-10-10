## Topics
1. [Find](#find)
2. [Grep](#grep)
3. [Tr](#tr)

## **Find**

- syntax: `find /path/to/directory -name 'search_string'`
- `-iname`: case insensitive name search
- `-path`: path search
- `-ipath`: case insensitive search
- `-type`: filter type of file (`f`: file, `d`: dir, `l`: link)
- `-user`: filter user
- `-group`: filter group
- `-maxdepth`: max depth of search
- `-mindepth`: min depth of search
- `-maxdepth 1 -mindepth 1`: to search only in children of given dire

## **Grep**

- syntax: `grep "search_string" filename` (search ‘search_string’ in file)
- filename or filepattern can be given. Ex: `grep 'finance' report*.csv` will search ‘finance’ in all files starting with report
- `search_string` can be posix basic regex ([https://www.grymoire.com/Unix/Regular.html](https://www.grymoire.com/Unix/Regular.html)). basic regex is diff from regex used in python re
- `-E`: (extended regex) with this flag the `search_string` can be the regex normally used in python
- Example: count files present in a given directory recursively using grep
    - `ls -lR output | grep -E '[-][rwx-]{9}' | wc -l`:
        - Here `ls -lR` will print all files/dir recursively
        - regex will search for file permissions that start with `'-'` (those are files)
        - `wc -l` will count the output
    - `ls -lR output | grep '[-][rwx-]\{9\}' | wc -l`
        - This does the same thing as above, just the regex syntax for basic reg in unix is diff
- `-i`: case insensitive search
- `-w`: check full words
- `-A <n>`: print matched lines along with n lines before it
- `-B <n>`: print matched lines along with n lines after it
- `-C <n>`: print matched lines along with n lines around it
- `-r`: search recursively
- `-v`: invert the result (not operation)
- `-c`: count the number of lines which matched
- `-l`: return only files names which matched

## **Tr**

- syntax: `tr [options] 'set1' ['set2']` (replace set1 characters with set2 characters at the same position)
- `tr '\n' ' '`: replace `\n` with space i.e print everything in one line
- `tr ' ' '\n'`: replace space with `\n` i.e print in new line after space
- `tr ‘a-z’ ‘A-Z’`: convert to uppercase