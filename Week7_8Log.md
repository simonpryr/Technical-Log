# Technical-Log for Week 7 and 8
# A. ArcGIS Server on Google Clous Platform (GCP)
Total time spent: 1.5 hours on 29th of Feb, 2024
## 1.	Creating a project 	
-	Create a new project with suitable name by navigating to new project menu
-	If it is an individual account chose No Organization option
-	
## 2.	Setting up Virtual Machine in GCP
-	Navigate to Compute Engine and select VM Instances
-	Create Instance and provide a unique name to your VM, change the default boot disk, Under the Boot disk menu select Custom images. Select the Shawn’s ArcGIS Server project and under the project select the available image
-	Enable the firewall to allow both HTTP (80) and HTTPS (443) traffic.
-	After creating VM, Google Cloud starts costing the account money.

## 3.	Configure the instance to connect and log in	
-	Next to the RDP, click the drop down menu and select set windows password
-	Set username as student and the new password will be shown once so save it (It will show 1 tie only so save it as a text file notepad).

## 4.	Setting up the Firewall rule so that  change the default TCP Port for RDP from 3389 to 444 since fleming has blocked 3389 port for campus security purpose. 
-	Go to set up firewall rule and select create firewall rule
-	Provide a name, under target select all instances in the network, under the source filter select IPV4 ranges, and choose IPV4ranges as 0.0.0.0/0 for any computer on the internet to work. We can change the ip settings to make it more secure. 
-	To know your IP address, we can google whatsmyip.
-	Set the TCP port 444 under the Specified protocols and ports and click create to apply the firewall to the VM.

## 5.	Setting up GCP Firewall rule to allow ArcGIS Server Management Port	
-	Under the VPC network select firewall and click on create firewall rule and name it as arcgisserveradmin. Under targets select All instances in the network and select IPV4 ranges for source filter, and choose IPV4ranges as 0.0.0.0/0 for any computer on the internet to work. We can change the IP settings to make it more secure.
-	Set the TCP port 444 under the Specified protocols and ports and click save.

## 6.	Setting up windows Firewall rule to allow ArcGIS Manager Ports
•	Login to the remote desktop 
-	Search for remote desktop connection from on windows desktop and open it.
-	Copy the running VM external IP number (Changes each time) from console and paste the IP number followed by”:444” in the computer box under remote desktop connection interface and click connect.
-	Enter your credentials: username as student and password obtained while creating VM.
•	In the search menu in remote desktop type firewall and select windows Defender Firewall with Advanced Security, click on Inbound Rules and select New Rule. 
•	Select port and under protocol and ports interface, select TCP and under Specific local ports type in 6443, 6080 and click next.
•	Give name to this new rule as ArcGIS Server Admin Ports.

## 7.	Turn off the VM when not in Use.				(Time Spend: 5 min)
-	Go to Compute Engine and VM Instances. Green tick appear when the VM is running.
-	Click on three dots “More Actions” Drop down menu next to the RDP and select Stop option to turn off the VM.

# B. Publish Canada Service to your Own GCP VM
Total time Spent: 30 minutes on 13/03/2024-14/03/2024
### Steps 
1.	Start your VM on GCP
2.	Register data source on the server
-	On the remote desktop Canada zip file is already there, extract this canada file in the file path C:\GISWorkspace\Canada.
3.	Log in to ArcGIS server manager on the VM.
4.	Open ArcGIS Pro, add the Canada shape file in the map and make symbology
5.	Connect to the ArcGIS Server using the login details of ArcGIS Server
6.	From the catalog pan, under the Servers, select the connected server and right click and publish the map Service.
7.	Resolve the unique id and registration warnings that shows up while analyzing.
8.	Publish the server.


