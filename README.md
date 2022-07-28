# Table of Contents:
 - [Home Chef Technical Interview Philosophy](#Home-Chef-Tech-Candidate-Interview-Process) 
 - Home Chef Tech Candidate Interview Process
 - Candidate Technical Interview Prep Guide
 - Candidate Technical Interview Setup Guide
    - Mac Interview Set Up Instructions Only *** TODO BEFORE INTERVIEW ***
    - Windows Interview Set Up Instructions Only *** TODO BEFORE INTERVIEW ***
 - Helpful Debugging Commands

---

*This repo is designed for candidate who are currently in process with Home Chef. If you stumbled across this interview and are curious about Home Chef and think interviewing with us might be fun please reach out to `hr@homechef.com`*

# Home Chef Tech Candidate Interview Process:

Our goal is to ensure you have a great candidate experience while moving through our interview process. On average our process takes two weeks to complete. Occasionally steps are adjusted/added/removed but typically the interview is as follows:

 1. Phone call with Recruiter or Engineering Manager - 5. hours
 2. Behavioral interview with 2 Home Chef engineers - 1.5 hours
 3. Technical interview pairing with 2 Home Chef engineers on a ticket we've completed in our production code base recently - 2 hours
 4. Hire or no hire decision is made within ~72 hours of the technical interview

If you are not sure where you are in this process or it has been an extended period of time since you last heard from us please reach out to `hr@homechef.com`

# Home Chef Technical Interview Philosophy:

During the technical interview our goal is to see what it is like to work with you. You may not complete the exercise in full, and that’s perfectly fine. We have specifically designed our interview to better understand how you think and what it’s would be like to work with you in something close to the environment that we would share if you are hired.  

We won't ask you a leetcode problem or to code merge sort or a red black tree from scratch. Our technical interview will involve you pairing with two of our engineers and working through a ticket we've complete on our internal apps team recently. Our goal is to give you enough time so you are able to ask questions, get the necessary context needed, and make progress on the problem, ideally, without feeling like you are racing against the clock. 

# Candidate Technical Interview Prep Guide:

At Home Chef our tech stack is a mix of React, Redux HTML, CSS (tailwinds), HAML/Rails Views, and JavaScript on the front end. We use a Ruby on Rails back end with a PostgreSQL database. We don't expect you to be an expert in these things.

Our technical interview is designed so you can make progress on it regardless of your specific technical background or level of experience. That being said, being familiar with the concepts and tools below may be helpful during the technical interview:
  - Basic Ruby on Rails CRUD app functionality
  - Interacting with API's (Making GET/POST requests)
  - React
  - React Hooks, specifically useState
  - Redux/State Management
  - Serializers

# Candidate Technical Interview Setup Guide:
# Mac Setup:

**TODO BEFORE THE INTERVIEW:**
- Install [VS code](https://code.visualstudio.com/Download)
- Add/install Microsoft's "[Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)" extension

**TODO WITH YOUR INTERVIEWER:**
- Create ssh config file *if one does not already exist*
	- Navigate to root directory '~'. `cd ~`
    If `.ssh` **DOES NOT** exist:
    - In root directory (~), `mkdir .ssh` 
    - `ls .ssh`
    - inside `~/.ssh`, `touch config`
	If `.ssh` **DOES** already exist, proceed to next steps:
- Open config file
- Paste connection info into the `config` file and save config file. Your interviewer will send you the connection info, but see example below:
  ex.
  ```Host hc-interview
    HostName EC2_INSTANCE_URL_GOES_HERE
    User candidate
    LocalForward 3000 localhost:3000
    LocalForward 3001 localhost:3001```
    
- Open VS Code
- Command + Shift + P and enter `Remote-SSH: Connect to Host`
- Select `hc-interview`
- A new VS Code tab will open and ask you to enter a password in the dropdown. The password is `candidate`
- Once entered, select `Open Folder` from the left side of the screen
- Select `/home/candidate/interview-internal-apps-2022/` from the dropdown
- You will be asked to enter the password again. `candidate`
- You should now be able to see the files and code base we will be working in on the left side of the screen. Any code changes you make and save, your interviewers will be able to see. 

# Windows Setup:
**TODO BEFORE THE INTERVIEW:**

- Install [VS code](https://code.visualstudio.com/Download)
- Add/install Microsoft's "[Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)" extension

**TODO WITH YOUR INTERVIEWER:**

- Create ssh config file *if one does not already exist*
	- Navigate to root directory 'C:\Users\Username'. `cd ~`
    If `.ssh` **DOES NOT** exist:
    - In root directory (~), `mkdir .ssh` 
    - `ls .ssh`
    - inside `~/.ssh`, `touch config`
	If `.ssh` **DOES** already exist, proceed to next steps:
- Open config file
- Paste connection info into the `config` file and save config file. Your interviewer will send you the connection info, but see example below:
  ex.
  ```Host hc-interview
    HostName EC2_INSTANCE_URL_GOES_HERE
    User candidate
    LocalForward 3000 localhost:3000
    LocalForward 3001 localhost:3001```

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
- Simply exit the VS Code terminal, and you will be disconnected from the ssh client.

# Helpful Debugging Commands:

- To run Rails Console:

```docker exec -it $( docker ps | grep homechef_mealhand | awk "{print \$1}" | head -n 1 ) rails c```

- To attach a shell to the mealhand container in order to use ```binding.pry```:

```docker attach $( docker ps | grep homechef_mealhand | awk "{print \$1}" | head -n 1```
