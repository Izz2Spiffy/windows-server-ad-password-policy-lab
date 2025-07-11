# windows-server-AD-password-policy-lab
A complete, beginner-friendly Windows Server 2022 lab built from scratch using VirtualBox. Includes Active Directory setup, domain configuration, DNS, and a full password policy audit using Group Policy. Designed to simulate a real-world enterprise environment.


### 🖼️ Screenshot 01 – Renaming the Computer

In this step, I renamed the default computer name (`DC-WINSERVER2022`) to `DC-CYBERLAB` as part of the post-installation configuration.

Renaming the server to something meaningful helps with identification — especially when managing multiple servers in a real-world domain environment. Using a prefix like `DC-` (Domain Controller) makes it clear that this server will be responsible for managing domain authentication and directory services.

📍 **Command-line Setup Tool:** This is part of the initial Windows Server Setup screen shown after installation, before the full GUI environment loads.

### 🖼️ Screenshot 02 – Initial Server Setup via SConfig

After the Windows Server 2022 installation completed, I was brought to the **SConfig** (Server Configuration) menu. This command-line utility allows you to configure key server settings before launching the desktop GUI.

From this screen, I verified:
- The computer name change (now shows as `DC-CYBERLAB`)
- That the system is in **Workgroup mode** (default before domain promotion)
- Remote management was enabled

🔧 Other available configuration options from this screen include:
- Setting a static IP address
- Enabling Remote Desktop
- Installing updates
- Joining a domain or changing to a new workgroup
- Accessing PowerShell to install additional features

This menu simulates how **real-world system administrators** often configure headless servers, especially in secure or remote environments where GUI access isn’t always available.

📝 **Tip:** You can type the number for any menu item to access its configuration screen. For example, typing `8` accesses **Network Settings**.

### 🖼️ Screenshot 03 – Viewing Network Adapter in SConfig

After selecting option `8` from the SConfig menu, I was shown a list of available network adapters. This screen confirms which network interfaces are installed and currently active.

In this case:
- **Index #**: 1
- **IP Address**: 10.0.2.15 (assigned via DHCP)
- **Adapter**: Intel(R) PRO/1000 MT Desktop Adapter (default VirtualBox NIC)

📌 This screen is important because it allows you to:
- Select which adapter to configure
- Set a **static IP** (important for domain controllers)
- Configure **DNS** settings

🔧 To proceed, you type the **index number** for the adapter you want to configure — in my case, `1`.

### 🖼️ Screenshot 04 – Set Static IP and DNS Server (Before Promotion)

Once I selected my network adapter (`Index 1`), I was given the following options:

1. Set network adapter address
2. Set DNS servers
3. Clear DNS server settings

✅ As a best practice for domain controllers and any critical infrastructure, **a static IP address is required**. DHCP-assigned addresses can change over time, which would break name resolution and trust relationships in the domain.

---

#### Why this matters in the real world:
- **Static IP** ensures stability for domain services, DNS, and GPO distribution
- Helps other devices on the network consistently reach this server
- Prepares the server for **Active Directory promotion**

🛠️ **What I did next:**
- Selected option `1` to begin configuring the static IP, subnet mask, and default gateway.
- I then continued with option `2` to specify a preferred DNS server.
