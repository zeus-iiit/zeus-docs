# Checklist

Complete the given steps to get your own cloud up and running. This checklist is based completely on the TripleO deployment method consisting of an undercloud (for managing) and an overcloud (for the actual production cloud).

### Important milestone:

- [ ] Prepare environment on baremetal
- [ ] Install the undercloud (using instack)
- [ ] Undercloud Deployment
    - [ ] Set up images for overcloud
    - [ ] Register all H/W nodes with the undercloud
    - [ ] Introspect the H/W
    - [ ] Create different node profiles
- [ ] Plan for configuring the overcloud
    - [ ] Assign flavor
    - [ ] Assign provisioning images
    - [ ] Decide how many instances need to be deployed for each service
    - [ ] Configure service parameters
    - [ ] Create HEAT template describing the overcloud
- [ ] Deploy:
    - [ ] Use HEAT for the deployment
    - [ ] Identify and reserve nodes using Nova
    - [ ] Use ironic to startup nodes and install correct images
- [ ] Per Node setup:
    - [ ] Nodes gather configuration metadata from the HEAT template
    - [ ] HEAT configures the services on the nodes
    - [ ] Puppet triggers tests to check progress of the deployment and allows debugging
- [ ] Overcloud initialization:
    - [ ] Services on the nodes of overcloud are registered with Keystone
