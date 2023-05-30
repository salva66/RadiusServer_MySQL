
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
