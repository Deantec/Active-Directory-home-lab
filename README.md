# Active Directory Home Lab: Windows Server 2025

A hands-on lab where I built a small Active Directory domain and practiced the account tasks a help desk handles every day.

**Full write-up with screenshots:** [Active_Directory_Home_Lab.pdf](Active_Directory_Home_Lab.pdf)

## Environment
- **Server:** Windows Server 2025 (evaluation) virtual machine
- **Role:** Active Directory Domain Services (AD DS), promoted to a domain controller
- **Domain:** `lab.local` (NetBIOS name: LAB)
- **Tools:** Server Manager, Active Directory Users and Computers (ADUC), PowerShell

## What I did

### 1. Installed AD DS and created the domain
Added the Active Directory Domain Services role in Server Manager, promoted the server to a domain controller, created a new forest (`lab.local`), and restarted.

### 2. Created an organizational unit, user, and group
In ADUC I created:
- An OU named **Lab User**
- A user account named **Test User**
- A security group named **Help Desk**

### 3. Added the user to the group
Opened the **Help Desk** group, went to the **Members** tab, and added Test User.

### 4. Reset a user password
Right-clicked Test User, chose **Reset Password**, and set a new password. I verified the change with PowerShell:

```powershell
Get-ADUser testuser -Properties PasswordLastSet | Select Name, PasswordLastSet
```

### 5. Disabled and re-enabled an account
Used **Disable Account** on Test User (the icon changed to show it was disabled), then **Enable Account** to restore it.

## What I learned
- How a domain controller, domain, OU, user, and group relate to each other
- Where help desk tasks like password resets and account enable/disable are done
- Why group membership matters for managing access
- How to confirm a change with PowerShell instead of assuming it worked

## Next steps
- Join a Windows 11 VM to the domain and sign in as the test user
- Practice account unlocks and group-based access
