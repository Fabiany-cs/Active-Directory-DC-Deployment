# Active Directory DC Deployment
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
  <h1>Description:</h1>
  <p>Welcome to the Active Directory Domain Cntroller Deployment project! This GitHub repository provides comprehensive guidance for downloading the Windows Server 2019 ISO file, setting up an Active Directory Domain Controller (DC) within a virtual machine (VM), configuring user accounts, and automating the creation of additional Active Directory users using PowerShell scripts, and lastly setting up all the aspects of networking (DHCP, NICs, DNS, etc). Through this project, you'll learn how to establish a robust network infrastructure and manage user accounts efficiently using Active Directory.</p>

  <h1>Features:</h1>
  <ul>
    <li><strong>Active Directory Domain Controller Setup: </strong>Step-by-step instructions to configure a Windows Server 2019 VM as an Active Directory Domain Controller, including setting up two NICs—one internal and one external for Wi-Fi.</li>
    <li><strong>Network Configuration: </strong>Configure networking settings to ensure that the Windows 10 Pro client is connected through the DC's internal NIC while receiving internet connectivity through the DC's external facing NIC.</li>
    <li><strong> PowerShell Script for User Creation: </strong>Utilize PowerShell scripts to automate the creation of 1,000 Active Directory users, enabling scalability and facilitating testing of Group Policy Objects (GPOs) and security Identity and Access Management (IAM) settings.</li>
    <li><strong>Windows Server 2019 ISO Download: </strong> Obtain the Windows Server 2019 ISO file from official sources to initiate the deployment process.</li>
  </ul>

  <h1>Overview Architecture:</h1>
    <img width="1032" alt="Architecture Image" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/5f8873cd-5235-4eba-88e3-3e78dad5a19a">


<hr>

<h1>Steps:</h1>

<h2>Downloading Windows ISO Files for VM</h2>
<ol>
    <li>
        <strong>Download Windows Server 2019 ISO:</strong>
        <ul>
            <li>Go to <a href="https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019">Windows Server 2019 Download Page</a> and download the Windows Server 2019 ISO file.</li>
        </ul>
    </li>
    <li>
        <strong>Download Windows 10 ISO:</strong>
        <ul>
            <li>Go to <a href="https://www.microsoft.com/en-us/software-download/windows10ISO">Windows 10 Download Page</a> and download the Windows 10 ISO file.</li>
        </ul>
    </li>
</ol>

<h2>Downloading Oracle VirtualBox</h2>
<ol>
    <li>
        <strong>Download VirtualBox:</strong>
        <ul>
            <li>Go to <a href="https://www.virtualbox.org/wiki/Downloads">VirtualBox Download Page</a> and download the VirtualBox Platform Package corresponding to your local machine.</li>
        </ul>
    </li>
</ol>

<h2>Setting Up DC VM</h2>
<ol>
    <li>
        <strong>Create a New VM:</strong>
        <ul>
            <li>Add the Windows Server 2019 ISO file to the VM.</li>
            <li>Allocate appropriate CPU cores and memory.</li>
        </ul>
    </li>
    <li>
        <strong>Network Options:</strong>
        <ul>
            <li>Add 2 NICs to the VM:
                <ul>
                    <li>1 External for internet access.</li>
                    <li>1 Internal for communication within Active Directory.</li>
                </ul>
            </li>
        </ul>
      <img width="1018" alt="3" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/a2f006ca-44a6-472c-a8b8-183597b14318">
      <img width="743" alt="4" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/a920983b-8d7f-42d7-8688-ec5aecc092e3">
      <img width="744" alt="5" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/72ae143b-7223-4f7d-98c7-f1a160c9d30b">
    </li>
</ol>


<h2>Launching the VM Instance and Creating Admin Login Information</h2>
<ol>
  <li>Follow the on-screen instructions to configure the initial setup of the virtual machine.</li>
  <li>Create your administrative login information (username and password) when prompted.</li>
  <img width="508" alt="7" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/6c35787a-934a-498a-80d8-34e49378cfa0">
  <img width="505" alt="8" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/0ab327a9-8bd3-4f4e-a208-a0f17d4f159b">
</ol>


<h2>Identifying and Setting up both NICs within Windows</h2>
<ol>
  <li>Go to Network Configurations to identify the NAT NIC and the Internal NIC.</li>
    <li>By going to properties, you can see which NIC has a private IP address and which has only an Automatic Private IP Addressing (APIPA) (169.254.x.x) </li>
  <li>Rename the NICs accordingly based on your identification.</li>
  <img width="782" alt="11" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/91109c1b-c376-404e-9b99-1efa3f69bc20">
  <img width="782" alt="12" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/63cc90be-5446-493d-8dee-fca3483325c0">
  <img width="782" alt="13" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/0791fecd-457c-427a-a67d-7c26b53269b8">
</ol>


<h2>Setting Up Internal NIC</h1>
    <ol>
        <li>Assign the static IP address for the Internal NIC</li>
        <li>When you install Active Directory, DNS is automatically set up so we will assign the DNS server with the loopback address. (127.0.0.1)</li>
        <img width="782" alt="14" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/609eb735-b34f-4aa6-85d7-814ad48066fe">
        <img width="782" alt="15" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/b37bc67e-79a2-4b93-a121-ba370cf1a396">
    </ol>


