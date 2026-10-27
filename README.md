# Kali Linux Static IP Configuration

## 1. Objective

To configure a static IPv4 address on Kali Linux using Oracle VirtualBox and NetworkManager.

## 2. Lab Environment

* **Operating System:** Kali Linux
* **Virtualization Software:** Oracle VirtualBox
* **Network Mode:** NAT Network
* **Network Name:** NatNetwork
* **Network Subnet:** `10.0.0.0/24`
* **Required IP Address:** `10.0.0.2/24`
* **Network Interface:** `eth0`

## 3. Procedure

### Step 1: Configure the VirtualBox Network

1. Open Oracle VirtualBox.
2. Select the Kali Linux virtual machine.
3. Navigate to **Settings → Network → Adapter 1**.
4. Enable the network adapter.
5. Set the network mode to **NAT Network**.
6. Select `NatNetwork` and ensure the virtual cable is connected.

### Step 2: Identify the Network Interface

Run the following command to view the available network interfaces and their IP addresses:

```bash
ip addr
```

The Ethernet interface used in this practical was `eth0`.

### Step 3: Identify the Network Connection

Run:

```bash
nmcli connection show
```

The connection profile used was `Wired connection 1`.

### Step 4: Configure the Static IP Address

Run the following command to assign the required IPv4 address:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.method manual ipv4.addresses 10.0.0.2/24
```

This sets the connection to use a manually configured IPv4 address.

### Step 5: Activate the Network Connection

Run:

```bash
sudo nmcli connection up "Wired connection 1"
```

This activates the connection using the saved configuration.

### Step 6: Verify the IP Address

Run:

```bash
ip -4 addr show eth0
```

The expected IPv4 address is:

`10.0.0.2/24`

## 4. Key Learnings

* Configuring static IPv4 addresses in Kali Linux.
* Identifying network interfaces using Linux commands.
* Managing network connections with NetworkManager.
* Understanding subnet prefixes and virtual network configuration.
* Troubleshooting network connectivity.

## 5. Conclusion

This practical provided hands-on experience with static IP configuration, NetworkManager, and virtual networking in Kali Linux using Oracle VirtualBox.
