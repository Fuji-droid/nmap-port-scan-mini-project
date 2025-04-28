**Mini Project 1: Open Port Scanning on Ubuntu VM using nmap**

**Background:** Scanning open ports on a newly installed virtual machine (VM) before and after adding a service.

**Details:** When you install a fresh virtual machine (in this case, Ubuntu), you'll need to ensure that the tool **nmap** is installed to scan for open ports. Follow these steps:

**1. Update system packages:**

```bash
sudo apt update
```

This command updates your system's package list to make sure you are installing the latest versions available. You may be prompted to enter your password (note: no characters will appear when you type it).

**2. Install nmap:**

```bash
sudo apt install nmap
```

Let the terminal complete the installation process. Once installed, you can proceed to scan your system.

**3. Find your system's IP address:**

```bash
ip a
```

Look for your IP address under a section like `enp0s3`.

- **enp0s3** refers to your network interface:
  - `en` stands for Ethernet
  - `p0` stands for Bus 0
  - `s3` stands for Slot 3
- The address listed under `inet` is your IP address.

**4. Perform your first nmap scan:**

```bash
nmap YOUR_IP_ADDRESS
```

(Replace `YOUR_IP_ADDRESS` with the address found in the previous step.)

You will likely see a result showing no open ports. (Screenshot: NMAP1)

**5. Install a service to create an open port:** To simulate an open port, install a basic web server like **Apache**:

```bash
sudo apt install apache2
```

**6. Check if Apache is running:**

```bash
sudo systemctl status apache2
```

You should see a message indicating that the Apache service is **active (running)**. (Screenshot: NMAP3)

**7. Run another nmap scan:** After installing Apache, re-run the nmap command:

```bash
nmap YOUR_IP_ADDRESS
```

This time, you should see **Port 80 (HTTP)** open.

**8. Stopping the Apache server:** For security purposes, you can stop the web server when not needed:

```bash
sudo systemctl stop apache2
```

**Important Points to Remember:**

- **Apache2** is a popular open-source web server that serves websites over the internet.
- To understand more about any Linux command, use the `man` command:
  ```bash
  man COMMAND_NAME
  ```
- You can simulate additional open ports by installing other services:

| Service Name        | Purpose                    | Opens Which Port? | Installation Command            |
| ------------------- | -------------------------- | ----------------- | ------------------------------- |
| OpenSSH Server      | Secure remote login (SSH)  | Port 22 (TCP)     | sudo apt install openssh-server |
| FTP Server (vsftpd) | File transfer server (FTP) | Port 21 (TCP)     | sudo apt install vsftpd         |

- **Understanding "sudo apt install nmap":**
  - `sudo` = Super User DO (grants administrative permissions)
  - `apt` = Advanced Package Tool (Ubuntu's package manager)
  - `install nmap` = Requests the system to install the `nmap` tool

In simple terms, you are telling Ubuntu: *"I have permission and would like you to install nmap for me."*
