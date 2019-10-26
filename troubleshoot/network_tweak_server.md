# Reverse Wi-Fi from a system to server over Ethernet

1. Type `nm-connection-editor` in your terminal.
2. Add a shared network connection by pressing the `Add` button.
3. Choose `Ethernet` from the list and press `Create`.
4. Click `IPv4 Settings` in the left.
5. Choose `Shared` to other computers by clicking the `Method` drop-down menu.
6. Enter a new name like `Shared WiFi LAN` as the `Connection name` at the top.

## Connect to the above network on server

1. Connect ethernet jack to the any unconfigured ethernet interface on the server.
2. Delete any existing configuration of the ethernet interface.
3. Configure the interface to obtain the IP address.
```
nmcli connection modify eno1 ipv4.method auto
nmcli connection up eno1
```
4. Ping the internet to check if the connection works.
