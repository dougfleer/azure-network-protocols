<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used</h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

1. Create and Configure Azure Virtual Machines.
2. Configure Network Security Groups.
3. Capture and Analyze Traffic with Wireshark.
4. Test NSG Rules and Observe Behavior.

<h2>Actions and Observations</h2>

### Step 1: Create and Configure Azure Virtual Machines
1. Deploy a **Windows 10** VM and an **Ubuntu Server 20.04** VM in the same virtual network.
2. Assign static private IPs to both VMs.
3. Ensure both VMs are in the same resource group for ease of management.

### Step 2: Configure Network Security Groups (NSGs)
1. Create an NSG and associate it with the subnet containing the VMs.
2. Add the following rules:
   - Allow inbound SSH traffic (TCP 22) to the Ubuntu server.
   - Allow inbound RDP traffic (TCP 3389) to the Windows VM.
   - Allow ICMP traffic for testing pings.
3. Test the rules by attempting to connect between the VMs using allowed protocols.

### Step 3: Capture and Analyze Traffic with Wireshark
1. Install Wireshark on the Windows VM.
2. Start a packet capture on the Ethernet interface.
3. From the Ubuntu server, initiate ICMP, SSH, and HTTP traffic to the Windows VM.
4. Observe the captured packets in Wireshark to identify protocol behavior and patterns.

### Step 4: Test NSG Rules and Observe Behavior
1. Modify the NSG to block inbound ICMP traffic.
2. Test by attempting to ping the Windows VM from the Ubuntu server.
   - Observe that the pings fail due to the new rule.
3. Re-enable ICMP traffic in the NSG.
   - Confirm that pings now succeed.
4. Experiment with additional protocols (e.g., DNS queries) and observe traffic behavior.

By completing this lab, you will gain practical knowledge of using Network Security Groups to control traffic and analyzing network activity with Wireshark. This tutorial demonstrates proficiency in network configuration and security in cloud environments.
