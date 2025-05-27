<h1 align="center" id = sinatechservices> Sina Tech Services </h1>
<p> Sina Tech Services is a startup project providing software development and SEO optimization services to small businesses. This project is deployed on an AWS cloud server running Ubuntu Linux to host our business applications and manage clients. </p>

<h2 id = "contents"> Table Of Contents </h2>
<ul>
    <li> <a href = "#getting-started"> Getting Started </a> </li>
    <li> <a href = "#specifications"> Project Specifications </a> </li>
    <li> <a href = "#configuration"> Server Configuration </a> </li>
    <li> <a href = "#access"> Accessing the Virtual Machine </a> </li>
    <li> <a href = "#apache"> Installing Apache </a> </li>
    <li> <a href = "#domain"> Domain Registration and Configuration </a> </li>
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
    <li> Select <b> Instance ID </b> and you will note a string provided under <b> Public DNS</b>. It should look something like this: <pre> <code> ec2-3-25-114-116.ap-southeast-2.compute.amazonaws.com </code> </pre> </li>
    <li> Open Linux command line, use 'cd' to move to the directory where the key pair "sinatech-webserver-key" is saved, then paste the given command line: <pre> <code> ssh -i sinatech-webserver-key.pem ubuntu@ec2-3-25-114-116.ap-southeast-2.compute.amazonaws.com </code> </pre></li> 
</ul>
Now you have console access to the virtual machine.

<h2 id = "apache"> Installing Apache </h2>
After having console access to the virtual machine, we need to Install Apache Webserver to start hosting our website. But before that, we need to update the apt repositories in case they may be out of date. We can update them with <pre> <code> sudo apt update </code> </pre>
Once updated, now we install Apache Webserver with <pre> <code> sudo apt install apache2 </code> </pre>
Once installed, a default webpage will already be hosted on the virtual machine. You can visit it by typing AWS EC2's public IP address in your web browser.

<h2 id = "domain"> Domain Registration and Configuration </h2>
Websites over the internet can be accessed by typing their associated IP addresses in the web browser, but remembering every complex IP addresses of websites over the internet is close to impossible. Therefore, domain names, which are human-friendly address of a website, are used to access them. <br>Register a domain name through any registrar (e.g, GoDaddy, Namecheap) and follow the given steps to link the website with the registered domain name.
<ul>
    <li> Once registered, log in to the account created in the domain registrar's website.</li>
    <li> Once logged in, navigate to <b> My Account </b> and then <b> Doamins </b> </li>
    <li> There you can see the domain registered by you in the domain registrar's company. Select your domain and then navigate to DNS section.</li>
    <li> In DNS section, select <b> Add New Record </b> and select "A" from "Type".</li>
    <li> In the "Name" field, type @ which will connect the IP address with main domain. In this case, www.sinatechservices.com </li>
    <li> In the "value" tag, type the public IP address of the AWS EC2 instance. you can find it when clicking <b> Connect </b> on the instance</li>
    <li> In the "TTL" tag, select custom and type 600 in the "Seconds" field.</li>
</ul>
Now you can access the website hosted on virtual machine by typing the registered domain name in the browser.

