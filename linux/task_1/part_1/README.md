## task 1

### Task1.Part1
---
1) Log in to the system as root.

![](https://i.imgur.com/S6BPlKA.png)
---
2) Use the passwd command to change the password. Examine the basic
parameters of the command. What system file does it change *?

*Here's the basic syntax of the "passwd" command:*
```bash
passwd [options] [username]
```

[options]: These are optional flags that you can use to modify the behavior of the passwd command. Some common options include:

-  -l: Lock the password (disable the account).
-  -u: Unlock the password (enable the account).
-  -d: Delete the password for the specified user.
-  -e: Expire the password immediately, forcing the user to change it upon next login.
-  -S: Display password status information.

[username]: This is the name of the user for whom you want to change the password. If you don't specify a username, it assumes you are changing the password for the current user (the one running the command).

When you change a user's password using the "passwd" command, it updates the */etc/shadow* file. The */etc/shadow* file is a system file that stores the hashed passwords and other security-related information for user accounts. It's crucial for maintaining the security of user passwords, as it keeps the password hashes in a protected location.

>**WARNING**:Keep in mind that you typically need superuser (root) privileges to change the password for other users or to use certain options like locking or expiring passwords.

![](https://i.imgur.com/uYcr8Xn.png)
---
3) Determine the users registered in the system, as well as what commands they execute. What additional information can be gleaned from the command
execution?

To determine the users registered in the system and the commands they execute, you can use various commands and tools, such as w, who, last, and ps. Here's how you can gather this information:

List of Logged-In Users and Their Commands (w, who, ps):

- w: The w command displays information about currently logged-in users, including their usernames, terminal sessions, login times, idle times, and the commands they are currently running.

- who: The who command provides information about logged-in users and their terminal sessions.

- ps aux: The ps command with the aux options displays a list of all running processes, including the user who initiated each process and the command being executed.

These commands will show you a snapshot of the current user activity on the system.
![](https://i.imgur.com/3VGnwOI.png)

---
4) Change personal information about yourself.

The main commands for working with Linux accounts are **useradd**, **userdel**, and **usermod**, as well as the password file editor vipw. However, please note that changing user information should typically be done by a system administrator with the appropriate permissions.

![](https://i.imgur.com/TDuSPR8.png)
---
![](https://i.imgur.com/22bQqsX.png)
![](https://i.imgur.com/RZ9JfaU.png)
![](https://i.imgur.com/hwaNJEU.png)

---
5) Become familiar with the Linux help system and the man and info commands.Get help on the previously discussed commands, define and describe any two keys for these commands. Give examples.
man - an interface to the on-line reference manuals
![](https://i.imgur.com/LLO79S8.png)

Two commonly used keys within the man command are:

Navigation Keys:

    - Spacebar: Scroll down one page at a time.
    - Enter: Scroll down one line at a time.
    - B: Scroll up one page at a time.
    - Y: Scroll up one line at a time.
    - /: Search for a specific keyword within the manual page. After typing /, enter your search term and press Enter. To find the next occurrence, press N, and to go to the previous occurrence, press Shift+N.
Quitting and Exiting:

    - q: Quit the man viewer and return to the terminal.

**info** - read Info documents
![](https://i.imgur.com/nKzNeXc.png)

Two commonly used keys within the info command are:

Navigation Keys:

    - Spacebar: Scroll down one page at a time.
    - B: Scroll up one page at a time.
    - N: Go to the next page.
    - P: Go to the previous page.
    - U: Go up to the parent node (move up one level in the documentation structure).
    - Tab: Move the cursor to the next hyperlink.
    - Enter: Follow a hyperlink.
Quitting and Exiting:

    - q: Quit the info viewer and return to the terminal.

---
6) Explore the more and less commands using the help system. View the contents of files .bash* using commands.
![](https://i.imgur.com/56fUWHf.png)

You can use the following keys for navigation:

    - Spacebar: Scroll down one page.
    - B: Scroll up one page.
    - G: Go to the end of the file.
    - 1G or gg: Go to the beginning of the file.
    - /search_term: Search for a specific term within the file. Replace search_term with the term you want to find. Press 'n' to find the next occurrence and 'N' to find the previous one.
    - q: Quit less and return to the terminal.
---
7) * Describe in plans that you are working on laboratory work 1. Tip: You should read the documentation for the finger command.

        [Lab 1- finger](lab_1/README.md)
---
8) * List the contents of the home directory using the ls command, define its files and directories. Hint: Use the help system to familiarize ourself with the ls command.

        [Lab 2- ls](lab_2/README.md)