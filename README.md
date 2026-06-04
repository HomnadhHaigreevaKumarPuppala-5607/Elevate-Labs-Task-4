# Elevate Labs Cyber Security Internship - Task 4

## Objective
Configure and test basic firewall rules to allow or block traffic. 

## Tools Used
* Linux Terminal
* UFW (Uncomplicated Firewall)

## Steps Completed

1. **Firewall Initialization:** Checked the status of UFW and ensured it was installed.
2. **Allowed SSH:** Added a rule to allow SSH traffic on port 22 (`sudo ufw allow 22/tcp`) to prevent losing access to the machine.
3. **Enabled UFW:** Turned on the firewall to begin filtering traffic.
4. **Blocked Port 23:** Added an inbound rule to explicitly deny traffic on port 23 for Telnet (`sudo ufw deny 23/tcp`).
5. **Tested the Rule:** Attempted to connect to port 23 locally using `telnet localhost 23`. The firewall successfully blocked the traffic, returning a "Connection refused" error. (See attached screenshot).
6. **Restored State:** Removed the test block rule (`sudo ufw delete deny 23/tcp`) to restore the system to its original state.

---

## How a Firewall Filters Traffic
A firewall acts as a digital gatekeeper, inspecting incoming and outgoing network traffic based on a set of predefined security rules. It filters traffic primarily by examining the data packets' headers, looking at the source and destination IP addresses, the protocol being used (like TCP, UDP, or ICMP), and the port numbers. If a packet matches a "deny" rule, the firewall drops or rejects it. If it matches an "allow" rule, the traffic is permitted to pass through.

---

## Interview Questions & Answers

**1. What is a firewall?**
A firewall is a network security device or software that monitors, filters, and controls incoming and outgoing network traffic based on established security policies.

**2. Difference between stateful and stateless firewall?**
* **Stateless:** Inspects each individual packet in isolation against a set of rules (like IP and port) without context. It doesn't know if a packet is part of an ongoing conversation.
* **Stateful:** Tracks the active state and context of network connections. It remembers if a packet is part of an established connection, making it smarter and more secure against spoofing attacks.

**3. What are inbound and outbound rules?**
* **Inbound rules:** Dictate what external traffic is allowed to enter the network or device. 
* **Outbound rules:** Dictate what internal traffic is allowed to leave the network and go out to the internet or other networks.

**4. How does UFW simplify firewall management?**
Linux natively uses `iptables` or `nftables`, which have highly complex syntax. UFW provides a very simple, user-friendly command-line interface that translates human-readable commands into those complex backend rules.

**5. Why block port 23 (Telnet)?**
Telnet is an obsolete and highly insecure protocol. It transmits all data—including usernames and passwords—in plain text. Anyone intercepting the network traffic can easily read these credentials. 

**6. What are common firewall mistakes?**
* Creating overly permissive rules (e.g., "Allow All" for testing and forgetting to remove it).
* Locking yourself out by enabling the firewall without first allowing management ports like SSH (Port 22).
* Placing rules in the wrong order (a broad "allow" rule placed above a specific "deny" rule will render the deny rule useless).

**7. How does a firewall improve network security?**
It acts as the first line of defense, reducing the attack surface by blocking unauthorized access, stopping malicious traffic, and preventing vulnerable services from being exposed to the public internet.

**8. What is NAT in firewalls?**
NAT (Network Address Translation) is a process where a firewall translates multiple private, internal IP addresses into a single public IP address before sending traffic out to the internet. This hides the internal network structure and conserves the limited pool of public IPv4 addresses.
