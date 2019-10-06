## Baremetal Node Configuration

### Baremetal node states:

* First **enroll** the nodes. This does not make the node available for any changes or any actions on them

```bash
openstack baremetal import --initial-state=enroll instackenv.json
```
* Next, nodes are made alive using **manage** action, providing power, IPMI and SSH access to ironic. Operator can execute introspection, RAID configuration, etc, however, it is still not deployable in this stage. Nodes directly move into **available** state.

```bash
openstack baremetal node manage <NAME OR UUID>

# For moving all avaliable nodes to manageable state
openstack baremetal introspection bulk start
```

* In this stage, the nodes are made available to nova for deployment using **provide** action.

```bash
openstack baremetal node provide <NAME OR UUID>
```

### Node Cleaning

It is the erasing of previous tenants data before the first enrollment of hardware and after every unprovisioning. Enable automated cleaning by changing the following in `undercloud.conf`

```apacheconf
[DEFAULT]
clean_nodes = True
```

###### For manual cleaning:

The nodes must be in **manageable** state and cleaning in done on request.

```bash
# If the node is not in the manageable state, move it there:
openstack baremetal node manage <UUID or name>

# Run manual cleaning on a specific node:
openstack overcloud node clean <UUID or name>

# or all manageable nodes:
openstack overcloud node clean --all-manageable

# Make the node available again:
openstack overcloud node provide <UUID or name>

# or provide all manageable nodes:
openstack overcloud node provide --all-manageable
```

### BIOS Settings

###### Apply BIOS ssettings

```bash
# To apply given BIOS configuration to all manageable nodes:
openstack overcloud node bios configure --configuration <..> --all-manageable

# To apply given BIOS configuration to specified nodes:
openstack overcloud node bios configure --configuration <..> node_uuid1 node_uuid2 ..
```
The configuration needs to be a JSON/YAML string (can be stroed in a file too) in the following form:

```
{
  "settings": [
    {
      "name": "setting name",
      "value": "setting value"
    },
    {
      "name": "setting name",
      "value": "setting value"
    },
    ..
  ]
}
```

###### Reset BIOS ssettings
```bash
# To reset the BIOS configuration to factory default on specified nodes:
openstack overcloud node bios reset --all-manageable

# To reset the BIOS configuration on specified nodes:
openstack overcloud node bios reset node_uuid1 node_uuid2 ..
```
