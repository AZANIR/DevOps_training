## Task3.Part2

1. Check the implementability of the most frequently used OPENSSH commands in the MS Windows operating system. (Description of the expected result of the commands + screenshots: command – result should be presented)

**ssh** - Secure Shell Login:
- *Description*: This command is used to establish a secure shell connection to a remote server.
- *Expected Result*: You should be prompted to enter your username and password or use SSH keys for authentication.

**scp** - Secure Copy:
- *Description*: Used for securely copying files between your local system and a remote server.
- *Expected Result*: You can copy files to/from the remote server, similar to the 'cp' command in Unix-like systems.

**ssh-keygen** - SSH Key Generation:
- *Description*: Generates SSH key pairs for secure authentication.
- *Expected Result*: Running this command should generate a public and private key pair and store them in your user's SSH directory.

**ssh-copy-id** - Copy Public Key to Server:
- *Description*: Copies your public key to a remote server, allowing you to authenticate without a password.
- *Expected Result*: You'll be prompted to enter your server's password to copy the public key.

**ssh-add** - Add Private Key to SSH Agent:
- *Description*: Adds your private key to the SSH agent for passwordless logins.
- *Expected Result*: The key will be added to the agent, and you won't need to enter the key's passphrase each time you connect.

**ssh-agent** - Start SSH Agent:
- *Description*: Starts the SSH agent to manage your SSH keys.
- *Expected Result*: Running this command should start the SSH agent process.

**ssh-keyscan** - Retrieve SSH Server Public Key:
- *Description*: Fetches the public key of a remote SSH server.
- *Expected Result*: The server's public key will be displayed in the terminal.

**ssh-config** - SSH Client Configuration:
- *Description*: Edit or view the SSH client configuration file.
- *Expected Result*: Opens the configuration file in a text editor or displays its contents.

**sftp** - Secure File Transfer Protocol:
- *Description*: Initiates an interactive file transfer session similar to FTP.
- *Expected Result*: You can navigate the remote server's file system and transfer files.

![ssh](https://i.imgur.com/XSoEJIv.png)

![](https://i.imgur.com/RgbUy7u.png)

![](https://i.imgur.com/YW20wSG.png)

![](https://i.imgur.com/jmCBvXP.png)

---
2. Implement basic SSH settings to increase the security of the client-server connection (at least )

We can increase the security of the client-server connection by changing the default port for SSH connections, disabling root login, and disabling password authentication.

- Disable Root Login:
- Use Strong Authentication:
- Change Default SSH Port:
- Implement IP Whitelisting:
- Disable Empty Passwords:
- Implement Idle Session Timeout:
- Use Two-Factor Authentication (2FA):
- Monitor SSH Logs:
- Limit SSH Protocol Versions:

change default port for SSH connections to 2222 and password authentication to no

![](https://i.imgur.com/O9AzTi5.png)



---
3. List the options for choosing keys for encryption in SSH. Implement 3 of them.

**RSA (Rivest–Shamir–Adleman):**
- *Description*: **RSA** is one of the oldest and widely supported asymmetric encryption algorithms. It uses a pair of public and private keys for encryption and decryption.
- *Implementation*: To use RSA keys for SSH, generate an RSA key pair using the ssh-keygen command, and then copy the public key to the server.

**DSA (Digital Signature Algorithm):**
- *Description*: **DSA** is another asymmetric encryption algorithm used for SSH. It's less common than RSA but still supported.
- *Implementation*: To use DSA keys, generate a DSA key pair with ssh-keygen, and then copy the public key to the server.

**ECDSA (Elliptic Curve Digital Signature Algorithm):**
- *Description*: ECDSA is a modern asymmetric encryption algorithm that offers strong security with shorter key lengths compared to RSA or DSA.
- *Implementation*: To use ECDSA keys, generate an ECDSA key pair using ssh-keygen, and copy the public key to the server.

```bash
//For RSA:
ssh-keygen -t rsa -b 2048

//For DSA:
ssh-keygen -t dsa

//For ECDSA:
ssh-keygen -t ecdsa -b 256
```

---
4. Implement port forwarding for the SSH client from the host machine to the guest Linux virtual machine behind NAT. 

![](https://i.imgur.com/lREWT1E.png)

![](https://i.imgur.com/8764Ujr.png)

---
5. *Intercept (capture) traffic (tcpdump, wireshark) while authorizing the remote client on the server using ssh, telnet, rlogin. Analyze the result.

![](https://i.imgur.com/joeDgOI.png)

![](https://i.imgur.com/R00SOz6.png)

![](https://i.imgur.com/N7zriW9.png)

