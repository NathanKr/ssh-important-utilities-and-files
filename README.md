<h1>Project name</h1>
SSH Essentials

<h2>Project Description</h2>
<p>This repository contains a list of important utilities and files related to SSH.</p>

<h2>Project Motivation</h2>
<p>SSH involves many concepts that can overwhelm new users. This repository compiles the key components to simplify the learning process and serve as a handy short guide.</p>

<h2>What is SSH</h2>
<p>SSH (Secure Shell) is a cryptographic network protocol for secure data communication, especially for remote login and command-line execution, between two networked computers.</p>

<h3>Key Concepts</h3>
<ul>
<li><strong>Client-server architecture:</strong> SSH operates on a client-server model. The SSH client initiates a connection to the SSH server.</li>
<li><strong>Port 22:</strong> By default, SSH operates on TCP port 22.</li>
<li><strong>Encryption:</strong> All data transmitted between the client and server is encrypted using strong symmetric cryptographic algorithms.</li>
<li><strong>Authentication:</strong> SSH supports various authentication methods, including password-based and public-key-based authentication.</li>
</ul>

<h2>Motivation for SSH</h2>
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
<p>In many scenarios, public-key cryptography is preferred over password-based authentication for improved security. A public-key pair is used for authentication but a symmetric encryption algorithm is used for encrypting the data transmitted during the session.</p>

<h2>Components list in this repo</h2>
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

<ul>
    <li><h3>ssh</h3>
        <ul>
            <li>Used for securely connecting to a remote server.</li>
            <li>Example: <code>ssh user@hostname</code> - initiates a secure connection to a remote server using your specified username and hostname.</li>
        </ul>
    </li>
    <li><h3>sshd</h3>
        <ul>
            <li>The SSH daemon that runs on servers, listening for incoming SSH connections and handling authentication.</li>
        </ul>
    </li>
    <li><h3>scp</h3>
        <ul>
            <li>Securely copies files between local and remote systems using SSH.</li>
            <li>Example: <code>scp file.txt user@hostname:/path/to/destination</code> - securely copies a file from your local machine to a remote server using SSH</li>
        </ul>
    </li>
    <li><h3>sftp</h3>
        <ul>
            <li>Secure File Transfer Protocol, an interactive file transfer utility over SSH.</li>
            <li>Example: <code>sftp user@hostname</code> - starts a secure file transfer session to a remote server using the SFTP (Secure File Transfer Protocol) protocol</li>
        </ul>
    </li>
    <li><h3>ssh-keygen</h3>
        <ul>
            <li>Generates and manages SSH key pairs.</li>
            <li>Example: <code>ssh-keygen -t rsa -b 4096</code> - generates a new RSA SSH key pair with 4096 bits for secure authentication.</li>
        </ul>
    </li>
    <li><h3>ssh-copy-id</h3>
        <ul>
            <li>Copies a public key to a remote server for passwordless login.</li>
            <li>Example: <code>ssh-copy-id -i ~/.ssh/your_specific_public_key.pub user@hostname</code> - copies the specified public SSH key to a remote server for passwordless login</li>
        </ul>
    </li>
    <li><h3>ssh-agent</h3>
        <ul>
            <li>A helper program to store private keys in memory for easy authentication.</li>
            <li>Example: <code>eval $(ssh-agent) && ssh-add ~/.ssh/id_rsa</code> - starts an SSH agent and adds your private key to it for easy SSH key management.</li>
        </ul>
    </li>
    <li><h3>ssh-add</h3>
        <ul>
            <li>Adds private keys to ssh-agent for session-based authentication.</li>
            <li>Example: <code>ssh-add ~/.ssh/id_rsa</code> - adds your private SSH key to the SSH agent for easy SSH key management, even if there is no passphrase</li>
        </ul>
    </li>
</ul>

<h2>Important Client Side SSH Files</h2>
<ul>
    <li><h3>/etc/ssh/ssh_config</h3>
        <ul>
            <li>System-wide configuration file for the SSH client.</li>
            <li>This file provides default settings for all users on the system unless overridden by user-specific configuration files</li>
        </ul>
    </li>
    <li><h3>~/.ssh/config</h3>
        <ul>
            <li>User-specific SSH client configuration file. Allows setting per-host options like ports, usernames, or keys.</li>
            <li>The following example shows how to set up a user-specific SSH configuration file for connecting to a remote server with custom settings. By default, SSH uses port 22, your local username, and the first available key:
        
```bash
Host myserver
HostName example.com
User myuser
Port 2222
IdentityFile ~/.ssh/id_rsa
```
</li>
        </ul>
    </li>
    <li><h3>~/.ssh/known_hosts</h3>
        <p>This file is a client-side file and an important component of SSH security. Here’s a quick overview of what it is and how it works:</p>
<ul>
    <li><strong>Purpose:</strong> Stores the fingerprints (unique identifiers or hashed representations) of the public keys of remote servers you've previously connected to via SSH. This helps verify the identity of the server in future connections.</li>
    <li><strong>Format:</strong> Contains entries for each known host, including the hostname, IP address, and the server’s public key.</li>
</ul>
    </li>
    <li><h3>~/.ssh/id_rsa and ~/.ssh/id_rsa.pub</h3>
        <ul>
            <li>Default private (id_rsa) and public (id_rsa.pub) key files for RSA-based authentication.</li>
            <li>These keys are generated on the client-side and the public key is typically copied to the server's ~/.ssh/authorized_keys file to enable passwordless login</li>
            <li>These keys are generated typically using ssh-keygen</li>
        </ul>
    </li>
   
</ul>

<h2>Important Server Side SSH Files</h2>
<ul>
 <li><h3>~/.ssh/authorized_keys</h3>
    <ul>
    <li><strong>Purpose:</strong> The <code>authorized_keys</code> is a server-side file. It is an important component of SSH security, used to manage which SSH keys are authorized to log into a specific user account on a remote system. It specifies which public keys are permitted to authenticate and gain access to the server.</li>
    <li><strong>Location:</strong> In the home directory of the user account on the server.</li>
    <li><strong>Function:</strong> When you attempt to login via SSH from a client machine, the server checks your public key against the entries in the <code>authorized_keys</code> file. If a match is found, you are granted access without needing to enter a password.</li>
    </ul>
    </li>
    <li><h3>/etc/ssh/sshd_config</h3>
        <ul>
            <li>Configuration file for the SSH daemon (sshd). Used to set server-wide options like authentication methods, ports, and allowed users.</li>
        <li>Recommended settings:

```bash
    Port 22
    PermitRootLogin no
    PasswordAuthentication yes
```
            
</li>
        </ul>
    </li>
    <li><h3>/etc/ssh/ssh_host_*</h3>
        <ul>
            <li>Server's private and public host key files (e.g., ssh_host_rsa_key and ssh_host_rsa_key.pub).</li>
        </ul>
    </li>
    <li><h3>/var/log/auth.log (or /var/log/secure on some systems)</h3>
        <ul>
            <li>Log file for tracking SSH authentication attempts.</li>
        </ul>
    </li>
</ul>


<h2>Most Commonly Used Files in Daily Operations</h2> 
<p>These are the files most users frequently interact with while using SSH:</p> 
<ul> 
<li><strong>On the Client Side:</strong> 
<ul> 
<li><code>~/.ssh/config</code>: User-specific configuration file to simplify SSH commands</li>
<li><code>~/.ssh/id_rsa</code> and <code>~/.ssh/known_hosts</code>: - Keep <code>id_rsa</code> private and secure.</li>
<li>Periodically clean outdated entries in <code>known_hosts</code></li> 
</ul> 
</li> 
<li><strong>On the Server Side:</strong> 
<ul> 
<li><code>/etc/ssh/sshd_config</code>: Central configuration for the SSH server. Ensure secure settings like: 

```bash
   PermitRootLogin no 
   PasswordAuthentication no 
   PubkeyAuthentication yes
```

</li> 
<li><code>/etc/ssh/ssh_host_*</code>: Server’s host keys that establish trust during connections.
</li> 
</ul> 
</li> 
</ul>

