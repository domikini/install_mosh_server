# Install mosh server as compliment to ssh
Mosh is a free replacement for SSH that allows roaming and supports intermittent connectivity. Unlike regular SSH connections, Mosh continuously syncs your local and remote sessions to ensure that your client automatically reconnects to the server when you switch between wireless networks or wake your computer from sleep. This guide explains how to install Mosh on your Linode and your personal computer.

Note
Mosh does not support port forwarding or proxying, and you cannot use mosh to copy files or mount remote directories. You’ll still need to use SSH for these tasks.

# Preparing Your Firewall
Before installing Mosh, you should verify that your Linode’s firewall will allow the Mosh client and server to communicate. If you followed our instructions to create a firewall with iptables, you’ll need to edit /etc/iptables.firewall.rules and add another rule to allow the Mosh client to connect to your Linode over UDP ports 60000–61000.

'''
/etc/iptables.firewall.rules

-A INPUT -p udp --dport 60000:61000 -j ACCEPT

Activate the new firewall rule by entering the following command:

sudo iptables-restore < /etc/iptables.firewall.rules
'''
