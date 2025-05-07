<p align="center">
<img src="https://i.imgur.com/pqTjnLb.png" alt="osTicket logo"/>
</p>

### Day 3 – Setting Up Shared Resources for Departments

With staff accounts active, team leads began requesting shared folders and printers so their departments could begin collaborating on site planning and logistics.

I created shared folders, configured NTFS and share permissions, deployed network printers, and used Group Policy Objects (GPOs) to automate access and drive mappings. (Used ChatGPT to confirm GPO best practices and avoid inheritance issues.)

### 🧪 Lab Tasks
#### 1. Create Department Shared 📂 Folders
I start by logging into the file server with a domain admin account. Then, I create shared folders for each department (Admin, HR, and IT) under C:\Shares\. After that, I set share permissions, giving each folder access to the respective AD security group with "Full Control" for the department's group only. I also remove "Everyone" from NTFS permissions and add the appropriate department group, applying "Modify" or "Read" rights as needed.

   <p align="center">
<img src="https://i.imgur.com/s6as9fq.png" alt="osTicket logo"/>
</p>

***

  <p align="center">
<img src="https://i.imgur.com/jebIUl2.png" alt="osTicket logo"/>
</p>

#### 2. Set Up Shared 🖨️ Printers (Optional but recommended)
Next, I install or add a network printer to the file server. I configure the permissions to allow only specific department security groups to access the printer, ensuring each department has dedicated printer access.

#### 3. Map 🌐 Network Drives Using GPO
I open Group Policy Management on the Domain Controller and create a new GPO (e.g., Map_HR_Drive) for the HR department. I navigate to User Configuration > Preferences > Windows Settings > Drive Maps and add a new mapped drive with the location \\FileServerName\HR and the drive letter C:. I set targeting to apply this mapping only to HR users using Item-level targeting or group filtering.

<p align="center">
<img src="https://i.imgur.com/9b1GmW9.png" alt="osTicket logo"/>
</p>

***

<p align="center">
<img src="https://i.imgur.com/0Ix9lj8.png" alt="osTicket logo"/>
</p>

***

<p align="center">
<img src="https://i.imgur.com/FxvnaE3.png" alt="osTicket logo"/>
</p>

***

<p align="center">
<img src="https://i.imgur.com/s6as9fq.png" alt="osTicket logo"/>
</p>

***


<p align="center">
<img src="https://i.imgur.com/ieiaVKs.png" alt="osTicket logo"/>
</p>

***


#### Step 4: Ensure 📂 NTFS Permissions
For files like Arlington_Heights_Construction_Plan.docx, I right-click and go to Properties > Security. I click "Edit" to add the correct security groups (e.g., HR_Group, ConstructionTeam), remove "Everyone," and set permissions to "Read" or "Modify" as needed.

<p align="center">
<img src="https://i.imgur.com/1PaWAJ0.png" alt="osTicket logo"/>
</p>

***

<p align="center">
<img src="https://i.imgur.com/i065ylv.png" alt="osTicket logo"/>
</p>

***

<p align="center">
<img src="https://i.imgur.com/WG1Cp1B.png" alt="osTicket logo"/>
</p>

***

#### Step 5: Set 📂 Folder-Level Sharing Permissions
I right-click the folder (e.g., C:\Shared\HR), go to Properties > Sharing tab, and select "Advanced Sharing." I check "Share this folder" and test the permissions to ensure only the correct department users can access it.

<p align="center">
<img src="https://i.imgur.com/siMvEbB.png" alt="osTicket logo"/>
</p>

***

<p align="center">
<img src="https://i.imgur.com/4WXIjaK.png" alt="osTicket logo"/>
</p>

***

### 💻 Technology Stack

#### Windows Server (2019+)	File & Print Server, Active Directory host

#### Active Directory (AD)	User & Group Management

#### Group Policy (GPO)	Network drive mapping, resource access

#### NTFS & Share Permissions	File-level and network-level access control

### 🎯 Goals Accomplished

#### ✅ Create and secure shared folders for each department

#### ✅ Ensure proper permissions are applied via NTFS and share settings

#### ✅ Use GPO to automate drive mapping for users

#### ✅ (Optional) Share and secure department printers

#### ✅ Validate that access control works based on AD security groups

#### ✅ Establish a clean and secure resource-sharing structure for the new HQ

#### ✅ Test Permissions
