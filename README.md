# Candidate Tech Interview Guide

# Mac Setup:
- Install [VS code](https://code.visualstudio.com/Download)
- Add/install Microsoft's "[Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)" extension
- Create ssh config file *if one does not already exist*
	- Navigate to root directory '~'. `cd ~`
    If `.ssh` **DOES NOT** exist:
    - In root directory (~), `mkdir .ssh` 
    - `ls .ssh`
    - inside `~/.ssh`, `touch config`
	If `.ssh` **DOES** already exist, proceed to next steps:
- open config file
- paste connection info into the `config` file and save config file. Your interviewer will send you the connection info, but see example below:
  ex.
    Host hc-interview
      HostName EC2_INSTANCE_URL_GOES_HERE
      User candidate
      LocalForward 3000 localhost:3000
      LocalForward 3001 localhost:3001
    
- Open VS Code
- Command + Shift + P and enter `Remote-SSH: Connect to Host`
- Select `hc-interview`
- A new VS Code tab will open and ask you to enter a password in the dropdown. The password is `candidate`
- Once entered, select `Open Folder` from the left side of the screen
- Select `/home/candidate/interview-internal-apps-2022/` from the dropdown
- You will be asked to enter the password again. `candidate`
- You should now be able to see the files and code base we will be working in on the left side of the screen. Any code changes you make and save, your interviewers will be able to see. 

# Windows Setup:
- Install [VS code](https://code.visualstudio.com/Download)
- Add/install Microsoft's "[Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)" extension
- Create ssh config file *if one does not already exist*
	- Navigate to root directory 'C:\Users\Username'. `cd ~`
    If `.ssh` **DOES NOT** exist:
    - In root directory (~), `mkdir .ssh` 
    - `ls .ssh`
    - inside `~/.ssh`, `touch config`
	If `.ssh` **DOES** already exist, proceed to next steps:
- open config file
- paste connection info into the `config` file and save config file. Your interviewer will send you the connection info, but see example below:
  ex.
    Host hc-interview
      HostName EC2_INSTANCE_URL_GOES_HERE
      User candidate
      LocalForward 3000 localhost:3000
      LocalForward 3001 localhost:3001

- Open VS Code
- Press `F1` and enter `Remote-SSH: Connect to Host`
- Select `hc-interview`
- A new VS Code tab will open and ask you to enter a password in the terminal. The password is `candidate`
- Once entered, select `Open Folder` from the left side of the screen
- Select `/home/candidate/interview-internal-apps-2022/` from the dropdown
- You will be asked to enter the password again. `candidate`
- You should now be able to see the files and code base we will be working in on the left side of the screen. Any code changes you make and save, your interviewers will be able to see. 

If Windows Machine doesn't have an OpenSSH compatible SSH client, follow this guide to install one via Windows Settings Note: This is not typical. Try running set up without this step:
   - Install [an OpenSSH compatible SSH client](https://aka.ms/vscode-remote/ssh/supported-clients).

# Disconnecting after interview:
- Simply exist the VS Code terminal, and you will be disconnected from the ssh client.

# Useful commands:

- To run Rails Console:
```docker exec -it $( docker ps | grep homechef_mealhand | awk "{print \$1}" | head -n 1 ) rails c```

- To attach a shell to the mealhand container in order to use ```binding.pry```:
```binding.pry:
docker attach $( docker ps | grep homechef_mealhand | awk "{print \$1}" | head -n 1```
