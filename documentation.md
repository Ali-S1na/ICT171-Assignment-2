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
    <li> <a href = "#website"> Website Development </a> </li>
    <li> <a href = "#move-website"> Moving Website to the Server </a> </li>
    <li> <a href = "#certificate"> Getting SSL Certificate </a> </li>
    <li> <a href = "#script"> Linux Script for SSL Certificate </a> </li>
    <li> <a href = "#conclusion"> Conclusion </a> </li>
</ul>

<h2 id = "getting-started"> Getting Started </h2>

<h3 id = "specifications"> Project Specifications </h3>
<ul> 
    <li> <b> Cloud Provider: </b> AWS EC2  </li>
    <li> <b> Instance Type: </b> t2.micro  </li>
    <li> <b> Operating System: </b> Ubuntu 24.02 LTS  </li>
    <li> <b> Server IP Address: </b> 3.25.51.189  </li>
    <li> <b> Domain: </b> www.sinatechservices.com  </li>
    <li> <b> Video Explainer: </b> <a href = "https://1drv.ms/v/c/b8298d2513159f7f/EVvriU7SkcBCvdm2bizIxg4B7V4ODcv7bNbehRbxP4_wbQ?e=L5dnIx&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D"> Click here </a> </li>
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
Websites over the internet can be accessed by typing their associated IP addresses in the web browser, but remembering every complex IP addresses of websites over the internet is close to impossible. Therefore, domain names, which are human-friendly address of a website, are used to access them. <br> Register a domain name through any registrar (e.g, GoDaddy, Namecheap) and follow the given steps to link the website with the registered domain name.
<ul>
    <li> Once registered, log in to the account created in the domain registrar's website.</li>
    <li> Once logged in, navigate to <b> My Account </b> and then <b> Domains</b>. </li>
    <li> There you can see the domain registered by you in the domain registrar's company. Select your domain and then navigate to DNS section.</li>
    <li> In DNS section, select <b> Add New Record </b> and select "A" from "Type".</li>
    <li> In the "Name" field, type "@"which will connect the IP address with main domain. In this case, sinatechservices.com </li>
    <li> In the "Value" tag, type the public IP address of the AWS EC2 instance. you can find it when clicking <b> Connect </b> on the instance.</li>
    <li> In the "TTL" tag, select custom and type 600 in the "Seconds" field.</li>
    <li> In DNS section, select <b> Add New Record </b> and fill the fields with same values except replace "@" with  "www" in the "Name" field.</li>
    <li> Once done, save the changes.</li>
</ul>
Now you can access the website hosted on virtual machine by typing the registered domain name in the browser.

<h2 id = "website"> Website Development </h2>
Now that the virtual machine is configured and the domain name is successfully translated into the associated IP address, we need to build our website and move it to the server. A website typically consists of 3 important parts which are HTML, CSS, and Javascript. HTML makes the overall structure of the website whereas CSS brings styles and colors to it. On the other hand, Javascript mkaes the web pages more interactive and dynamic. <br>
For this project, a free template is used from [Start Bootstrap] (https://startbootstrap.com/template/scrolling-nav) which is licensed under the [MIT License] (https://opensource.org/licenses/MIT). <br> The following changes are made to the website to make it a better fit for this project.
<ul>
    <li> The title and navbar brand name is changed to Sina Tech Services. </li>
    <li> The text in the header section is updated to welcome visitors to the webpage and display an attractive slogan. </li>
    <li> The "About Us" section of the webpage is updated to  display about the company's history and mission.</li>
    <li> The "Services" section of the webpage is updated to display the services offered by the company.</li>
    <li> The "Contact" section of the webpage is updated to display icons and data such as address, phone number, email address, and business hours of the company. </li>
    <li> In the footer section of the webpage, it is stated that this website is licensed under MIT License </li>
</ul>

<h2 id = "move-website"> Moving Website to the Server </h2>
Now that the webpages are developed, we need to move it to the virtual machine, making the website live and enabling people to visit the website from anywhere in the world. Follow the below steps to successfully move the website to the configured server.
<ul>
    <li> Open your Linux command line and navigate to the folder where the key pair "sinatech-webserver-key" is saved. </li>
    <li> Then type the given code to gain SSH access into the virtual machine <pre> <code> ssh -i sinatech-webserver-key.pem ubuntu@sinatechservices.com </code> </pre> </li>
    <li> Once accessed, navigate to the folder where a default html page is saved <pre> <code> cd /var/www/html</code> </pre></li>
    <li> Remove the default html page <pre> <code> sudo rm index.html</code> </pre></li>
    <li> Once removed, exit the EC2 instance, comeback to Linux command line, and upload the necessary website files to the same folder where the key pair "sinatech-webserver-key.pem" is saved.</li>
    <li> Use the following command to move each file to home directory of the virtual machine. <pre> <code> scp -i sinatech-webserver-key.pem filename ubuntu@sinatechservices.com:~/</code> </pre></li>
    <li> Now SSH into the virtual machine and move the website files from home directory to /var/www/html using sudo command. <pre> <code> sudo mv filename /var/www/html</code> </pre></li>
    <li> Once all the files are moved to /var/www/html the virtual machine will start hosting the website and it can be accessed by typing the domain name "www.sinatechservices.com" in the browser.</li>
</ul>

<h2 id = "certificate"> Getting SSL Certificate </h2>
Now that our website is live and functioning properly, we need to get SSL Certificate to authenticate our website and enable HTTPS encryption. for this project, we will get SSL certificate from Let's Encrypt. Follow the below steps to get SSL Certificate for sinatechservices.com
<ul>
    <li> SSH into your virtual machine and remove any certbot auto using this command  <pre> <code> sudo apt-get remove certbot </code> </pre></li>
    <li> Install certbot in the virtual machine  <pre> <code> sudo snap install --classic certbot </code> </pre></li>
    <li> Run Certbot using the following command  <pre> <code> sudo ln -s /snap/bin/certbot /usr/bin/certbot </code> </pre></li>
    <li> Get and serve certificate on the website  <pre> <code> sudo certbot --apache </code> </pre></li>
    <li> Set up automatic renewals for the website before they expire  <pre> <code> sudo certbot renew --dry-run </code> </pre></li>
    <li> To confirm if the SSL certificate is set up successfully, look up for the lock icon in the search bar next to the domain name.</li>
</ul>

<h2 id = "script"> Linux Script for SSL Certificate </h2>
In Linux, we can create script that consists of set of commands executed with just one line. We can create a linux script to get SSL Certificate for sinatechservices.com from Let's Encrypt. This helps to reduce the workload and promotes code efficiency. Follow the given steps to successfully create a Linux script for getting SSL Certificate.
<ul>
    <li> Open your Linux command line and create a bash script  <pre> <code> nano SSL-script.sh </code> </pre></li>
    <li> Copy the given code to create a bash script for getting SSL Certificate from Let's Encrypt  <pre> <code> #!/bin/bash <br> sudo apt-get remove certbot <br>
    sudo snap install --classic certbot <br>
    sudo ln -s /snap/bin/certbot /usr/bin/certbot <br>
    sudo certbot --apache <br>
    sudo certbot renew --dry-run </code> </pre></li>
    <li> Exit nano and change the file permissions of the script to make it executable  <pre> <code> sudo chmod u=rwx SSL-script.sh </code> </pre></li>
    <li> Move the script to the virtual machine where rest of the files are located  <pre> <code> scp -i sinatech-webserver-key.pem SSL-script.sh ubuntu@sinatechservices.com:~/ </code> </pre></li>
    <li> Now SSH into the virtual machine and move the bash scrript from home directory to /var/www/html using sudo command. <pre> <code> sudo mv SSL-script.sh /var/www/html</code> </pre></li>
    <li> Once moved.navigate to /var/www/html and run the bash script to get SSL Certificate for sinatechservices.com  <pre> <code> ./SSL-script.sh </code> </pre></li>
    The script will run the commands to get and display SSL Certificate on sinatechservices.com website and once the script is run, the website will be opened on Firefox browser to check if the lock icon beside the domain name in search bar appears.
</ul>

<h2 id = "conclusion"> Conclusion </h2>
This is the end of the documentation. It includes all the necessary steps and codes, explained thoroughly to make it easy for future developers to replicate or debug this project in case any issue occurs.