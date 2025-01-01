<h1>Project name</h1>
SSH Essentials

<h2>Project Description</h2>
<p>This repository contains a list of important utilities and files related to SSH.</p>

<h2>Project Motivation</h2>
<p>SSH involves many concepts that can overwhelm new users. This repository compiles the key components to simplify the learning process and serve as a handy short guide.</p>

<h2>What is ssh</h2>
<p>SSH (Secure Shell) is a cryptographic network protocol for secure data communication, especially for remote login and command-line execution, between two networked computers.</p>

<h3>Key Concepts</h3>
<ul>
<li><strong>Client-server architecture:</strong> SSH operates on a client-server model. The SSH client initiates a connection to the SSH server.</li>
<li><strong>Port 22:</strong> By default, SSH operates on TCP port 22.</li>
<li><strong>Encryption:</strong> All data transmitted between the client and server is encrypted using strong cryptographic algorithms.</li>
<li><strong>Authentication:</strong> SSH supports various authentication methods, including password-based and public-key-based authentication.</li>
</ul>

<h2>Motivation for ssh</h2>
<ul>
<li><strong>Security</strong>: SSH provides robust encryption and authentication, ensuring secure and private communication between devices over potentially unsecured networks.</li>

<li><strong>Remote Management</strong>: It allows administrators and users to remotely manage and configure servers, routers, and other network devices securely.</li>
</ul>

<h2>SSH Use Cases</h2>
<ul>
<li><strong>Remote Server Access</strong>: SSH allows users to securely connect to remote servers, enabling system administrators to manage servers and perform tasks as if they were physically present. For example, working on a Digital Ocean droplet from your PC.</li>


<li><strong>Automated Scripts</strong>: SSH is often used in scripts for automating tasks like backups, deployments, and monitoring, especially in DevOps environments, e.g., in GitHub Actions.</li>

<li><strong>Secure Git Access</strong>: Developers use SSH keys to securely interact with remote Git repositories, enabling safe code collaboration and version control.</li>

</ul>

<p> In many scenarios, public-key cryptography is preferred over password-based authentication for improved security. A public-key pair is used for both authentication and encryption in these cases</p>


****************************** go over this and below 
<h2>Component list in this repo</h2>
<ul>
<li>ssh </li>
<li>sshd</li>
<li>scp</li>
<li>sftp</li>
<li>ssh-keygen</li>
<li>ssh-copy-id</li>
<li>ssh-agent</li>
<li>ssh-add</li>
<li>~/.ssh/config and /etc/ssh/ssh_config</li>
<li>~/.ssh/known_hosts</li>
<li>~/.ssh/id_rsa and ~/.ssh/id_rsa.pub</li>
<li>~/.ssh/authorized_keys</li>
<li>/etc/ssh/sshd_config</li>
<li>/etc/ssh/ssh_host_*</li>
<li>/var/log/auth.log (or /var/log/secure on some systems)</li>
</ul>

Understanding these utilities and files is key to effectively managing and troubleshooting SSH.

<h2>Important SSH Utilities</h2>

1. ssh

Used for securely connecting to a remote server.

Example:

ssh user@hostname



2. sshd

The SSH daemon that runs on servers, listening for incoming SSH connections and handling authentication.



3. scp

Securely copies files between local and remote systems using SSH.

Example:

scp file.txt user@hostname:/path/to/destination



4. sftp

Secure File Transfer Protocol, an interactive file transfer utility over SSH.

Example:

sftp user@hostname



5. ssh-keygen

Generates and manages SSH key pairs.

Example:

ssh-keygen -t rsa -b 4096



6. ssh-copy-id

Copies a public key to a remote server for passwordless login.

Example:

ssh-copy-id user@hostname



7. ssh-agent

A helper program to store private keys in memory for easy authentication.

Example:

eval $(ssh-agent)
ssh-add ~/.ssh/id_rsa



8. ssh-add

Adds private keys to ssh-agent for session-based authentication.

Example:

ssh-add ~/.ssh/id_rsa


<h2>Important Client Side SSH Configuration Files</h2>
1. ~/.ssh/config

User-specific SSH client configuration file. Allows setting per-host options like ports, usernames, or keys.

Example:

Host myserver
    HostName example.com
    User myuser
    Port 2222
    IdentityFile ~/.ssh/id_rsa



2. ~/.ssh/known_hosts

Stores fingerprints of previously connected hosts to prevent man-in-the-middle attacks.



3. ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub

Default private (id_rsa) and public (id_rsa.pub) key files for RSA-based authentication.



4. ~/.ssh/authorized_keys

Stores public keys of users allowed to access the account. Only exists on the server.




<h2>Important Server Side SSH Configuration Files</h2>
1. /etc/ssh/sshd_config

Configuration file for the SSH daemon (sshd). Used to set server-wide options like authentication methods, ports, and allowed users.

Key settings:

Port 22
PermitRootLogin no
PasswordAuthentication yes



2. /etc/ssh/ssh_config

System-wide configuration file for the SSH client.



3. /etc/ssh/ssh_host_*

Server's private and public host key files (e.g., ssh_host_rsa_key and ssh_host_rsa_key.pub).



4. /var/log/auth.log (or /var/log/secure on some systems)

Log file for tracking SSH authentication attempts.


<h2>Most Commonly Used Files in Daily Operations</h2>
On the Client Side:

~/.ssh/config

~/.ssh/id_rsa and ~/.ssh/known_hosts


On the Server Side:

/etc/ssh/sshd_config

/etc/ssh/ssh_host_*