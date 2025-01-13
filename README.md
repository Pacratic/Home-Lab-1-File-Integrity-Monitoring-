# Home-Lab-1-File-Integrity-Monitoring-

<h1>Home Lab #1 Setting up file integrity monitoring</h1>



<h2>Why Is File Integrity Important?:</h2>

File Integrity Monitoring (FIM) plays a crucial role in maintaining the security and integrity of a system by actively detecting and alerting on unauthorized changes to critical files. Here's why FIM is an essential cybersecurity tool:<br />

<h2> Detecting Unauthorized Changes</h2>

FIM identifies and notifies users when critical system files are altered without authorization, helping prevent potential security breaches and ensuring system stability.<br />

<h2> Meeting Compliance Requirements </h2>

Many regulatory standards, such as PCI DSS, HIPAA, and GDPR, mandate the use of FIM as part of an organization's compliance framework to protect sensitive data.<br />

<h2> Mitigating Insider Threats </h2>

By monitoring changes made by internal users, FIM can detect potential insider threats, enabling organizations to respond quickly and effectively to suspicious activity.<br />

Implementing FIM demonstrates a proactive approach to system security and regulatory compliance, making it a cornerstone of any robust cybersecurity strategy. <br />

<h1> Requirements:</h1>

 -Oracle VirtualBox Manager<br />
 -Windows10 VM <br />
 -Wazuh OVA File <br />
<br />

<h2> Step 1: Install Wazuh </h2>
For setting up your home lab, using the Wazuh OVA (Open Virtual Appliance) file is a straightforward and convenient option. The OVA file simplifies deployment by providing a pre-configured virtual machine image.<br />
<br/>
<br/>
<h2>Step 2: Configure and Start Wazuh Virtual Machine in VirtualBox</h2> 

Once you have downloaded the Wazuh OVA file, follow these steps to set it up and ensure proper connectivity:<br />

Import the OVA File:<br />
Open VirtualBox. <br />
Go to File > Import Appliance. <br />
Select the downloaded Wazuh OVA file and click Next. <br />
Adjust the virtual machine settings as needed (e.g., memory or CPU allocation). <br />
Click Import to complete the process. <br />
<br />
2. Set Network to Bridge Mode: <br />
Select the imported Wazuh virtual machine in VirtualBox. <br />
Click Settings > Network. <br />
Under Adapter 1, ensure that: <br />
Enable Network Adapter is checked. <br />
Attached to is set to Bridged Adapter. <br />
Choose the correct network interface of your host machine (e.g., Ethernet or Wi-Fi). <br />
This configuration allows the virtual machine to obtain an IP address on the same network as your host machine, enabling direct access. <br />
<br />
<img src="https://imgur.com/a/HXYdxso.png" height="80%" width="80%" alt=""/>
<br />
<br />
3. Start the Virtual Machine:
Click Start in VirtualBox to power on the Wazuh virtual machine.
Once it boots up, you should see the IP address assigned to the virtual machine.
4. Access from Host Machine:
Open a web browser or terminal on your host machine.
Use the IP address displayed in the virtual machine to access the Wazuh dashboard or services.
