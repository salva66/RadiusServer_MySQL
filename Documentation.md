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

NB: The 3.0 is the base version number

Within the configuration file, create a new client under the clients section having the following credentials

##new client

ipaddr	= 192.168.56.5

secret	= testrad123!

nas_type = other

c) restart freeradius

$sudo /etc/init.d/freeradius restart

5. Configure the users file for the new user

$sudo nano /etc/freeradius/3.0/users

Within the #local test user account set the following values for the user

test-user-local Cleartext-Password := "hello"

Reply-Message := "Hello, %{User-Name}"

6. Now, yo can test the created user account against your radius server

a) you MUST start freeradius in debug mode

$sudo /etc/init.d/freeradius stop

$sudo freeradius -X

b) Testing the user if can access locally

$radtest test-user-local hello 127.0.0.1 0 testing123

Since the local test is successfull, we can now disable the created useraccount as we shall not require it any further

$sudo nano /etc/freeradius/3.0/users

Within the users file, comment all lines pointing towards the created test user

Since we have freeradius well up and running we now have to install its extension which is is freeradius-mysql since the database we are going to use is MySQL one hence we shall need to have freeradius service that can support MySQL databases.
