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

<ol>
    <li><strong>ssh</strong>
        <ul>
            <li>Used for securely connecting to a remote server.</li>
            <li>Example: <code>ssh user@hostname</code></li>
        </ul>
    </li>
    <li><strong>sshd</strong>
        <ul>
            <li>The SSH daemon that runs on servers, listening for incoming SSH connections and handling authentication.</li>
        </ul>
    </li>
    <li><strong>scp</strong>
        <ul>
            <li>Securely copies files between local and remote systems using SSH.</li>
            <li>Example: <code>scp file.txt user@hostname:/path/to/destination</code></li>
        </ul>
    </li>
    <li><strong>sftp</strong>
        <ul>
            <li>Secure File Transfer Protocol, an interactive file transfer utility over SSH.</li>
            <li>Example: <code>sftp user@hostname</code></li>
        </ul>
    </li>
    <li><strong>ssh-keygen</strong>
        <ul>
            <li>Generates and manages SSH key pairs.</li>
            <li>Example: <code>ssh-keygen -t rsa -b 4096</code></li>
        </ul>
    </li>
    <li><strong>ssh-copy-id</strong>
        <ul>
            <li>Copies a public key to a remote server for passwordless login.</li>
            <li>Example: <code>ssh-copy-id user@hostname</code></li>
        </ul>
    </li>
    <li><strong>ssh-agent</strong>
        <ul>
            <li>A helper program to store private keys in memory for easy authentication.</li>
            <li>Example: <code>eval $(ssh-agent) && ssh-add ~/.ssh/id_rsa</code></li>
        </ul>
    </li>
    <li><strong>ssh-add</strong>
        <ul>
            <li>Adds private keys to ssh-agent for session-based authentication.</li>
            <li>Example: <code>ssh-add ~/.ssh/id_rsa</code></li>
        </ul>
    </li>
</ol>


<h2>Important Client Side SSH Configuration Files</h2>
<ol>
    <li><strong>~/.ssh/config</strong>
        <ul>
            <li>User-specific SSH client configuration file. Allows setting per-host options like ports, usernames, or keys.</li>
            <li>Example:
                <pre>
Host myserver
    HostName example.com
    User myuser
    Port 2222
    IdentityFile ~/.ssh/id_rsa
                </pre>
            </li>
        </ul>
    </li>
    <li><strong>~/.ssh/known_hosts</strong>
        <ul>
            <li>Stores fingerprints of previously connected hosts to prevent man-in-the-middle attacks.</li>
        </ul>
    </li>
    <li><strong>~/.ssh/id_rsa and ~/.ssh/id_rsa.pub</strong>
        <ul>
            <li>Default private (id_rsa) and public (id_rsa.pub) key files for RSA-based authentication.</li>
        </ul>
    </li>
    <li><strong>~/.ssh/authorized_keys</strong>
        <ul>
            <li>Stores public keys of users allowed to access the account. Only exists on the server.</li>
        </ul>
    </li>
</ol>




<h2>Important Server Side SSH Configuration Files</h2>
<ol>
    <li><strong>/etc/ssh/sshd_config</strong>
        <ul>
            <li>Configuration file for the SSH daemon (sshd). Used to set server-wide options like authentication methods, ports, and allowed users.</li>
            <li>Key settings:
                <pre>
Port 22
PermitRootLogin no
PasswordAuthentication yes
                </pre>
            </li>
        </ul>
    </li>
    <li><strong>/etc/ssh/ssh_config</strong>
        <ul>
            <li>System-wide configuration file for the SSH client.</li>
        </ul>
    </li>
    <li><strong>/etc/ssh/ssh_host_*</strong>
        <ul>
            <li>Server's private and public host key files (e.g., ssh_host_rsa_key and ssh_host_rsa_key.pub).</li>
        </ul>
    </li>
    <li><strong>/var/log/auth.log (or /var/log/secure on some systems)</strong>
        <ul>
            <li>Log file for tracking SSH authentication attempts.</li>
        </ul>
    </li>
</ol>



<h2>Most Commonly Used Files in Daily Operations</h2>
<ul>
    <li><strong>On the Client Side:</strong>
        <ul>
            <li>~/.ssh/config</li>
            <li>~/.ssh/id_rsa and ~/.ssh/known_hosts</li>
        </ul>
    </li>
    <li><strong>On the Server Side:</strong>
        <ul>
            <li>/etc/ssh/sshd_config</li>
            <li>/etc/ssh/ssh_host_*</li>
        </ul>
    </li>
</ul>

