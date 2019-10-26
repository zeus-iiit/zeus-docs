# Congiguration for switch

Our switch will be having 2 VLANs - one for provisioning network and the other for the public/external network. The provisioning network will be used by the undercloud to provide DHCP service and PXE manage the bare metal servers in the Overcloud, while the external network will be used to remotely access the servers. The external network needs to connected to an external DHCP service.

#### Steps to configure the switch

1. Remember to reset the switch to factory default and then SSH in to it. This will prompt you to enter tne username and password. Provide the details (by default, the pair is **cisco** and **cisco**) and hit `Enter`.
2. You will be taken to the **Privilleged Mode**. Enter the global configuration mode and make the further changes.
```
SW1#config t
SW1(config)# hostname "a-name-for-the-switch" (here, hermes)
hermes(config)#
```
3. Next add two VLANs as exlplained above.
```
hermes(config)#vlan { vlan-id } (here, 10 for provisioning)
hermes(config)#vlan { vlan-id } (here, 20 for external/public)
```
4. Configure the provisioning and the external VLANs
```
hermes(config)#interface vlan 10
hermes(config-vlan)#name vlan-name (here, Provision)
hermes(config-vlan)#state active
hermes(config-vlan)#no shutdown
hermes(config-vlan)#ip address 10.1.1.1 255.255.255.0 #Assign network for the VLAN
hermes(config-vlan)#exit

hermes(config)#interface vlan 20
hermes(config-vlan)#name vlan-name (here, External/Public)
hermes(config-vlan)#state active
hermes(config-vlan)#no shutdown
hermes(config-vlan)#exit
```
5. Assign ports to the VLANs:

We are assigning gi1-8 in provisioning VLAN and gi13-20 to the public VLAN.
```
# for each port in [gi1, gi2, gi3, gi4, gi5, gi6, gi7, gi8]:
hermes(config)#interface port
hermes(config-if)#switchport mode access
hermes(config-if)#switchport access vlan 10
hermes(config-if)#no shut
hermes(config-if)#exit

# for each port in [gi13, gi14, gi15, gi16, gi17, gi18, gi19, gi20]:
hermes(config)#interface port
hermes(config-if)#switchport mode access
hermes(config-if)#switchport access vlan 20
hermes(config-if)#no shut
hermes(config-if)#exit
```
6. The ports are assigned and can be viewed a summary about in the following command.
```
hermes# show vlan
```
