<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Creating the VM's
- Installing Wireshark
- Observing network traffic with Wireshark

<h2>Actions and Observations</h2>

<p>
<img src="https://imgur.com/tYRYkNT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h2>1. Creating the VM's in Azure</h2>

First we must create 2 VM's to send network traffic between. For the main VM we will be using I am running Windows 10, and for the other VM I used Ubuntu server. 

I created both of these in Azure, but this can be done with any VM application.
</p>
<br />

<p>
<img src="https://imgur.com/wupbYrd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h2>2. Installing Wireshark</h2>
Once completed, boot up the main VM and search download wireshark in google. The installation is pretty straightforward, and once completed wireshark should automatically open. We can now begin sending / receiving data and analyze how protocols work in more detail. 

Since my VM is in Azure, wireshark is automatically running tons of traffic.
</p>
<br />

<p>
<img src="https://imgur.com/KHXBCsY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h2>3. Observing ICMP Traffic</h2>

Now that we have wireshark, let's observe some protocols in action. In windows powershell I ping the IP address of our Ubuntu server and observe what wireshark captures. In the filters on the top of wireshark, you can enter icmp or port == 3389. We do this so wireshark only shows us traffic from our pings. Now we can see in wireshark echo requests are being sent from our IP address (Source IP), and echo replies are coming back from the Ubuntu server (Destination IP). 
</p>
<br />

<p>
<img src="https://imgur.com/NzCt6j8.png" height="80%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/90QcF9e.png" height="80%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h2>4. Observing SSH Traffic</h2>

Next, we will SSH login to the Ubuntu server and observe the traffic wireshark shows us. We do this in Powershell by typing "ssh (username)@(VM's IP)". Immediately after we type this we see Elliptic Curve Deffie-Hellman Key traffic. This is a protocol that establishes a shared secret connection channel between two devices. Next we input the password for the Ubuntu VM, and we are fully logged in. You will now see that the command line changes color and is using bash (linux commands). Anything we type in the terminal will be shown on wireshark. 
</p>
<br />
