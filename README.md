# 🛠️ Day 3 – Setting Up Shared Resources in Active Directory

As part of the Chicago Bears' new Arlington headquarters IT infrastructure rollout, your task as a System Administrator is to configure shared network resources that will support collaboration between departments. These resources include shared folders for file storage, shared printers, and automated drive mappings. The goal is to ensure that only authorized users have access to specific resources using Active Directory groups and permissions.
This lab focuses on security, organization, and usability — all critical for enterprise environments.

### 🧪 Lab Tasks
#### 1. Create Department Shared Folders

•	Log into the file server with a domain admin account.

•	Create shared folders:

  o	C:\Shares\Admin
  
  o	C:\Shares\HR
  
  o	C:\Shares\IT
  
•	Configure share permissions:

  o	Share each folder with its respective AD security group.
  
  o	Allow “Full Control” to department groups only.
  
•	Set NTFS permissions:

  o	Remove "Everyone"
  
  o	Add the appropriate department security group.
  
  o	Apply Modify or Read rights as needed.

#### 2. Set Up Shared Printers (Optional but recommended)
•	Install or add a network printer to the file server.

•	Right-click printer > Properties > Sharing tab > Share the printer.

•	Set permissions to allow specific department security groups only.

#### 3. Map Network Drives Using GPO

•	Open Group Policy Management on the Domain Controller.

•	Create a new GPO (e.g., Map_HR_Drive) and link it to the department's OU.

•	Go to:

  o	User Configuration > Preferences > Windows Settings > Drive Maps

•	Add a New Mapped Drive:

  o	Location: \\FileServerName\HR

  o	Drive Letter: H:

  o	Label: HR Shared Folder

•	Set targeting to apply only to HR users (using Item-level targeting or group filtering).

#### 4. Test Access

•	Log in with a test account from each department.

•	Confirm:

  o	Correct network drive mapping.
  
  o	Proper folder access (can’t access other departments).
  
  o	Optional: printer is visible if assigned.

### 💻 Tech Stack

Windows Server (2019+)	File & Print Server, Active Directory host

Active Directory (AD)	User & Group Management

Group Policy (GPO)	Network drive mapping, resource access

NTFS & Share Permissions	File-level and network-level access control

SMB (Server Message Block)	Network file sharing protocol

Optional: PowerShell	Automation and scripting

### 🧾 Summary of Lab Goals

✅ Create and secure shared folders for each department

✅ Ensure proper permissions are applied via NTFS and share settings

✅ Use GPO to automate drive mapping for users

✅ (Optional) Share and secure department printers

✅ Validate that access control works based on AD security groups

✅ Establish a clean and secure resource-sharing structure for the new HQ
