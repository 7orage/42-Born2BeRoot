_This project has been created as part of the 42 curriculum by <lheteau>_
_We are the 16th January 2025._
***
# Born2BeRoot

You can find the official project subject at the following link:
[Born2BeRoot](https://yannick.eu/content/files/2023/07/en.subject.Born2beroot.pdf?utm_source=chatgpt.com)

### Table of contents

1. _Description_
2. _Instructions_
3. _Pros and cons_

	3.1. _Debian VS Rocky_

	3.2. _AppArmor VS SELinux_
	
	3.3. _UFW VS firewalld_
	
	3.4. _VirtualBox VS UTM_
4. _Ressources_

***
## **Description**

• This virtual machine is a minimal Linux server running the latest stable version of Debian. It is configured with:

- Two encrypted partitions using LVM for secure storage.
- SSH service running on port 4242 with root login disabled.
- A firewall (UFW) active, allowing only the SSH port.
- A regular user `lheteau`, belonging to both `user42` and `sudo` groups.
- Strong password policies applied to all users, including password expiration, complexity requirements, and warnings.
- Sudo configured with TTY enforcement, logging, limited paths, and restricted authentication attempts.

The hostname of the virtual machine is set as `lheteau42`.
***
• In this project, the goal was to create my first virtual machine using VirtualBox, following the strict instructions of Born2BeRoot. I set up a minimal Linux server, secured it with a firewall and SSH, managed users and permissions, and worked with encrypted partitions—all while applying proper system administration rules.

## **Instructions**

• To explore and test the VM, follow these steps:

1. **Download the VM**  
   Ensure you have the VM image file provided in this repository or via the project submission.

2. **Set up a virtualization environment**  
   - Recommended: [VirtualBox](https://www.virtualbox.org/).  
   - Import the VM image into your preferred hypervisor.

3. **Start the VM**  
   - Launch the VM using your hypervisor.  
   - Write the passphrase `lechocolatmedonneleschocottes` required and login as `lheteau` with the password `1234Choco.`.

4. **Access and explore**  
   - Once logged in, you can explore system configurations, installed services, and scripts.

## **Pros and cons**

### DEBIAN VS ROCKY

• For the operating system, I chose Debian. Debian is very stable, well-documented, and ideal for beginners in system administration. Rocky Linux is more enterprise-oriented and requires a more complex setup, especially with SELinux.

| Option      | Pros                                       | Cons                                  | Choice        |
|-------------|--------------------------------------------|---------------------------------------|---------------|
| Debian      | Stable, well-documented, easy to configure | Less enterprise-focused than Rocky    | ✅ Chosen     |
| Rocky Linux | Enterprise-ready, based on RHEL            | More complex setup, SELinux mandatory | ❌ Not chosen |

***
### APPARMOR VS SELINUX

• For security, I chose AppArmor. AppArmor is simple to configure thanks to its pre-built profiles and is natively integrated into Debian. SELinux is more powerful and flexible but much more complex for beginners.

| Option   | Pros                                       | Cons                       | Choice        |
|----------|--------------------------------------------|----------------------------|---------------|
| AppArmor | Simple to configure, ready-to-use profiles | Less flexible than SELinux | ✅ Chosen     |
| SELinux  | Very powerful and flexible                 | Complex for beginners      | ❌ Not chosen |

***
### UFW VS FIREWALLD

• For the firewall, I chose UFW. It is easy to use and allows quickly securing the server by opening only the SSH port. Firewalld is more flexible but more complex to configure.

| Option    | Pros                                         | Cons                         | Choice        |
|-----------|----------------------------------------------|------------------------------|---------------|
| UFW       | Simple and quick to set up, ideal for Debian | Less flexible than firewalld | ✅ Chosen     |
| firewalld | More flexible, zone and service management   | More complex configuration   | ❌ Not chosen |

***
### VIRTUALBOX VS UTM

• For virtualization, I chose VirtualBox. It is mature, stable, and compatible with Debian. It allows easy management of network, LVM partitions, and snapshots. UTM is lighter and faster on Mac ARM, but less documented for Linux.

| Option     | Pros                                                | Cons                                   | Choice        |
|------------|-----------------------------------------------------|----------------------------------------|---------------|
| VirtualBox | Mature, stable, Linux-compatible, easy to configure | Heavier than UTM                       | ✅ Chosen     |
| UTM        | Lightweight, fast on Mac ARM                        | Less documented, limited Linux support | ❌ Not chosen |

## **Ressources**

• I used several articles and online resources to support my coding journey. Notably, the videos “Born2BeRoot” by the youTuber Nirmal Gope was very helpful.
***
• Artificial Intelligence tools were helpful in the writing and structuring of this README.
