# Table of Contents:
 - [The Technical Interview Process](#Home-Chef-Tech-Candidate-Interview-Process)
 - [Our Interview Philosophy](#Home-Chef-Technical-Interview-Philosophy)
 - [Interview Prep Guide](#Candidate-Technical-Interview-Prep-Guide)
 - [Interview Setup Guide](#Candidate-Technical-Interview-Setup-Guide)
    - [Mac Setup Instructions](#Mac-Setup) **TO DO BEFORE INTERVIEW**
    - [Windows Setup Instructions](#Windows-Setup) **TO DO BEFORE INTERVIEW**
 - [Helpful Debugging Commands](#Helpful-Debugging-Commands)

---

*This repo is designed for candidates currently in the interview process with Home Chef. If you stumbled across this guide and think interviewing with us might be fun, please reach out to `hr@homechef.com`.*

---

# The Technical Interview Process

Our goal is to ensure you have a great candidate experience while moving through our interview process. On average, our process takes two weeks to complete. Occasionally steps are adjusted/added/removed, but typically the interview is as follows:

 1. Phone call with recruiter or engineering manager - .5 hours
 2. Behavioral interview with 2 Home Chef engineers - 1.5 hours
 3. Technical interview pairing with 2 Home Chef engineers on a real-life ticket - 2 hours
 4. Hiring decision is made within ~72 hours of the technical interview

If you are not sure where you are in this process or it has been an extended period of time since you last heard from us, please reach out to `hr@homechef.com`

# Our Interview Philosophy

During the technical interview, our goal is to see what it is like to work with you. You may not complete the exercise in full, and that’s perfectly fine. We have specifically designed our interview to better understand how you think and what it would be like to work with you &mdash; in something close to the environment that we would share if you were hired.\

## Pairing

Our technical interview involves pairing with two of our engineers and working through a ticket we've completed recently. Our definition of pairing means you are leading the session. The Home Chef Engineers are there to help you succeed by providing the necessary context, available as a resource to ask questions, and can help you with any code syntax. We want you to be as vocal as you can throughout the interview. Take us into your thought process by sharing how you will approach the problem, articulating tradeoffs, and why you are writing the code you are writing. Remember the objective of this interview is to learn what it is like to work with you. Our goal is to create an environment where you feel confident to best display your skills, can understand what it is like to work on our real code base, and do not feel like you are racing against the clock. 

# Technical Interview Prep Guide

At Home Chef our tech stack is a mix of React, Redux, HTML, CSS (Tailwind), HAML/Rails views, and JavaScript on the front end. We use a Ruby on Rails back end with a PostgreSQL database. We don't expect you to be an expert in these things.

Our technical interview is designed so you can make progress on it regardless of your specific technical background or level of experience. That being said, familiarity with the concepts and tools below may be helpful during the technical interview:
  - Basic CRUD app functionality
  - Interacting with APIs (making GET/POST requests)
  - React and React Hooks, including state management

# Interview Setup Guide
### Mac Setup

#### To complete before the interview:
1. Install [VS code](https://code.visualstudio.com/Download).
2. Add/install Microsoft's "[Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)" extension.

#### To complete along with your interviewer:
1. Create ssh config file: `touch ~/.ssh/config`
    Note: If you get the error "No such file for directory," create the directory by running `mkdir ~/.ssh`, then re-run the above command.
2. Your interviewer will send you some connection information to paste into this config file. Open it up, paste the connection info, then save. Example:
    ```
    Host hc-interview
      HostName EC2_INSTANCE_URL_GOES_HERE
      User candidate
      LocalForward 3000 localhost:3000
      LocalForward 3001 localhost:3001
    ```
3. Open VS Code, then Command + Shift + P and enter `Remote-SSH: Connect to Host`
4. Select `hc-interview`. A new VS Code tab will open and ask you to enter a password in the dropdown. The password is `candidate`.
5. Select `Open Folder` from the left side of the screen.
6. Select `/home/candidate/interview-internal-apps-2022/` from the dropdown. You will be asked to enter the password again: `candidate`
7. You should now be able to see the files of the codebase on the left side of the screen. Any code changes you make and save, your interviewers will be able to see.

### Windows Setup

#### To complete before the interview:
1. Install [VS code](https://code.visualstudio.com/Download).
2. Add/install Microsoft's "[Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)" extension.

#### To complete along with your interviewer:
1. Create ssh config file: `type null >> ~/.ssh/config`
    Note: If you get the error "The system cannot find the path specified," create the directory by running `mkdir ~/.ssh`, then re-run the above command.
2. Your interviewer will send you some connection information to paste into this config file. Open it up, paste the connection info, then save. Example:
    ```
    Host hc-interview
      HostName EC2_INSTANCE_URL_GOES_HERE
      User candidate
      LocalForward 3000 localhost:3000
      LocalForward 3001 localhost:3001
    ```
3. Open VS Code, then press `F1` and enter `Remote-SSH: Connect to Host`
4. Select `hc-interview`. A new VS Code tab will open and ask you to enter a password in the terminal. The password is `candidate`.
5. Select `Open Folder` from the left side of the screen.
6. Select `/home/candidate/interview-internal-apps-2022/` from the dropdown. You will be asked to enter the password again: `candidate`
7. You should now be able to see the files of the codebase on the left side of the screen. Any code changes you make and save, your interviewers will be able to see.

If your Windows machine doesn't have an OpenSSH compatible SSH client, follow this guide to install one via Windows Settings: (Note: This is not typical. Try running setup without this step.)
   - Install [an OpenSSH compatible SSH client](https://aka.ms/vscode-remote/ssh/supported-clients)

# Disconnecting After the Interview
Simply exit the VS Code terminal, and you will be disconnected from the SSH client.

# Helpful Debugging Commands

- To run the Rails console:

```docker exec -it $( docker ps | grep homechef_mealhand | awk "{print \$1}" | head -n 1 ) rails c```

- To attach a shell to the mealhand container in order to use `binding.pry`:

```docker attach $( docker ps | grep homechef_mealhand | awk "{print \$1}" | head -n 1```
