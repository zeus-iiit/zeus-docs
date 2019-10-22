# Connect to CISCO 300 Series Switch

This will guide to setup/access a managed CISCO 300 series switch in case you have a non-accessible console port, via. a Web-GUI. Following will be the steps to access the managed swtich. To access the switch by using the web-based interface, you must know the IP address the switch is using. The switch uses the factory default IP address of **192.168.1.254** by default.


> **Note** : Make sure the switch is factory reset before connecting to it for the first time.

1. Power on the CISCO 300 switch and leave it idle for 30 seconds to 5 minutes. The switch will perform POST during this period.
2. Connect your laptop to the switch using a ethernet cable to any of the fast ethernet ports on the switch. You must chose an IP address for the computer in the range of **192.168.1.1—192.168.1.253** that is not already in use.
3.  If the IP addresses is assigned by a DHCP server, make sure the DHCP server is running and can be reached from the switch and the computer. It might be necessary to disconnect and reconnect the devices for them to discover their new IP addresses from the DHCP server.
4. Open a Web browser window. If you are prompted to install an Active-X plug-in when connecting to the device, follow the prompts to accept the plug-in.
5. Enter the switch IP address in the address bar and press Enter. For example, **http://192.168.1.254**. The *Switch Login Page* displays.
6. Enter the default login information:
  - Username is **cisco**
  - Default password is **cisco** (passwords are case sensitive)
7. If this is the first time that you have logged on with the default username and password, the Change Password Page opens. The rules for constructing a new login and password are displayed on the page. Enter a new administrator password and click **Apply**

##### Useful links

- [CISCO 300 switches Admnistration Guide](https://www.cisco.com/c/dam/en/us/td/docs/switches/lan/csbms/sf30x_sg30x/administration_guide/78-19308-01.pdf)
- [CISCO 300 switches Quick Start](https://www.cisco.com/c/dam/en/us/td/docs/switches/lan/csbms/sf30x_sg30x/quick_start/78-19252-01.pdf)