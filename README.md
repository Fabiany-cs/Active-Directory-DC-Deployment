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


<h2>Rename PC to DC and Restart</h1>
  <ol>
      <img width="782" alt="16" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/be7307a6-236d-4eed-b241-b74e2ff9ba4e">
  </ol>


<h2>Setting up Active Directory</h2>
<ol>
    <li>
        When Server Manager loads, select “Add roles and features”
        <ol>
            <li>Select the DC you just renamed as the server pool.</li>
            <li>Add Active Directory Domain Services and proceed with “Next” and install.</li>
        </ol>
    </li>
  <img width="782" alt="18" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/172f26c8-e0e5-4ccb-bf4f-e15e200695d3">
  <img width="782" alt="19" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/9f123b2b-ba4a-4ad1-b2f8-b3e4e8abd357">
  <img width="782" alt="20" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/a0bd15f2-25df-4279-9a43-5d20d62b1508">
  <img width="782" alt="21" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/4a6165c8-e403-47aa-aa89-05b11137a114">
  <img width="782" alt="22" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/f5ae3182-bfe4-4ff3-b648-4d55
  <img width="782" alt="23" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/d4d278e8-f2ab-4382-82f3-d77cb55a4a5a">
  <img width="782" alt="22" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/e6129487-5af8-4c60-87f3-b18dbd43a076">
  <img width="782" alt="23" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/bbd04c32-cbfd-462f-9d71-9f37079d9fb1">
  <img width="782" alt="24" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/bd515713-c330-4a7b-abd1-ad1a356c66c6">
  <img width="782" alt="25" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/9349fb4a-4034-4b27-9c39-3562e2002949">
  <img width="782" alt="26" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/33b619ff-4500-43d3-a7ea-a0127ce3414d">
</ol>

<h2>Post Deployment Configuration</h2>
<ol>
    <li>
        Select on Post Deployment Configuration
        <ol>
            <li>Add a new Forest to Active Directory</li>
            <li>Name your Root domain (mydomain.com) and add your DC password</li>
            <li>It will restart the machine.</li>
            <li>Notice the new Login Window. It now says Your Domain name and \Admin account</li>
        </ol>
    </li>
  <img width="782" alt="28" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/7c2cef26-0f84-44aa-b06b-e4c1de7ea9c8">
  <img width="782" alt="29" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/41649745-077e-4738-810c-256d3ea35777">
  <img width="782" alt="30" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/2eacb2a0-c3c1-4a52-94ec-929e9c2180b8">
  <img width="782" alt="31" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/c0c55663-6006-4400-aa73-8d2a18f6c153">
  <img width="782" alt="32" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/c78765f9-e4e3-4654-a970-9334406c9609">
  <img width="782" alt="33" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/0b6ac04b-4184-42ba-b5a4-29f141b1828a">
</ol>


<h2>Adding Admin Organizational Unit (OU) in Active Directory</h2>
<ol>
    <li>
        Log in and open Active Directory Users and Computers (ADUC)
        <ol>
            <li>Right-click on your Root Domain and add an OU</li>
            <li>Name it Admins</li>
            <li>Now add a user in the Admins OU</li>
            <li>Since this is only a lab we will have the password never expire. In a production environment, you will definitely want to follow best security practices and have passwords expire and renew after a set period.</li>
            <li>Log out and sign into the new Admin account you just created.</li>
        </ol>
    </li>
  <img width="782" alt="34" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/a08cbb7f-bdaf-4ca1-8f52-a455797d8b6d">
  <img width="782" alt="35" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/24131ff5-8d0c-458a-b387-41e2e6ae8b8f">
  <img width="336" alt="36" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/52f50ff5-c4ad-490c-8cd8-25a5fd5ee912">
  <img width="782" alt="37" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/0db3debe-7cef-44e7-ab8d-b61af241c948">
  <img width="339" alt="38" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/8787a1d3-bacd-45e2-ab32-0bfab15116fd">
  <img width="338" alt="39" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/3c6e7278-91d6-422e-b0cf-886144f15074">
  <img width="782" alt="40" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/20fe852e-d229-4b82-96d9-f1fc8b2531c7">
  <img width="782" alt="41" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/91dd2fc7-2c75-4256-a901-28fcc59b05d0">
  <img width="782" alt="42" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/4c7086f3-8a53-486d-8bbf-cc22034513d6">
  <img width="782" alt="44" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/d18ac6b9-c99b-44a0-887f-de4c7635c600">
</ol>


<h2>Setting up RAS/NAT</h2>
<ol>
    <li>
        Back in Server Manager, select “Add roles and features”
        <ol>
            <li>Select “Remote Access” and follow the steps to configure.</li>
            <li>Select “DirectAccess and VPN (RAS) and Routing</li>
            <li>After adding the feature, select the tools on the top right and select “Routing and Remote Access”</li>
            <li>Right-click on the DC and select “Configure and Enable Routing and Remote Access”</li>
            <li>Select Network Address Translation (NAT)</li>
        </ol>
    </li>
  <img width="782" alt="46" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/7751f3f9-6a82-4dc4-9697-76184dddf848">
  <img width="782" alt="47" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/d5266796-81bd-4b93-9eea-b767363d4894">
  <img width="782" alt="48" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/d5db8d04-2e94-42c4-b342-1330f9d1fb8d">
  <img width="782" alt="49" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/037de75c-2e25-4992-89c6-f50941dc59af">
  <img width="782" alt="50" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/7e293843-3943-4224-a7c4-3d2825f26a5d">
  <img width="782" alt="51" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/82065a30-61e9-43f0-aed1-df98f6446735">
  <img width="782" alt="52" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/c8d1907c-235c-46f7-842e-ed56e40f6cf1">
  <img width="782" alt="53" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/bc17d85c-5f09-4a60-8fe0-07e556b83a91">
</ol>



<h2>Setting up DHCP</h2>
<ol>
    <li>
        Go back to the top right of Server Manager and select Tools then DHCP
        <ol>
            <li>Select the routable NIC-Internet (NOT THE INTRANET)</li>
            <li>Add the feature</li>
            <li>Select DHCP Server and install</li>
        </ol>
    </li>
  <img width="782" alt="54" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/34b3c4c4-eae8-48e6-8458-708e21da67c2">
  <img width="782" alt="55" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/0f55e6a8-661f-43ff-a401-277df006b710">
  <img width="782" alt="56" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/affbb816-9bac-4d0b-abd2-002c6f7bcfe3">
  <img width="782" alt="57" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/5a2d7d34-2209-467f-8d7f-ca76d87f326b">
  <img width="782" alt="58" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/9902a227-6f17-42b7-b2cb-89d7f85433c2">
</ol>



<h2>Adding a DHCP Scope</h2>
<ol>
        <li>Right-click on DHCP IPv4 and add a new scope</li>
        <li>Name the scope (I named it the scope range)</li>
        <li>I assigned a 100 IP address (172.16.0.100-200)</li>
        <li>Subnet /24 (255.255.255.0)</li>
        <li>Add the Default Gateway (router) 172.16.0.1</li>
        <li>Finish Install and right-click on DHCP and authorize the configuration then refresh.</li>
        <li>You will see both IPv4 and IPv6 DHCP servers with a green mark. (Green means good lol)</li>
  <img width="782" alt="59" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/ca5cc6e4-f694-463d-b2b6-a9b2dbd83a64">
  <img width="782" alt="60" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/68366176-e360-462a-9a4a-31e5f5ae44d6">
  <img width="782" alt="61" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/e4692e61-91aa-4c26-83c3-5ed7a4873415">
  <img width="782" alt="62" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/6bcc41ac-13fe-448f-9863-9ea7f98cf675">
  <img width="782" alt="63" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/bfef9843-1374-43af-94b6-de6d33d9fca5">
  <img width="782" alt="64" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/82dc1ae2-69ec-4523-a0a4-231f89775369">
  <img width="782" alt="65" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/0d959786-a648-498f-bdb3-3bdb2161f1f8">
  <img width="782" alt="66" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/fe6a980c-361d-4e21-a09f-bc47a878afb7">
  <img width="782" alt="67" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/636afb2e-a6f6-4ccd-9a9c-57b8762447e4">
</ol>

<h2>Creating 1,000 Users with PowerShell Script</h2>
<ol>
    <li>Open PowerShell ISE as Administrator</li>
    <li>Download the 1_CREATE_USERS.ps1 and names.txt from my repository:
        <ul>
            <li><a href="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/blob/main/1_CREATE_USERS.ps1">1_CREATE_USERS.ps1</a></li>
            <li><a href="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/blob/main/names.txt">names.txt</a></li>
        </ul>
    </li>
    <li>Open the PowerShell script within PowerShell ISE</li>
    <li>Run the command: <code>Set-ExecutionPolicy Unrestricted</code></li>
    <li>Accept Yes to all</li>
    <li>Change the directory within the terminal to where you have downloaded the files (cd)</li>
    <li>Press the Green Run button</li>
    <li>Select Run Once</li>
    <li>See all of the users being created within AD</li>
    <li>Open Active Directory Users and Computers (ADUC) and refresh the _USERS OU to see all the users populate</li>
  <img width="782" alt="71" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/55e22fc8-18f1-49b5-ac19-b4e8fc3cdb58">
  <img width="782" alt="72" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/4694adb2-616a-4226-945d-ba0a654c1599">
  <img width="782" alt="73" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/2a932be3-55aa-4e42-a600-2f8146f2d0b3">
  <img width="782" alt="74" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/49aaaca3-b16c-4ced-a342-0bfdeedeb73a">
  <img width="782" alt="76" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/291db94b-881f-4b24-819b-dfb44a9ddd79">
  <img width="782" alt="77" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/f9bb2155-6357-4469-be2e-a9e51389250f">
  <img width="782" alt="78" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/39fab3c4-97bf-47ba-bdb5-633d2341caff">
  <img width="782" alt="79" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/7ff75cf2-8f6b-464a-87bb-ba5967248c3e">
  <img width="782" alt="80" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/e77995a7-ee25-4432-b95a-c05bc37ca4b8">
</ol>



<h2>Create Another VM with the Windows 10 ISO File</h2>
<ol>
    <li>
        Set the network adapter to internal only (Cannot have internet connectivity)
        <li>When installing, select Windows 10 Pro since we will be connecting it to the DC</li>
        <li>Select "I do not have internet" and create the account</li>
    </li>
  <img width="745" alt="82" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/00026c80-1947-4b7c-b712-7fd6ba84ca84">
  <img width="735" alt="83" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/2f15566d-2b27-4861-a46c-631537d8a99d">
  <img width="511" alt="85" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/04804624-67ba-4add-b99d-4f7af283f7bf">
  <img width="782" alt="87" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/31904915-b001-41f1-8b3e-c4683a8906a9">
  <img width="782" alt="89" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/ec148e99-745e-4bc8-adf1-3a603403f7d8">
</ol>


<h2>Reviewing DHCP IPv4 Address Leases and ADUC</h2>
<ol>
    <li>
        Go back to the DC VM and go to DHCP settings within Server Manager
        <ol>
            <li>Go to IPv4 > Scope > Address Leases and you can see the machine that was just added to the domain</li>
        </ol>
    </li>
    <li>
        Open Active Directory Users and Computers (ADUC) and go to Computers
        <ol>
            <li>You can see the newly added client as well</li>
        </ol>
    </li>
  <img width="529" alt="Screenshot 2024-05-09 at 3 23 47 PM" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/76947b37-f72d-4064-8f69-faed72ce95a2">
  <img width="271" alt="Screenshot 2024-05-09 at 3 24 49 PM" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/6077ca55-39ec-4df0-a8e6-0c6670253678">
  <img width="350" alt="Screenshot 2024-05-09 at 3 25 59 PM" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/e1d449c2-98d9-458f-8b7c-7b0358ed3552">
  <img width="197" alt="Screenshot 2024-05-09 at 3 26 14 PM" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/9c517fbf-a476-478c-b167-fe00109107e8">
  <img width="337" alt="Screenshot 2024-05-09 at 3 28 56 PM" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/55b7d752-aec9-46d0-8b0a-1187a10053b2">
  <img width="498" alt="Screenshot 2024-05-09 at 3 29 59 PM" src="https://github.com/Fabiany-cs/Active-Directory-DC-Setup/assets/107880960/e03fad16-8c5d-4de0-922c-00d611543e03">
</ol>


