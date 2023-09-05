## Lab 1


### Using the **finger** command, as well as reading its documentation:

Objective: To familiarize ourselves with the *finger* command and its usage, as well as to explore user information on a Linux system.

1. Introduction to the finger Command

    - Read the documentation for the finger command using the man command to understand its basic usage and options.
    ```
    man finger
    ```
    ![](https://i.imgur.com/GDDfHnL.png)

2. User Information Lookup
    - Use the finger command to look up information about a specific user on the system. Replace username with the actual username you want to inquire about:
    ```
    finger username
    ```
    ![](https://i.imgur.com/LPPYLNj.png)

3. List of Logged-In Users
    - Use the finger command to list all users currently logged in to the system:
    ```
    finger
    ```
    ![](https://i.imgur.com/UUifCS4.png)

4. List of Logged-In Users with Additional Information
    - Use the finger command to list all users currently logged in to the system, with additional information:
    ```
    finger -l
    ```
    ![](https://i.imgur.com/KAzxwSK.png)