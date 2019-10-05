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
