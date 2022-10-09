### Setup local and remote
This is needed only once on a system
1. Type: `ssh-keygen' in cmd. This will create 'id_rsa.pub' file in C:\Users\abhinav\.ssh directory
2. Copy contents of this file.
3. Go to github->settings->ssh keys-> add 'ssh key'->paste here and give it a name

### Config commands
- Print config file contents: `git config --global --list`


### Proxy settings
- Setting proxy:
    ```
    git config --global https.proxy=https://
    git config --global http.proxy=http://
    ```
- Removing proxy:
    ```
    git config --global --unset https.proxy
    git config --global --unset http.proxy
    ```