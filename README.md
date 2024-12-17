
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites, Setup, and Installation</h1>
This guide details the necessary requirements and steps for installing osTicket, an open-source help desk ticketing system.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> 

<h2>List of Prerequisites</h2>

- IIS
- PHP Manager
- VC_redistx86
- MySQL 5.5.62
- Rewrite Module
- Heidi SQL

<h2>Installation Steps</h2>

<p>
</p>
<p>
<h3>&#9312; Create a Virtual Machine on Azure</h3>
The first step is to create a virtual machine on Azure. 
Choose the image or base operating machine as Windows 10 Pro, version 22H2.</p>
<p>
<img width="758" alt="VM setup-windows 10" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/301682469-a22b387c-d396-4fe5-8db9-7c2677941a30.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153831Z&X-Amz-Expires=300&X-Amz-Signature=a1447f37e6eda0a1efb144f9d5627e50d31fad4899757c29fb287c1f33b3122b&X-Amz-SignedHeaders=host">

<p>
</p>
<p>
<strong> NOTE: Make sure to set the size to at least 2 vcpus and 16 GiB memory. 
And confirm that RDP (3389) is allowed in "Select inbound ports" in order to allow Remote Desktop access to the VM.</strong> </p>
<p>
<img width="757" alt="VM inbound ports" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/301682957-3eb204b9-a099-4656-a4ec-9d8badb1f56b.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153904Z&X-Amz-Expires=300&X-Amz-Signature=ab8c2cc466b1f209ea736546777df73317380f522c3e4a327094d264e7b4f369&X-Amz-SignedHeaders=host">



</p>
<br />

<p>
</p>
<p>
<h3>&#9313; Review and Create </h3>
<p>Click on the last check box to confirm an eligible Windows 10 license then proceed to "Review + create". A validation process will occur then once it has passed simply continue to create.</p>

</p>
<br>
<h3>&#9314; Find your VM's public IP address</h3>
<p></p>Allow some time for your deployment to complete then find your VM's public IP address and copy it.</p>
<p>
<img width="1009" alt="VM IP ADDRESS" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302405031-9b3ffb24-60c9-421d-a22e-c4035c1b9fe4.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T154042Z&X-Amz-Expires=300&X-Amz-Signature=02fb0e0374789c675593c8a45e81f0814b8aac7357661b9c33d7ef48ac3a20ea&X-Amz-SignedHeaders=host">


</p>
<p>
<h3>&#9315; Connect to your VM using the Remote Desktop Connection app</h3>
<p>Open your Remote Desktop Connection app and paste the VM's IP and login with the same login credentials used to create the VM.</p>
<p>
<img width="302" alt="Remote desktop app" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/301684901-f331b259-db5b-447d-a05c-0367ef4297a0.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T152656Z&X-Amz-Expires=300&X-Amz-Signature=1cd951faaddf69b5efbf52d346c93eae77c195cea65d6f4843c70fb2dca8fa77&X-Amz-SignedHeaders=host">


</p>
<br />
<h3>&#9316; Enable IIS </h3>
<p> Once the VM is open, we will have to install / enable IIS. Go to the Control Panel and open the programs applet. Under programs, select "Turn Windows features on or off".</p>
<p> <img width="552" alt="CONTROL PANEL PROGRAMS" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302407163-52defb88-4165-4b34-bbea-8292bc2890c8.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T152718Z&X-Amz-Expires=300&X-Amz-Signature=b7708fcb4e40f69b4a0351a221984c233c339012f3b79f9e6c2617ceecf4ad17&X-Amz-SignedHeaders=host">

  
</p>
<p>Then you will have to enable and expand the following features:</p>
<p><img width="295" alt="Checklist 2" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302408261-0b7b096f-43e7-47a8-a3ef-5500a360453d.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T152736Z&X-Amz-Expires=300&X-Amz-Signature=6c1a4b0b62e8ed62edf4589b7261d5e1cbdc2897f0268e9499478e03d127c0c1&X-Amz-SignedHeaders=host">
</p>
<p> [X] Internet Information Services</p>
<p>[X] Web Management Tools </p>
<p>[X] IIS Management Console </p>
<p>[X] World Wide Web Services  </p>
<p>[X] Application Development Features </p>
<p>[X] CGI</p>
<p>[X] Common HTTP Features</p>
<br>
<p> Click okay and the features should be enabled.</p>
<br>
<p> <strong> NOTE: To quickly test if the changes were applied succesfully, simply type 127.0.0.1 on your browser and the page below should appear. </strong></p>
<img width="1094" alt="WINDOWS IIS" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302409256-4836fb28-6fcf-403d-853b-f412c707295c.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T152827Z&X-Amz-Expires=300&X-Amz-Signature=1ecfb3af7d7f26355cc87c05fb2854f871420ad6e59c0f364a9f87e0dc150e07&X-Amz-SignedHeaders=host">
<br> <br>
<h3>&#9317; Download and Install PHP Manager</h3>
<p> Simply download and install PHP manager from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a>(PHPManagerForIIS_V1.5.0.msi) 
</p> <br>
<p><img width="386" alt="PHP Manager" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302409947-566a1c1c-3731-4ff7-a74c-10a21b84a851.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T152848Z&X-Amz-Expires=300&X-Amz-Signature=af9c32e5bddd6f4579d0683332771c29ed673b2552546ee837664b6bc7e58f86&X-Amz-SignedHeaders=host">
</p> 
<br>
<h3>&#9318; Download and Install the Rewrite Module</h3>
<p> Download and install the rewrite module (rewrite_amd64_en-US.msi) from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a> </p>
<p><img width="386" alt="rewrite module" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302415097-177cc396-71e3-4658-9084-3e6fae94c1a5.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T152911Z&X-Amz-Expires=300&X-Amz-Signature=69c670bd5ee35ef386f843330aadbed5495762dcac83ec7bad8f8b2c47b10d88&X-Amz-SignedHeaders=host"></p>
<h3>&#9319; Create a new directory</h3>
<p>Proceed to File Explorer and create the directory C:\PHP </p>
<img width="647" alt="PHP" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302417245-683aa120-d73c-4bce-bf6d-f58309fdac5c.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T152928Z&X-Amz-Expires=300&X-Amz-Signature=ab8a739582d39400ad571c1bd96f2e8d2bfa7ca4c07ef44cb941472c5eb480e5&X-Amz-SignedHeaders=host">
<br>
<br>
<h3>&#9320; Download and install php-7.3.8-nts-Win32-VC15-x86.zip </h3>
<p> Download and install php-7.3.8-nts-Win32-VC15-x86.zip from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a> and unzip the contents into the newly created C:\PHP </p>
<img width="631" alt="PHP zip" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302418830-b43949f3-78a7-4ab8-a526-dfd4f159d2d6.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153001Z&X-Amz-Expires=300&X-Amz-Signature=f01d3ef38d927cb3b8e44b856ea7606a62dfb5c4d9dce5e437dc9506ffd13e1a&X-Amz-SignedHeaders=host">
<br>
<h3>&#9321; Download and install VC_redist.x86.exe </h3>
<br>
<h3>&#9322; Download and install MySQL 5.5.62 </h3>
<p> Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a>  and select the following configurations; </p>
<p> [X] Typical Setup</p>
<p>[X] Launch Configuration Wizard after install </p>
<p>[X]Standard Configuration 
</p>
<br>
<img width="383" alt="mysql" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302419946-964a5ada-7d58-4efd-a0f2-6744610d999d.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153018Z&X-Amz-Expires=300&X-Amz-Signature=b52a81675c44f788b8bcd01845ed51a21f5b6a9ecc63878a917568512ebcbd0d&X-Amz-SignedHeaders=host">
<br>
<h3>&#9323; Launch IIS as an administrator</h3>
<p> Search for IIS in the windows search bar and right click it and select open as administrator</p>
<br>
<h3>&#9324; Register PHP Manager </h3>
<br>
<img width="682" alt="PHP registration 2" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302426016-a3282eb4-90ea-474b-9259-33bfa4d01957.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153042Z&X-Amz-Expires=300&X-Amz-Signature=4253872cb60ea805640ab2fa51063eb1c1363e1152e944d0ee7bf9dc9548591f&X-Amz-SignedHeaders=host">

<br>
<br>
<p><strong> NOTE: Registration will require you to provide a path to "php-cgie.exe". Simply lead it to the PHP folder previously created and you will find the file it is asking for. 
</strong></p>
<br>
<img width="623" alt="PHP path " src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302423055-ac6d2463-c9ef-4803-b3d6-3e5d4a9bc177.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153100Z&X-Amz-Expires=300&X-Amz-Signature=f2ff8074d72be34c6de35053f4ec08e338078f57a6769c8953a5cb25f667201e&X-Amz-SignedHeaders=host">

<br>
<p>
</p> 
<h3>&#9325; Restart the IIS server</h3>
<p> The restart button can be found on the right side of the window.</p>
<br>
<img width="623" alt="Restart IIS" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302425425-89c60a3c-2556-4909-ad78-4ae501b38da1.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153117Z&X-Amz-Expires=300&X-Amz-Signature=f4cafba4685c2d7b684dcd51d415c80a7f94e13a2e99c51a59685b36ac29ee10&X-Amz-SignedHeaders=host">
<br>
<br>
<h3>&#9326; Download and install osTicket</h3>
<p> Download and install osTicket v1.15.8 from the installation files and extract the contents to c:\inetpub\wwwroot </p>
<br>
<img width="547" alt="inetpub" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302426826-bea57cd3-27f4-4564-9cb4-1bfd7492b6ca.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153133Z&X-Amz-Expires=300&X-Amz-Signature=1f3cfb0231d61f2f32d231247139374fa2c933d3c9568f3b02700387120f1ff9&X-Amz-SignedHeaders=host">
<p> Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”</p>
<br>
<br>
<h3>&#9327; Restart the IIS server again.</h3>
<img width="623" alt="Restart IIS" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302425425-89c60a3c-2556-4909-ad78-4ae501b38da1.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153204Z&X-Amz-Expires=300&X-Amz-Signature=3741e64adde0c60673a09b9b4f5e79e0716a9199f101f7471cda8555cd3ee35e&X-Amz-SignedHeaders=host">
<br>
<br>
<h3>&#9328; Launch osTicket </h3>
<p>On the left hand side of IIS, Expand on the VM name -> Sites - > Default Website -> osTicket </p>
<img width="623" alt="osTicket" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302429090-93165771-1d49-430c-a66a-cc2cf3c87e93.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153223Z&X-Amz-Expires=300&X-Amz-Signature=0d88cc8ef9ad4cd16aec1ed678ce6ff2108d4b5c29c3023f553218948dd1bfb3&X-Amz-SignedHeaders=host">
<p></p>
<p><strong>NOTE: Make sure to click on osTicket</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<h3>&#9329; Click on Browse *80 to launch osTicket</h3>
<p> On the right side of the window, click on browse *80 </p>
<img width="623" alt="browse80" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302430152-53e70118-0357-4f5e-aa56-77560edec238.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153238Z&X-Amz-Expires=300&X-Amz-Signature=9b2ca184111dfb158ab42d46801603ea1cddcda7f226175d5a745897acec967c&X-Amz-SignedHeaders=host">
<br>
<br>
<br>
<p><strong>This should then lead to your browser opening osTicket</strong>.</p>
<br>
<br>
<img width="664" alt="osTicket browser" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302437901-258689e2-a099-43e1-a555-a70eb7ad1e9d.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153300Z&X-Amz-Expires=300&X-Amz-Signature=7dd58cee1fcd7145be5a01f2bc3c35eeb6fa3fac1b40c554548417aea57bd91b&X-Amz-SignedHeaders=host">
<br>
<br>
<br>
<h3>&#9330; Enable extensions</h3>
<p>Open IIS and click on PHP Manager and select "enable or disable extension". </p>
<p>Enable the following extensions:</p>
<p>[X]Enable: php_imap.dll</p>
<p>[X]Enable: php_intl.dll</p>
<p>[X]Enable: php_opcache.dll</p>
<img width="273" alt="php enable 2" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302439204-f384957a-2228-47d9-9249-987c929eb691.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153321Z&X-Amz-Expires=300&X-Amz-Signature=8e61bc0e30143cbd06830b6d2021c18d60e9b6875780d30a95f9807cde81d31f&X-Amz-SignedHeaders=host">
<br>
<br>
<br>
<h3>&#9331; Refresh osTicket</h3>

<p>Refresh the osTicket page on the browser and notice some extensions will now appear active.</p>
<img width="608" alt="OSticket changes" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302439729-5d6aded2-86bf-44b8-b20f-5035e912cd44.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153338Z&X-Amz-Expires=300&X-Amz-Signature=86a0a5fb68f5a0ec55b5bdfc47e42c7c647268c983a514ef640efac8ad33686e&X-Amz-SignedHeaders=host">
<br>
<br>
<br>

<h3>&#12881; Rename ost-config.ph</h3>

<p> Under C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php, rename "ost-sampleconfig.ph" to "ost-config.ph"</p>
<img width="527" alt="ostconfig rename" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302440181-1dcd19e8-6b76-4d83-9d59-17dc4ef5b28f.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153354Z&X-Amz-Expires=300&X-Amz-Signature=e7bedec21c39c45a5f68050669c73eafece5a80d49685c4b1d3e4066f7cb4dd5&X-Amz-SignedHeaders=host">
<br>
<br>
<br>

<h3>&#12882; Change ost-config.ph permissions</h3>

<p>Change ost-config.php permissions by right clicking and selecting</p>
<p>Properties -> Security -> Advance -> Disable inheritance</p> 
<p>Select remove all inherited permissions and add everyone as a principal. Select all boxes to ensure all permissions are granted. </p>
<img width="571" alt="Permissions" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302441216-d634bc06-dcc0-4b41-814d-1f7de0afa0bf.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153408Z&X-Amz-Expires=300&X-Amz-Signature=aa3b1dd1f060863ac95a855d2ba699fd7b19751d03fc7cae027d2bc87516ed29&X-Amz-SignedHeaders=host">
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12883; Continue osTicket installation</h3>

<p> Continue the osTicket installer on your browser by filling the first half of the page.</p>
<img width="611" alt="osticket signup" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302443939-1df4ef77-85f3-4f36-bf93-44ce3e910d64.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153426Z&X-Amz-Expires=300&X-Amz-Signature=fceeb6c6200e80e62f922a507197d603d01f9466fe3af898cc5b8980c52c7937&X-Amz-SignedHeaders=host">
<br>
<br>
<p><strong>NOTE: Don't worry about the database credentials. We'll fill those out later.</strong> </p>
<br>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12884; Download and install Heidi SQL from the installation files</h3>

<p>Open Heidi SQL and create a new session. Make sure to fill in the username as root and create a password. After filling up your credentials now click open and a new session should show up.
</p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12885; Create new database </h3>

<p>On the left side of the window, right click on "Unnamed" and click create new database and name it "osTicket".</p>
<img width="512" alt="SQL" src="https://github-production-user-asset-6210df.s3.amazonaws.com/158519921/302445470-eaa5aa61-2eea-4406-a7d7-fa77616dbe16.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20241217%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241217T153452Z&X-Amz-Expires=300&X-Amz-Signature=aeeabc255a3f41e286611741fd7d7d7f1b271583cfd25cdde21847cccf75dc43&X-Amz-SignedHeaders=host">
<br>
<br>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12886; Finish signing up</h3>

<p>Then go back to your osTicket browser and fill up the missing credentials. 
It should look something like this.</p>
<img width="308" alt="osticket final signup" src="https://github.com/kirkgacias/osticket-prereqs/assets/158519921/a185574b-775a-49fb-9468-c5d82033e823)">
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12887; Finalize osTicket installation</h3>

<p>Click install and osTicket should begin setting up. </p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h2> Final cleanup steps</h2>
<p>[X] Delete "setup" file located at C:\inetpub\wwwroot\osTicket\setup</p>
<p>[X] Set permissions of "ost-config.php" to read only.</p>
<p> File is located at C:\inetpub\wwwroot\osTicket\include\ost-config.php</p>
<br>
<br>
<h1>Congratulations!!! &#127881; you just installed osTicket</h1>









