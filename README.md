Quick step-by-step

Prepare the environment

Start an Ubuntu (or Kali) VM for the host and a Kali VM for testing.

Install UFW (if needed)

sudo apt update
sudo apt install ufw -y


Check status: sudo ufw status.

Enable UFW

sudo ufw enable


Confirm it’s active: sudo ufw status.

Add basic rules

Allow SSH and HTTP, deny FTP:

sudo ufw allow ssh
sudo ufw allow http
sudo ufw deny ftp


Verify with: sudo ufw status numbered.

Modify or delete rules

List numbered rules: sudo ufw status numbered

Delete rule #N: sudo ufw delete N.

Test firewall from attacker/test VM (Nmap)

From Kali run:

sudo nmap -Pn [Target_IP]


Observe which ports are shown open/closed and confirm rules behave as expected.

Add advanced rules (optional)

Allow from a single IP: sudo ufw allow from [IP_ADDRESS]

Allow a custom port: sudo ufw allow 8080/tcp.

Enable and review logging

sudo ufw logging on
sudo tail -f /var/log/ufw.log


Use logs to detect unexpected traffic or rule hits.

Best practices / analysis

Keep rules minimal and specific (least privilege).

Regularly audit rules, disable unused ones, secure admin access, and correlate logs with packet captures (Wireshark) if needed.

Cleanup

Disable UFW if required for cleanup/testing:

sudo ufw disable


Shut down VMs when finished.
