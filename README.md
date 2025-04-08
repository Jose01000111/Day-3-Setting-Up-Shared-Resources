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

  https://imgur.com/jebIUl2
  
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

https://imgur.com/9b1GmW9

•	Create a new GPO (e.g., Map_HR_Drive) and link it to the department's OU.

•	Go to:

  o	User Configuration > Preferences > Windows Settings > Drive Maps

https://imgur.com/0Ix9lj8

•	Add a New Mapped Drive:

https://imgur.com/FxvnaE3

  o	Location: \\FileServerName\HR

  o	Drive Letter: C:

https://imgur.com/s6as9fq

https://imgur.com/ieiaVKs

  o	Label: HR Shared Folder

•	Set targeting to apply only to HR users (using Item-level targeting or group filtering).

https://imgur.com/WG1Cp1B

#### Step 4: Ensure NTFS Permissions
Right-click the file Arlington_Heights_Construction_Plan.docx and select Properties.

https://imgur.com/1PaWAJ0

Go to the Security tab.

Click Edit to modify permissions.

Add the security group (e.g., HR_Group, ConstructionTeam).

https://imgur.com/WG1Cp1B

Remove "Everyone" if listed and set the appropriate permissions (e.g., Read or Modify).

Click Apply, then OK.

#### Step 5: Set Folder-Level Sharing Permissions
Right-click the folder (e.g., C:\Shared\HR) > Properties.

Go to the Sharing tab and click Advanced Sharing.

Check Share this folder.

https://imgur.com/siMvEbB

Test permissons for Operation.

https://imgur.com/4WXIjaK

#### Step 6: Access the Shared File from a Client
On a client PC, log in as a member of the security group that has been granted access.

Open File Explorer.

Access the shared file using the mapped drive (e.g., H:\Arlington_Heights_Construction_Plan.docx).

Alternatively, you can use the UNC path: \\fileserver\HR\Arlington_Heights_Construction_Plan.docx



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
