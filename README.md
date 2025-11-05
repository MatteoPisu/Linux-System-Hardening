Linux-system-hardening project

Phase 1: setting up the environment

**Goal:** Create a secure and up-do-date Linux environment for hardening

What I did:
- Installed Ubuntu 22.04 in VirtualBox
- Added the user I logged in with to the sudo group and verified with 'sudo whoami'
- Applied security updates 'sudo apt update && sudo apt upgrade -y'
- Installed the following packages: net-tools, ufw, fail2ban, lynis
- Created snapshot after the security updates for safety

See screenshots on folder Phase 1

Phase 2: Access control and SSH Hardening

**Goal:**
- Restrict unauthorized access
- Enforce key-based SSH login
- Disable root login over SSH
- Enforce strong password policy for every user
 
What I did:
- Edited /etc/ssh/sshd_config to set "PermitRootLogin no"
- Generated SSH key pair and copied the public key to the VM
- Disable password login and verified that the login works using the new SSH key
- Installed 'libpam-pwquality'
- Configured /etc/pam.d/common-password for complexity and character types
- Tested it first with a weak password and then with a strong one

See screenshots on folder Phase 2


Phase 3: Firewall and intrusion prevention

**Goal:**
- Block unwanted network traffic
- Prevent brute-force attacks
- Monitor and protect the system from common intrusion attempts


What I did:
1. UFW Firewall:
- Deny all incoming connections
- Allow all outgoing connections
- Allow SSH to prevent lookout
- Enabled UFW and verified rules
2. Fail2Ban:
- Configured [sshd] jail
- enabled monitoring of SSH
- Set maxretry=3 and bantime=600 seconds
3.System Audit with Lynis
- Ran sudo lynis audit system
- Reviewed warning
- Confirmed that everything is properly configured


See screenshots on folder Phase 3
