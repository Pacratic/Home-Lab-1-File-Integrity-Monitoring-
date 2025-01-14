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

Set Network to Bridge Mode: <br />

Select the imported Wazuh virtual machine in VirtualBox. <br />

Click Settings > Network. <br />

Under Adapter 1, ensure that: <br />

Enable Network Adapter is checked. <br />

Attached to is set to Bridged Adapter. <br />

Choose the correct network interface of your host machine (e.g., Ethernet or Wi-Fi). <br />

This configuration allows the virtual machine to obtain an IP address on the same network as your host machine, enabling direct access. <br />
<br />

![image](https://github.com/user-attachments/assets/1fe74df4-8fcd-40a6-aa73-26cec8dcf605)

<br />
<br />

<h2> Step 3: Log In to Wazuh CLI and Access the Web Interface</h2>
<br />
Log In to the Wazuh CLI: <br />
Open the Wazuh virtual machine console in VirtualBox. <br />

Use the default credentials to log in: <br />

Username: wazuh-user <br />
Password: wazuh <br />

Now that the login has been accepted we now need to run the ifconfig command <br />
<br />
![image](https://github.com/user-attachments/assets/0dfda170-e7f3-4593-88c1-87488d9346a1)
<br />
<br />

Access the Wazuh Web Interface: <br />

Open your favorite web browser on the host machine. <br />

Enter the following URL, replacing <WAZUH_IP_ADDRESS> with the IP address you retrieved: Enter the following URL into your web browser, replacing <WAZUH_IP_ADDRESS> with 10.0.0.94 <br />

![image](https://github.com/user-attachments/assets/49128055-9c8d-43d1-8aef-2d012166556b)
<br />
<br />

Use the default credentials: <br />

Username: admin <br />
Password: admin <br />

Once you log in, you'll have access to the Wazuh dashboard to begin configuring and managing your system. <br />

![image](https://github.com/user-attachments/assets/900bf255-14b4-4fc0-b07d-22b74e987d25) 
<br />
<br />

Deploy a New Agent: <br />

In the Wazuh GUI, go to the Agents section. <br />
Click on Deploy new agent. <br />

![image](https://github.com/user-attachments/assets/28a54f0c-a444-4edf-ba62-da1422762e1c)
<br />
<br />


Configure Agent Installation:

Select Windows as the operating system. <br />

Enter your Wazuh Server's IP address (e.g., 10.0.0.94). <br />

Set an agent name (e.g., WindowsAgent01). <br />

![image](https://github.com/user-attachments/assets/21dff221-f4f9-4437-89f1-2927c5602b8c)
<br />
<br />

Get the PowerShell Script: <br />

The Wazuh platform will generate a PowerShell script for installation. <br />

Copy the script to your Windows machine.<br />

![image](https://github.com/user-attachments/assets/36150b0c-3904-4223-93ad-ab530dcf836b)
<br />
<br />
Run the PowerShell Script on Windows:

Open PowerShell on your Windows machine with administrator privileges: <br />

Press Win + X and select Windows PowerShell (Admin). <br />
Paste the copied script into the PowerShell window and run it. <br />

![image](https://github.com/user-attachments/assets/f0c5ff09-05b8-45e7-b22d-a9534e99b818)
<br />
<br />

Start the Wazuh Agent Service: <br />

Once the script completes, you will also be provided with a command to start the Wazuh Agent service. <br />

Run the provided command in PowerShell to activate the agent. <br />


Verify the Agent Status:<br />

Return to the Wazuh GUI on your browser.<br />

In the Agents section, ensure your newly added agent appears in the list and is marked as Connected.<br />

![image](https://github.com/user-attachments/assets/5064d7a4-1476-463e-a29d-82d0d2cb8886)
<br />
<br />

<h2>Lets configure the Wazuh agent to monitor the System32 folder</h2>

The Wazuh Agent Manager is the configuration file for the agent running on the machine you want to monitor. You’ll need to edit the configuration directly on the machine where the Wazuh Agent is installed.<br />

Steps to Access the Agent Manager Configuration: <br />

Log in to the Machine Running the Wazuh Agent <br />

Locate the Program Files lised for the ossec-agent <br />

Once found open the text editor within this file <br />

The <directories> tags in the <syscheck> block define the files and directories being monitored. To include the System32 directory for file integrity monitoring, you need to add an additional <directories> entry. <br/>

![image](https://github.com/user-attachments/assets/eed12355-fe71-4217-b4d4-5fd943c6031d)
<br/>
<br/>
After rebooting the Wazuh app, we can see the implemented changes have now taken effect. Further changes can be done so this can be vizualized to better assist!<br />











