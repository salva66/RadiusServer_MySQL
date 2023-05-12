1. Set a static IP Adrress for your Ubuntu Machine, which for our case is 192.168.56.11

2. Update the OS to the latest version
$sudo apt-get update
$sudo apt-get upgrade

3. Install FreeRadius
$sudo apt-get install freeradius

4. Create a test client that shall help test if the installation of radius is well.

a) Determine the version of the installed freeradius
$freeradius -v
This version number shall be used throughout to access the files within the freeradius folder
b)run
$sudo nano /etc/freeradius/3.0/clients.conf
Within the configuration file, create a new client under the clients section having the following credentials
##new client
ipaddr	= 192.168.56.5
secret	= testrad123!
nas_type = other
c) restart freeradius
$sudo /etc/init.d/freeradius restart
