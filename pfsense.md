
Here are the steps on how to enable FreeRADIUS in pfSense:

Go to System > Packages.
Click on the Available Packages tab.
Find the FreeRADIUS package and click on the Install button.
Click on the OK button to confirm the installation.

Once the installation is complete, go to Services > FreeRADIUS.
Click on the Interfaces tab.
Click on the Add button to create a new interface.
Enter the following information:
Interface IP Address: The IP address of the interface that will be used to listen for RADIUS requests.
Port: The port that will be used to listen for RADIUS requests. The default port is 1812.
Interface Type: Select the type of interface. The default type is Authentication.
IP Version: Select the IP version. The default version is IPv4.
Click on the Save button.

If you choose to use an authenticated backend, you will need to configure the remote authentication server in the user manager. Here are the steps:

1. Log in to the pfSense web interface and go to System > User Manager.
2. Click on the Authentication Servers tab.
3. Click the Add button to add a new server.
4. Set the Server Type to RADIUS.
5. Enter a descriptive name for the server in the Name field.
6. Enter the IP address of the Ubuntu machine hosting the MySQL database in the Host field.
7. Enter the shared secret that you configured for the RADIUS server in the Secret field.
8. Enter the RADIUS authentication port (usually 1812) in the Authentication Port field.
9. Enter the RADIUS accounting port (usually 1813) in the Accounting Port field.
10. Enter the NAS IP Attribute value. This should be the IP address of the pfSense interface that the users will be connecting to.

Once you have entered all the necessary information, click the Save button to save the settings.

Now, you can configure the captive portal to use the remote authentication server you just created:

1. Go to Services > Captive Portal.
2. Click on the General tab.
3. Set the Authentication method to "Use an authenticated backend".
4. In the Authentication server dropdown, select the RADIUS server you just created.
5. Save the settings by clicking the Save button.

Now, when users connect to the captive portal, they will be prompted for their username and password. The credentials will be checked against the MySQL database on the Ubuntu machine using the RADIUS protocol. If the credentials are valid, the user will be granted access to the network.
