# Background

![Alt text](YottaDB-VSCode.PNG?raw=true "YottaDB VSCode")

This repo helps YottaDB developers better develop routines from within Visual Code Studio. Each save of a routine file from within Visual Code studio will cause the routine to load and compile within YottaDB

# Requirements

[Visual Code Studio](https://code.visualstudio.com/)

# Extensions utilised

[Code Runner VSCode extension](https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner)

[Remote SSH extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)

# Setup

1) Install VSCode
2) Add the **Remote SSH** extension - File - Preferences - Extensions - Remote SSH
3) Once installed, a green button should appear to the bottom left of the VSCode window labelled **Open a Remote Window** Click on this and select **Connect to Host**
4) Select **Add New SSH Host**
5) Enter **ssh username@192.168.240.1 -A** Where username is the username under which yottadb was installed and 192.168.240.1 is the IP address of the server running YottaDB
6) A pop up box should appear titled **Host added!** Click **Connect**
7) Select **Linux** as the platform for the remote host and then proceed to enter the password
8) Once connected, you should be able to **Open Folder** and navigate to the **.yottadb** folder in the user's home directory.
9) Navigate to the routines directory for the YottaDB installation e.g. **/root/.yottadb/r1.30_x86_64/r**
10) You should then be able to see the YottaDB routines listed and be able to double click a routine for editting
11) On the server running YottaDB, add the ydbcompil executable file and allow it to be accessed via the system path i.e. move the file to **/usr/local/bin** Ensure that ydb is also accessable via the system path i.e. **ln -s /usr/local/yottadb/ydb /usr/local/bin/ydb**
12) Back in VSCode Studio, Click File - Preferences - Extensions and add **Run On Save** by **pucelle** (Please note that there are a number of extensions with the same name. Take time to add the correct one)
13) Click on the cog icon for the extension and then **Extension Settings**
14) Click **Edit in settings.json**
15) Copy and paste the text from [here](https://raw.githubusercontent.com/RamSailopal/YottaDB-VSCode/main/settings.json)

    The key entries are the ones below:

        "code-runner.executorMap": {
    
            "mumps": "ydbcompil '$fileNameWithoutExt'"
    
        },
    
        "code-runner.executorMapByFileExtension": {
    
            ".m": "ydbcompil '$fileNameWithoutExt'"
    
        },
    
        "files.associations": {
    
           "*.m": "mumps"
    
        }
    
17) Click on the play icon on the top right hand side of the code window. This will compile the YottaDB mumps code. The ydbcompil executable will automatically run to compile the code Any compilation errors will show in the terminal window.

# Additional Optional Setup

**The M/MUMPS/Cache language syntax highlighting and basic formatting** extension by **David Silin** can also by added by following the same procedure as above to add syntax highlighting when editting routines.

https://marketplace.visualstudio.com/items?itemName=dsilin.mumps


