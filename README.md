<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>
This project provides a detailed walkthrough of the post-installation configuration of osTicket, an open-source help desk and ticketing system. After installing the core platform, there are several essential steps required to make the system functional, secure, and ready for real-world use by support teams. This project documents those steps and demonstrates how to configure osTicket for a realistic IT support environment.<br />




<h2>Environments and Technologies Used</h2>

- osTicket (Help Desk Ticketing System)
- System Administration
- Microsoft Azure (Cloud computing)
- Microsoft Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> 
- Windows Server 2022

<h2>Post-Install Configuration Objectives</h2>

- Adding a New "Master Admin" role
- Adding a New "System Administrators" Department
- Adding a New "Level II Support" Team
- Allowing Non-registered Users to Create Tickets
- Adding New Agents
- Setting Agent's Passwords
- Adding Service Level Agreements (SLAs)

<h2>Configuration Steps</h2>


###  -Adding a New "Master Admin" role

Now that osTicket is successfully installed from scratch,  it is time to do some configuration and system administration work. To start this off, we will create a new Role in osTicket called "Master Admin". This will be the highest level administrator that has every single permission available to them. Roles are used to determine an Agent's permissions. Generally, most Agents will not have every single permission as the Master Admin does.

1. Open `http://localhost/osTicket/scp/logs.php` in a web browser, enter the correct credentials

2. Navigate to `Agents` > `Roles` > `(+) Add New Role`

3. In the `Definition` tab:
    - In the **Name:** field, enter the desired role. In this case, it is `Master Admin`
    - Optionally, add any desired details regarding the new role in the __*Internal Notes*__ field

4. In the `Permissions` tab, give all available permissions to the Master Admin:
    - ✅ `Assign — Ability to assign tickets to agents or teams`
    - ✅ `Close — Ability to close tickets`
    - ✅ `Create — Ability to open tickets on behalf of users`
    - ✅ `Delete — Ability to delete tickets`
    - ✅ `Edit — Ability to edit tickets`
    - ✅ `Edit Thread — Ability to edit thread items of other agents`
    - ✅ `Link — Ability to link tickets`
    - ✅ `Mark as Answered — Ability to mark a ticket as Answered/Unanswered`
    - ✅ `Merge — Ability to merge tickets`
    - ✅ `Post Reply — Ability to post a ticket reply`
    - ✅ `Refer — Ability to manage ticket referrals`
    - ✅ `Release — Ability to release ticket assignment`
    - ✅ `Transfer — Ability to transfer tickets between departments`

<img width="970" height="461" alt="image" src="https://github.com/user-attachments/assets/4ee6050e-5e6f-486f-b322-c81e7f8df434" />



###  -Adding a New "System Administrators" Department

Each Agent is appointed a specific department which is determined by their assigned role within the helpdesk. For now, we'll just create a "System Administrators" department where the Master Admins will be designated. Various other settings such as email settings, service level agreements (SLAs), and managers can also be configured in the `Departments` tab.

1. Navigate to `Agents` > `Departments` > `(+) Add New Department`

2. In the **Name:** field, enter `System Administrators`

3. Scroll to the bottom of the page and click the orange `Create Dept` button

<img width="970" height="936" alt="image" src="https://github.com/user-attachments/assets/c88d9844-59b6-4b71-9122-45c4f509eb52" />


###  -Adding a New "Level II Support" Team

 Teams enable cross-departmental collaboration by aggregating skilled agents from various units. This structure facilitates the creation of specialized groups. For instance, you can develop a help topic related to a specific product and assign it to a team of agents with expertise in that product. In this demonstration, we'll create a "Level II Support Team" to illustrate this concept.

1. Navigate to `Agents` > `Teams` > `(+) Add New Team`

2. In the **Name:** field, enter `Level II Support`

3. At the bottom of the page, click the orange `Create Team` button

<img width="970" height="685" alt="image" src="https://github.com/user-attachments/assets/06e7e74e-6358-4287-a292-ad207fab9bbd" />


###  -Allowing Non-registered Users to Create Tickets

Out-of-the-box installations of osTicket require users to be registered and logged-in before they can create tickets. Since this isn't always ideal, the setting regarding this functionality needs to be adjusted.

1. Navigate to `Settings` > `Users` > Tick ✅ `Require registration and login to create tickets`

2. At the bottom of the page, click the orange `Save Changes` button

<img width="970" height="692" alt="image" src="https://github.com/user-attachments/assets/63229b69-6b37-4260-ab92-03734210821e" />


###  -Adding New Agents

Next, we'll proceed to create Agents. Agents  are the helpdesk staff responsible for resolving tickets. Each Agent is assigned a primary department and role for tickets within their designated area. Agents can be granted access to multiple departments, with potentially different roles in each. The Access, Permissions, and Teams tabs are used to adjust access levels, manage permissions, and assign teams for each staff member.

1. Navigate to `Agents` > `Agents` > `(+) Add New Agent`

2. In the `Account` tab, fill out the **Name:**, **Email Address:**, and **Username:** fields for the particular Agent being added. Do the same for any desired settings in the `Access` and `Permissions` tabs as well

3. At the bottom of the page, click the orange `Create` button

4. Repeat these steps until as many Agents as desired have been added

> 
> While creating an administrator-level Agents (e.g. System Administrators, Managers), permit them expanded access to the Support department so that they are able to assign tickets to support-level employees.

<img width="970" height="928" alt="image" src="https://github.com/user-attachments/assets/8eb6f4f1-de1a-421c-90af-a32ce4bb2bd6" />


<img width="970" height="448" alt="image" src="https://github.com/user-attachments/assets/5b606dd4-5a07-4f2d-bc8c-52858812d2d2" />


###  -Setting Agent's Passwords
1. In the Admin panel of osTicket, navigate to `Agents` > `Agents` > and then select that Agent that needs their password set
   
2. Under the **Authentication** section, click `Set Password`
   
3. Uncheck `Send the agent a password reset email`
   
4. In the `New Password` and `Confirm Password` fields, enter a matching secure password and then click the `Update` button
   
5. Verify that the `Require password change at next login` is unchecked

> 
> The steps above outline how an admin would manually set an Agent's password. However, the two boxes that were left unchecked are alternative methods for the Agent to set their own password instead.

<img width="970" height="753" alt="image" src="https://github.com/user-attachments/assets/0baff260-a53a-4e8b-8314-140e1dca0d74" />


###  -Adding Service Level Agreements (SLAs)

SLA (Service Level Agreement) Plans define the expected resolution time for specific ticket types. Each SLA incorporates a schedule and a grace period. For instance, in our example, the SEV-A (Severity A) SLA operates on a 24/7 schedule with a one-hour grace period. This structure ensures clear expectations for ticket resolution timeframes.

1. Navigate to `Manage` > `SLA` > `(+) Add New SLA Plan`

2. Fill out the information in accordance to the SLA plan of choice

3. At the bottom of the page, click the orange `Add Plan` button

<img width="970" height="673" alt="image" src="https://github.com/user-attachments/assets/0f52e0d7-2ecd-4025-8095-71b8d555d368" />


###  -Adding Help Topics

Help Topics facilitate ticket categorization for users. For example, we can create a "Business Critical Outage" topic, which could be used for scenarios such as customers being unable to access mobile banking services. This categorization streamlines the ticket management process and prioritization.

1. Navigate to `Manage` > `Help Topics` > `(+) Add New Help Topic`

2. In the **Topic:** field, enter the relevant information for the topic of choice

3. At the bottom of the page, click the orange `Add Topic` button

<img width="970" height="642" alt="image" src="https://github.com/user-attachments/assets/e652be0e-30da-4fcf-ad35-65597aff1aac" />

<br><div align="center">


