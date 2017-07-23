IP address: 34.211.170.96
SSH port: 2200
URL: ec2-34-211-170-96.us-west-2.compute.amazonaws.com
Steps:
	1) Launch Amazon ec2 instance and download private key.
	2) Configure security group's inbound rules to allow ssh from port 2200, http and https connections.
	3) Connect to the instance from local host's terminal.
		"ssh -i path_to_private_key/key.pem root@IP_address"
	4) Update and upgrade packages.
		"sudo apt-get update"
		"sudo apt-get upgrade"
	5)	i- Make grader user.
			"sudo adduser grader"
		ii- Give it access to sudoers.
			"sudo nano /etc/sudoers.d/grader", put in it "grader ALL=(ALL:ALL) ALL", save and exit.
		iii- Generate public key for encryption.
			in the local machine: "ssh-keygen -t rsa to creeate key pair"
			"mkdir .ssh"
			"nano .ssh/authorized_keys" and put in it the text in .pub key made in the local machine
			"chmod 700.ssh"
			"chmod 644 .ssh/authorized_keys" to set permissions.
	6) Configure Uncomplicated Firewall to allow SSH from port 2200, HTTP and NTP connections.
		"sudo ufw default deny incoming"
		"sudo ufw default allow outgoing" previous two lines are default before configuration of firewall.
		"sudo ufw allow 2200/tcp" to allow ssh from port 2200.
		"sudo ufw allow www" to allow HTTP connections.
		"sudo ufw allow ntp"
		"sudo ufw enable" to apply changes to firewall.
	7) Install apache2, mod-wsgi and git.
		"sudo apt-get install apache2 libapache2-mod-wsgi git"
		"sudo a2enmod wsgi" to enable mod_wsgi.
	8) Install Postgresql, log to it and create user and database.
		"sudo apt-get install postgresql postgresql-contrib"
	9) Install Flask and libraries used in the python file.
		Installation can be seen here "http://flask.pocoo.org/docs/0.12/installation/"
	10) Clone the web app from https://github.com/bahaahussein/ItemCatalog to /var/www .
	11) Make changes to it to fix bugs and make it use Postgresql instead of sqlite.
	12) Make wsgi file to serve the application.
	13) Edit the default virtual file of apache2.
		Instructions can be seen here "https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts"
	14) Restart apache.
		"sudo service apache2 restart"