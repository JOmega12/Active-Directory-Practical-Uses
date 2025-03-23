# Active-Directory-Practical-Uses

<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>


<h1>Active Directory Practical Uses</h1>
This tutorial outlines the practical use cases for Active Directory(AD) such as enabling/disabling accounts, account lockouts, configuring Group Policy Object (GPO) to an Organizational Unit(OU)
<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Remote Desktop Connection
- Azure Virtual Machine
  -  DC-1 and Client-1 Setup

<h2>Prequisites</h2>

- Before diving into the practical use cases for the Active Directory, we first need to have these projects learned and set up:
  - <a href="https://github.com/JOmega12/Active-Directory-Setup-with-Virtual-Machines">Active Directory Setup With Virtual Machines</a>
  - <a href="https://github.com/JOmega12/Active-Directory-Deployment-and-Configuration">Active Directory Deployment And Configuration </a>
  - <a href="https://github.com/JOmega12/Active-Directory-Generating-Users">Active Directory Generating Users </a>

<h2> Objectives</h2>

- Learn about the capabilities of administrators within Active Directory
- Learn about the challenges of users connected to the domain and how it is resolved

<h2>Scenarios/ Practical use cases</h2>

<h3>Configuring Lockout Policy</h3>

<b>Situation: </b>
- When unauthorized users try to access user accounts, we want to create a lockout policy for all users and computers in the domain.

<b>Steps: </b>

- So, in DC-1 open the start windows and right click RUN then type `gpmc.msc` in search box to open Group Policy Management(GPM)
![typeGPM](https://github.com/user-attachments/assets/7c9d8392-bd5b-4b83-95be-252986296206)

- In GPM click on Forest > Domains -> Default Domain THEN
- Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Account Policies -> Account Lockout Policy
![HowToAccountLockout](https://github.com/user-attachments/assets/0d98a828-fb49-4d9f-8f56-f46458c45033)
  
- In Account Lockout Policy, there is the `Account Lockout Threshold` and set it to 5 for this examples (usually other organizations have their own policy, but in this case we will do 5)
  
![lockoutAT5](https://github.com/user-attachments/assets/2f8fe74a-0ab8-4462-a8f5-8dc1e9938cb3)

- In for lockout duration, set it to 30minutes
  
![lockoutattemptMin](https://github.com/user-attachments/assets/00ad8f5c-e895-4a64-b87a-e780e46cb5c0)

- Then you will have this policy here:

![overall](https://github.com/user-attachments/assets/562124da-79d4-488a-9e83-d88370ab646c)

<b>Result</b>
- As the Domain Administrator, we have created a policy where if a user has attempted to enter a password incorrectly, it will lock itself out
- This is similar to day-to-day life where users would forget their logins and ask an administrator for a reset of their password

<h3>Dealing with Locked Accounts</h3>

<b>Situation: </b>
- A user cannot remember their password and has failed to login 5 times. They come to you and ask to unlock their account and give them a new password

<b>Steps: </b>
- Log into DC-1 and pick a random user to lock out (In this case it is Ben Cole)

![NameOFUser](https://github.com/user-attachments/assets/bece04e7-cd9e-4dec-872e-d73c781ac48f)

- Attempt to login 5 times with bad password

![LockoutAttempt](https://github.com/user-attachments/assets/8cc1a9ce-4ec4-4869-9600-9d5e63b957a4)

- Observe that the account has been locked

![obnserveLockoutAccount](https://github.com/user-attachments/assets/7dd5f23d-421d-4c5b-a25f-6b5431f038d6)

- In ADUC, find the person my right clicking in forest

![findINADUC](https://github.com/user-attachments/assets/ab70e381-0caf-43d3-84c6-3df130ae5b8a)

- Unlock Password
- Reset Password

![resetPassword](https://github.com/user-attachments/assets/6b5becca-103e-4455-94b8-d9b695d2873d)

- Attempt to login with new password (hint: the new password is `Password2`)

<b>Result</b>
- The result is that you gave the user a new password for them to access their account and after unlocking a locked account

<h3>Enablic/Disabling Accounts</h3>

<b>Situation: </b>
- A user has resigned from the company and your manager has been tasked to deactivate their account
- However, a security leak has happened and they are attempting to use the resigned user's account to hack into the company and you are tasked to observe

<b>Steps: </b>
- Go to DC-1 and in the same account Deactivate the User (in this case Ben Cole)

![NameOFUser](https://github.com/user-attachments/assets/048b8aef-43ac-4034-8399-3c2fd8978a97)

- then on start search `eventvwr.msc`

![eventViewer](https://github.com/user-attachments/assets/e930f3a2-b39e-4b19-a71a-1da862115d52)

- then windows log > security > right click `Find` on ben.cole and Observe Failure to logon

![observeFailureToLogon](https://github.com/user-attachments/assets/4f518e41-539a-4789-8d24-7fa43f14e218)

- Then go to ADUC and disable the account

![disable](https://github.com/user-attachments/assets/f024f219-3d94-4e0a-ab9d-4bf77c6b42ff)

<br />
<h2>Conclusion</h2>

<p>These occurrences might/ will happen in day-to-day work, especially when users in an organization forget their passwords and lock themselves out.</p>
<p>Or, find that you might need to look up and observe why a user's account is failing.</p>


<br />
