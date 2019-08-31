# Environment Setup

Download and install VirtualBox: <a href="https://www.virtualbox.org/" target="_blank">https://www.virtualbox.org/</a>

1. You should be safe using the default settings when installing
2. Note you may get a popup about downloading an updated ExtensionPack, feel free to do so
3. Open a command prompt and cd into the VirtualBox Program Files directory, something like: cd "C:\Program Files\Oracle\VirtualBox"
4. Configure a dhcpserver for the internal network intnet via:* VBoxManage dhcpserver add -netname intnet -ip 10.13.13.100 -netmask 255.255.255.0 -lowerip 10.13.13.101 -upperip 10.13.13.254 -enable*

![Image](./images/setup-1.png "Image")

## Configuring DHCP

```
VBoxManage dhcpserver add -netname intnet -ip 10.13.13.100 -netmask 255.255.255.0 -lowerip 10.13.13.101 -upperip 10.13.13.103 -enable
```

1. Download the Kali Linux VirtualBox image: <a href="https://www.offensive-security.com/kali-linux-vm-vmware-virtualbox-image-download/" target="_blank">https://www.offensive-security.com/kali-linux-vm-vmware-virtualbox-image-download/</a>.

1. Download the Mr. Robot image: <a href="https://www.vulnhub.com/entry/mr-robot-1,151/" target="_blank">https://www.vulnhub.com/entry/mr-robot-1,151/</a>.

    1. Import the MrRobot Image into VirtualBox via the import button, you shouldn’t need to change any of the preconfigured settings

    1. Use the VM's Settings dialog in the Oracle VM VirtualBox graphical user interface. In the Networking category of the settings dialog, select Internal Networking from the drop-down list of networking modes. Select the name of an existing internal network from the drop-down list below or enter a new name into the Name field.

    1. Ensure the machine starts correctly. RIGHT CNTRL IS THE DEFAULT BUTTON TO BREAK THE CURSOR OUT OF THE VM CONTEXT.

    1. On the machine login with the following credentials:
        1. **Username: robot**
        2. **Password: abcdef****ghijklmnopqrstuvwxyz**** (all letters of the alphabet)**
    2. Navigate to: */opt/bitnami/apps/wordpress/htdocs/video *
    3. Delete everything in this file except fsociety.webm. (*this command will content from the web application that may be somewhat controversial.  Since our focus is on educating students about general CTF challenge solving & pentesting concepts, we’re removing extraneous material.) *

    
    ![Image](./images/setup-1.png "Image")

1. Once the machine is running, click Machine | Take Snapshot to take a snapshot of the Mr. Robot VM at its initial state
1. Repeat the process for the Kali Linux OVA making sure to use the same network that was set for Mr. Robot VM
    1. Turn off the machine and configure it to use the same internal network that the Mr. Robot VM is on
    2. Start the machine and take a snapshot just as with the Mr. Robot VM
2. From the Mr. Robot VM get it’s IP address

1. From the Kali Linux machine, navigate to the IP address in the web browser and confirm the site loads.

## Resetting the Lab Environment Between Students

1. This should be as easy as reloading back to the snapshots taken during the setup to ensure a fresh, clean environment for the next student

## Guide for Students

1. Start off with the basics of Linux commands: cd, clear, ls, cat, vim, grep, man, su etc.
    1. Talk about user directories
    2. Talk about root vs a regular user
2. Go into detail about nmap, how to use it to scan for live hosts on a network and how to scan a specific host
    1. Briefly touch on common ports used by a server: HTTP, SSH, etc.
3. Go into detail about the Robots Exclusion Standard, aka robots.txt
4. Talk about WordPress
    1. Specifically talk about things like wp-admin, wp-login, readme.html and license.txt
    2. Discuss how WordPress is commonly associated with a large number of vulnerabilities due to ease of misconfiguration
5. Go into detail about capturing and viewing network calls via the developer tools of a browser and Burp Suite
6. Go into detail about how dictionary attacks work and talk about how to use THCHydra, the password cracker
7. Go into detail about local file inclusion attacks, and remote code executions
    1. Note that as per environment setup, there should be a pre-saves PHP file that will open a reverse shell on the host
8. Go into detail about netcat and how it works
9. Talk about hashes and how MD5 is considered broken
10. Talk about the SUID bit and why it’s dangerous