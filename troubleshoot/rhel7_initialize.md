# Configure RHEL7 Server

After installing the RHEL7 into the undercloud, the subscription for the system needs to be activated so that the repos can be enabled and the required softwares packages be installed. You need to have an active subscription in Redhat. In this case, we are using a **Redhat Developer Subscription**. Next follow the commands to configure the system for further steps.
```bash
# 1. Login as root
# 2. Make sure you have an active internet connection

subscription-manager register
# provide the username and password for your account that has a Redhat subscription

# To activate the subscription:
subscription-manager suscribe

# List all avaiable repos:
subscription manager repos
```
