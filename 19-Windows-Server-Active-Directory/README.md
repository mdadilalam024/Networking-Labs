
# Lab 19: Windows Server 2022 – Active Directory Domain Services (AD DS)

## Objective

Install and configure Active Directory Domain Services (AD DS) on Windows Server 2022, create a domain, manage users and groups, and join a Windows client computer to the domain.

## Tools Required

- Windows Server 2022
- Windows 10 or Windows 11 Client VM
- Oracle VirtualBox or VMware
- Minimum 2 Virtual Machines
- Internet connection for initial setup and updates (optional)

## Lab Environment

| Device | Operating System | Role |
|---|---|---|
| Server VM | Windows Server 2022 | Domain Controller |
| Client VM | Windows 10/11 | Domain Client |

Both virtual machines must be connected to the same VirtualBox Internal Network or Host-Only Network.

## Network Configuration

### Server Configuration

| Setting | Value |
|---|---|
| Computer Name | DC01 |
| IP Address | 192.168.10.10 |
| Subnet Mask | 255.255.255.0 |
| Preferred DNS | 192.168.10.10 |
| Domain Name | adil.lab |
| NetBIOS Name | ADIL |

### Client Configuration

| Setting | Value |
|---|---|
| Computer Name | CLIENT01 |
| IP Address | 192.168.10.20 |
| Subnet Mask | 255.255.255.0 |
| Preferred DNS | 192.168.10.10 |

Default Gateway can be left blank if the lab network does not require external connectivity.

## Step 1: Configure Windows Server

1. Start Windows Server 2022.
2. Rename the computer to DC01.
3. Restart the server.
4. Open Network Connections.
5. Configure a static IP address.

PowerShell commands to rename the server:

```powershell
Rename-Computer -NewName "DC01" -Restart
```

After restart, configure the static IP through the network adapter settings.

## Step 2: Install Active Directory Domain Services

1. Open Server Manager.
2. Click Manage.
3. Select Add Roles and Features.
4. Select Role-based or feature-based installation.
5. Select the local server.
6. Select Active Directory Domain Services.
7. Click Add Features.
8. Continue through the wizard.
9. Click Install.

## Step 3: Promote Server to Domain Controller

After installation:

1. Open Server Manager.
2. Click the notification flag.
3. Select Promote this server to a domain controller.
4. Select Add a new forest.
5. Enter the root domain name:

```text
adil.lab
```

6. Select DNS Server and Global Catalog.
7. Set a Directory Services Restore Mode (DSRM) password.
8. Continue through the wizard.
9. Complete prerequisite checks.
10. Click Install.

The server will restart after promotion.

## Step 4: Verify Active Directory

After restarting:

1. Sign in using the domain administrator account.
2. Open Server Manager.
3. Go to Tools.
4. Open Active Directory Users and Computers.

Verify that the domain adil.lab is available.

## Step 5: Create an Organizational Unit

1. Open Active Directory Users and Computers.
2. Right-click the domain.
3. Select New → Organizational Unit.
4. Create an OU named:

```text
IT-Department
```

## Step 6: Create a Domain User

1. Open the IT-Department OU.
2. Right-click and select New → User.
3. Enter the following details:

| Setting | Value |
|---|---|
| First Name | Adil |
| User Logon Name | adil.user |
| Password | Set a lab-only password |

Complete the wizard.

For this lab, use a strong password and do not reuse your personal password.

## Step 7: Configure Client DNS

Start the Windows 10/11 client VM.

Configure:

- IP Address: 192.168.10.20
- Subnet Mask: 255.255.255.0
- Preferred DNS Server: 192.168.10.10

The client must use the Domain Controller's DNS server to locate the domain.

## Step 8: Join Client to Domain

On CLIENT01:

1. Open Settings.
2. Go to System → About.
3. Open Advanced system settings or Domain or workgroup settings.
4. Select Change.
5. Select Domain.
6. Enter:

```text
adil.lab
```

7. Enter domain administrator credentials when prompted.
8. Wait for the welcome message.
9. Restart the client.

## Step 9: Verify Domain Membership

On the client, open Command Prompt:

```cmd
whoami
systeminfo
ipconfig /all
```

Verify domain membership.

You can also run:

```cmd
nltest /dsgetdc:adil.lab
```

A successful response should identify the domain controller.

## Step 10: Test Domain User Login

1. Sign out from CLIENT01.
2. Select Other User.
3. Enter the domain account:

```text
ADIL\adil.user
```

4. Enter the lab password.
5. Verify that the domain user can sign in.

## Important Active Directory Concepts

- Active Directory: Microsoft's directory service for centralized identity and resource management.
- Domain Controller: Server that hosts Active Directory Domain Services.
- Domain: Logical administrative boundary for users, computers and resources.
- Organizational Unit (OU): Container used to organize directory objects.
- Domain User: User account managed by Active Directory.
- Group Policy: Used to centrally manage user and computer settings.
- DNS: Helps clients locate domain controllers and other domain services.

## Important Commands

```powershell
ipconfig /all
nslookup adil.lab
nltest /dsgetdc:adil.lab
whoami
systeminfo
```

## Troubleshooting

If the client cannot join the domain:

- Check that both VMs are on the same virtual network.
- Verify the server's static IP address.
- Set the client DNS address to 192.168.10.10.
- Check DNS service and domain controller status.
- Verify that the domain name is correct.
- Check connectivity using ping.
- Ensure the server and client clocks are synchronized.
- Check firewall and network connectivity.

## What I Learned

- Windows Server 2022 administration.
- Active Directory Domain Services.
- Domain Controller installation.
- DNS integration with Active Directory.
- Organizational Unit creation.
- Domain user management.
- Windows client domain joining.
- Centralized identity management.
- Active Directory troubleshooting.

## Practical Evidence

Add your own screenshots after completing the lab:

- Windows Server 2022 desktop.
- AD DS role installation.
- Domain Controller promotion.
- Active Directory Users and Computers.
- Created Organizational Unit.
- Created domain user.
- Client domain join confirmation.
- Successful domain user login.

## Author

Md Adil Alam

GitHub: https://github.com/mdadilalam024
