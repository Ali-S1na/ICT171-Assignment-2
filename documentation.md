<h1 align="center" id = sinatechservices> Sina Tech Services </h1>
<p> Sina Tech Services is a startup project providing software development and SEO optimization services to small businesses. This project is deployed on an AWS cloud server running Ubuntu Linux to host our business applications and manage clients. </p>

<h2 id = "contents"> Table Of Contents </h2>
<ul>
    <li> <a href = "#getting-started"> Getting Started </a> </li>
    <li> <a href = "#specifications"> Project Specifications </a> </li>
    <li> <a href = "#configuration"> Server Configuration </a> </li>
    <li> <a href = "#access"> Accessing the Virtual Machine </a> </li>
</ul>

<h2 id = "getting-started"> Getting Started </h2>

<h3 id = "specifications"> Project Specifications </h3>
<ul> 
    <li> <b> Cloud Provider: </b> AWS EC2  </li>
    <li> <b> Instance Type: </b> t2.micro  </li>
    <li> <b> Operating System: </b> Ubuntu 24.02 LTS  </li>
    <li> <b> Domain: </b> www.sinatechservices.com  </li>
</ul>

<h2 id = "configuration">Server Configuration </h2>
First, create an AWS EC2 account to proceed with server configuration. This may take a while due to credit card checks. Once created, log into the account and follow the given steps to launch a successfull AWS EC2 instance (virtual machine).


<ul>
    <li> Navigate to EC2 dashboard and select <b> Launch Instance. </b> </li>
    <li> Name the AWS EC2 instance (e.g., sinatech-server). </li>
    <li> Select an operating system for the virtual machine (Ubuntu Server 24.04 LTS). </li>
    <li> Select instance type (t2.micro). </li>
    <li> Create a key pair for the AWS EC2 instance. Give it a meaningful name like "sinatech-webserver-key" which could be easily identified later on. Download and keep this key pair safe as this will be used later on to remotely access the virtual machine. </li>
    <li> Configure security group. You can name this group anything (e.g., sinatech-security). </li>
    <li> Add security group rules SSH (port 22), HTTP (port 80), and HTTPS (port 443). SSH allows remote access to the virtual machine while HTTP and HTTPS enable users to access the site. </li>
    <li> Leave rest of the fields at the default. </li>
    <li> Review and if satisfied with the changes, click <b> Launch Instance. </b> </li>
    <li> After this, the Amazon EC2 instance will be launched. You can monitor its status by navigating to EC2 dashboard and select "Instances". </li>
</ul>

<h2 id = "access">Accessing the Virtual Machine </h2>
The server is now created and running in the cloud. Now you need to have SSH access to the virtual machine. Follow the given steps below to have console access to the server.
<ul>
    <li> Select the virtual machine created and click on the "Connect" button provided. </li>
    <li> Select <b> Instance ID </b> and you will note a string provided under <b> Public DNS</b>. It should look something like this: </li>
        ``` like this ```
</ul>


