## Task2

1) Analyze the structure of the /etc/passwd and /etc/group file, what fields are present in it, what users exist on the system? Specify several pseudo-users, how to define them?

The **/etc/passwd** and **/etc/group** files are essential configuration files in Unix-like operating systems, including Linux. They store information about users and groups on the system.

The **/etc/passwd** file contains information about user accounts on the system. Each line represents a user account and is structured as follows:

```bash
username:password:UID:GID:GECOS:home_directory:login_shell
```

- **username**: This is the user's login name.
- **password**: Historically, this field used to contain the encrypted password, but modern systems typically store a placeholder (usually an 'x' or '*') and store the actual password hash in the /etc/shadow file, which is only accessible by the root user.
- **UID** (User ID): A numerical value that uniquely identifies the user. It is used for permissions and resource allocation.
- **GID** (Group ID): The primary group to which the user belongs, identified by its numerical group ID.
- **GECOS** (General Electric Comprehensive Operating System): This field usually contains additional information about the user, such as their full name, office number, and phone number.
- **home_directory**: The path to the user's home directory.
- **login_shell**: The user's default login shell, which determines the command-line interface they use when they log in.

Some pseudo-users that you may find in the /etc/passwd file, which are not real users but serve specific purposes:

- **root**: The superuser or system administrator account.
- **nobody**: A low-privileged user account used for running certain system services.
- **daemon**: Another low-privileged account used for running system daemons or background services.
- **nfsnobody**: Used for NFS (Network File System) operations.

The **/etc/group** file contains information about user groups on the system. Each line in this file has the following structure:

```bash
group_name:password:GID:user_list
```

- **group_name**: The name of the group.
- **password**: Historically, this field used to contain the group password, but it is rarely used nowadays, and an 'x' or '*' is often found here.
- **GID** (Group ID): A numerical value that uniquely identifies the group.
- **user_list**: A comma-separated list of user accounts that belong to the group.

Some pseudo-groups that you may find in the **/etc/group** file:

- **root**: The root group, which typically includes only the root user.
- **adm**: A group used for system log files and monitoring access.
- **users**: A default group for regular user accounts.

To view the users and groups present on your system, you can use the following commands:

To list all users:

```bash
cat /etc/passwd | cut -d: -f1
```

To list all groups:

```bash
cat /etc/group | cut -d: -f1
```

![](https://i.imgur.com/efds70W.png)

---
2) What are the uid ranges? What is UID? How to define it?

User IDs (UIDs) are numerical identifiers assigned to each user account on a Unix-like operating system, including Linux. UIDs are used to uniquely identify users and are essential for access control and permission management. The range of UIDs is defined to ensure proper system functioning and to avoid conflicts. There are three main UID ranges:

**System User IDs (0-999)**: UIDs in this range are reserved for system users and services. These accounts are typically used for system-related tasks and should not be used for regular user accounts. The most critical system user is the root user, which has a UID of 0.

**Regular User IDs (1000-59999)**: UIDs in this range are typically used for regular user accounts. When you create a new user account on a Linux system, it will typically be assigned a UID from this range. The specific range may vary slightly between different Linux distributions or system configurations.

**Reserved and Special UIDs (60000 and above)**: UIDs in this range are often reserved for special purposes or specific applications. They are not typically used for regular user accounts. Some applications or services may create their own UIDs in this range for isolation and security purposes.

*To define a UID for a user account, you can follow these steps:*
- Create a user account
- Manually specify a UID
- To view the UID associated with a user account

```bash
sudo useradd -s /bin/bash newuser33
sudo useradd -s /bin/bash -u 1001 newuser33
id newuser33
```

![](https://i.imgur.com/3CVpxlK.png)

---
3) What is GID? How to define it?

Group ID (GID) is a numerical identifier assigned to a user group on Unix-like operating systems, including Linux. GIDs are used to uniquely identify groups, which are collections of user accounts that share common permissions and access rights to files and resources. Just like with UIDs (User IDs), it's essential to define GIDs to manage access control and permission settings accurately.

*To define a GID for a user group, you can follow these steps:*

- Create a user group
- Manually specify a GID
- To view the GID associated with a group

```bash
sudo groupadd mygroup
sudo groupadd -g 1001 mygroup
getent group mygroup
```

![](https://i.imgur.com/yfgCCDP.png)

---
4) How to determine belonging of user to the specific group?

We can use several methods and commands.
- Using the groups Command: You can use the groups command followed by the username to display all the groups to which a user belongs.

```bash
groups username
```

- Using the id Command: The id command can also be used to display information about a user, including their group memberships. Running the id command with a username as an argument will show the user's UID, GID, and group memberships:

```bash
id username
```

- Checking the /etc/group File: You can directly examine the /etc/group file to see which users are members of a specific group. Open the file using a text editor or use commands like grep.

```bash
grep 'groupname' /etc/group
```

- Using the getent Command: The getent command can also be used to query group memberships for a specific user.

```bash
getent group | grep 'groupname'
```

![](https://i.imgur.com/jgHtPfv.png)

---
5) What are the commands for adding a user to the system? What are the basic parameters required to create a user?

To add a user to a Linux system, you can use the useradd or adduser command, depending on your distribution and preferences.

```bash
sudo useradd [options] username
```
- **username**: The login name of the new user.
- **[options]**: Additional options you can specify, such as setting the home directory, primary group, etc.

```bash
sudo useradd -m -s /bin/bash newuser
```

- **-m**: Create the user's home directory if it doesn't exist.
- **-s /bin/bash**: Set the user's login shell to /bin/bash.

The **adduser** command is a higher-level utility that provides an interactive interface for creating users.

```bash
sudo adduser username
```

This command will interactively prompt you for various user details, including the username, password, home directory, and more. It also sets up the user's environment more comprehensively.

Here are some common parameters and options you might specify when adding a user:

- **-m** or --create-home: Create the user's home directory.
- **-g** group or --gid group: Set the user's initial login group.
- **-G** groups or --groups groups: Add the user to additional groups (comma-separated).
- **-s** shell or --shell shell: Set the user's login shell.
- **-p** password or --password password: Set the user's encrypted password. 

```bash
sudo useradd -m -d /home/johndoe -g users johndoe
```

In this example:

- **-m**: Create the user's home directory.
- **-d /home/johndoe**: Set the user's home directory to /home/johndoe.
- **-g users**: Set the user's primary group to the "users" group.

---
6) How do I change the name (account name) of an existing user?

To change the name (account name) of an existing user on a Linux system, you can use the **usermod** command. 

```bash
sudo usermod -l new_username old_username
``` 

---
7) What is skell_dir? What is its structure?

The **skel** directory, short for "skeleton directory," is a template directory used as the basis for creating the home directories of new user accounts on a Linux or Unix-like system. When you create a new user using the useradd or **adduser** command, the contents of the **skel** directory are copied to the user's home directory to provide a set of default files and configurations.

Here is an example of what the structure of a **skel** directory might look like:

```bash
/etc/skel/
├── .bashrc
├── .bash_profile
├── .bash_logout
├── Documents/
├── Downloads/
├── Pictures/
├── Templates/
├── custom_script.sh
└── README.txt
```

---
8) How to remove a user from the system (including his mailbox)?

To remove a user from a Linux system, you can use the **userdel** command, which removes the user's account and optionally their home directory and mailbox. Here are the steps to remove a user, including their mailbox:

```bash
sudo userdel -r username
```

---
9) What commands and keys should be used to lock and unlock a user account?

To lock and unlock a user account on a Linux system, you can use the passwd command with the **-l** (lock) and **-u** (unlock) options. These commands allow you to disable or enable a user's ability to log in, respectively. 

```bash
//lock user
sudo passwd -l username

//unlock user
sudo passwd -u username
```

---
10) How to remove a user's password and provide him with a password-free login for subsequent password change?

To remove a user's password and allow them to log in without a password temporarily for subsequent password change, you can use the **passwd** command with certain options. 

```bash
sudo passwd -d username
```

---
11) Display the extended format of information about the directory, tell about the information columns displayed on the terminal.

When you display the extended format of information about a directory in a terminal, you typically use the **ls** command with the **-l** option

```bash
ls -l
``` 

---
12) What access rights exist and for whom (i. e., describe the main roles)?
Briefly describe the acronym for access rights. 

Access rights, also known as permissions or access control, determine who can perform specific actions (such as reading, writing, or executing) on a file or directory in a computer system. 

**Owner (User)**: The owner of a file or directory is usually the user who created it. They have the most extensive control and can typically modify permissions, read, write, and execute the file or directory.

**Group**: Files and directories can belong to a specific group, which consists of one or more users. Group permissions allow members of that group to access the file or directory according to the permissions set for the group. This is useful for collaborative work when multiple users need shared access.

**Others**: "Others" refers to all users who are not the owner or members of the group. These are typically users who have no direct affiliation with the file or directory. Permissions set for others determine what level of access they have.

The acronym for access rights is often represented using a combination of letters, which stand for specific permissions. The most common letters used in the acronym are:

**R**: Read permission allows a user to view the contents of a file or list the contents of a directory.
**W**: Write permission allows a user to modify the contents of a file or create, delete, or rename files within a directory.
**X**: Execute permission allows a user to run a program or script, or traverse (enter) a directory.
These permissions are typically represented in a sequence of characters, with each character indicating the permission for the owner, group, and others. For example:

**rwxr-xr--** indicates that the owner has read, write, and execute permissions, the group has read and execute permissions, and others have only read permission for the file or directory.

**drwxrwx--x** indicates a directory where the owner and group have read, write, and execute permissions, while others have only execute permission.

---
13) What is the sequence of defining the relationship between the file and the user?

The relationship between a file and a user in Unix-based systems is defined through ownership (user and optionally group) and permissions, which dictate what actions users can take with the file.


---
14) What commands are used to change the owner of a file (directory), as well as the mode of access to the file? Give examples, demonstrate on the terminal.

To change the owner of a file or directory, you can use the chown command. To change the mode of access (permissions) for a file or directory, you can use the chmod command.

Change Owner (User and Group):

```bash
sudo chown newowner:newgroup filename
```

```bash
sudo chown alice:staff myfile.txt
```

Change Permissions:

```bash
chmod permissions filename
```

```bash
chmod 755 myfile.txt
```

---
15) What is an example of octal representation of access rights? Describe the umask command.

An example of an octal representation of access rights is "755," where the owner has read, write, and execute permissions (4+2+1), and the group and others have read and execute permissions (4+1).

The umask command is used to set default permissions for newly created files and directories in Unix-like systems. It subtracts the specified umask value from the maximum permissions to determine the default permissions. For example, umask 022 sets default file permissions to 644 and directory permissions to 755.

---
16) Give definitions of sticky bits and mechanism of identifier substitution. Give an example of files and directories with these attributes.

**Sticky Bit**:

**Definition**: The sticky bit is a permission attribute in Unix-like operating systems. When set on a directory, it allows only the owner of a file to delete or rename their files within that directory, even if other users have write permissions in the same directory. It's commonly used on directories where multiple users need to write files, like /tmp.

**Mechanism of Identifier Substitution:**

**Definition**: Identifier substitution is a security mechanism in Unix-like systems where a process temporarily assumes the privileges or identity of another user, usually the superuser (root). This mechanism allows a process to perform tasks that require elevated permissions while maintaining the original user's context. It's typically used for system maintenance or administrative tasks.

---
17) What file attributes should be present in the command script?

In a Unix-like operating system, command scripts should typically have the following file attributes or characteristics:

Execute Permission: The script file should have the execute permission (usually denoted as **+x** or **chmod +x**) to allow it to be executed as a program. Without this permission, you won't be able to run the script as a standalone program.

Shebang (#!) Line: A shebang line at the beginning of the script specifies the interpreter or shell to be used for executing the script. For example, **#!/bin/bash** indicates that the script should be interpreted using the Bash shell. This line is essential for the system to know how to execute the script.

```bash
#!/bin/bash
# This is a sample script
echo "Hello, World!"
```