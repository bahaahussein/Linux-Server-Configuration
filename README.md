IP address: 34.211.170.96
SSH port: 2200
URL: ec2-34-211-170-96.us-west-2.compute.amazonaws.com
Steps:
	1) Launch Amazon ec2 instance and download private key.
	2) Configure security group's inbound rules to allow ssh from port 2200, http and https connections.
	3) Connect to the instance from local host's terminal.
	4) Update and upgrade packages.
	5) Make grader user, give it access to sudoers and generate public key for encryption.
	6) Configure Uncomplicated Firewall to allow SSH from port 2200, HTTP and NTP connections.
	7) Install apache2, mod-wsgi and git.
	8) Install Postgresql, log to it and create user and database.
	9) Install Flask and libraries used in the python file.
	10) Clone the web app from https://github.com/bahaahussein/ItemCatalog to /var/www .
	11) Make changes to it to fix bugs and make it use Postgresql instead of sqlite.
	12) Make wsgi file to serve the application.
	13) Edit the default virtual file of apache2.
	14) Restart apache.