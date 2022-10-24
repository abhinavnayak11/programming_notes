## **Python Installation (Windows)**
1. Install Python from official website
2. Add “C:\Users\Nayak\AppData\Local\Programs\Python\Python310” (folder location of python.exe) and “C:\Users\Nayak\AppData\Local\Programs\Python\Python310\Scripts” (folder location of pip.exe) to the path in enviroment variables
3. Move these paths to the the top
4. Go to “Manage app execution alias” and turn off App installer for python.exe and python3.exe

## **Virtual Environments**

### **Creating Virtual Environment**
1. Create a new folder where you will store all the virtual environments
2. `cd C:\Users\Nayak\Environments` (path to the new folder)
3. `python -m venv ml` (ml is the new virtual env)
4. `python -m venv ml --system-site-packages` (if you want all the libraries from the system to be there in new env)

### **Activating env**
- cmd: `path/to/env/folder/Scripts/activate.bat`
- git bash: `source /path/to/env/folder/Scripts/activate`
- unix: `source /path/to/env/folder/bin/activate.csh`

### **Deactivating**
- `deactivate`