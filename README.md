# SDI_AnsiblePlaybooks

## Getting Started

** This is still a work in progress. README files in this collection were copied from roles repository and need to be edited.


### Installing Ansible

First, you'll need to install Ansible on the machine that will execute your playbooks (called the control node).  The
control node can be as simple as a laptop or virtual machine, and can be running any Unix-like OS (Linux, BSD, macOS).

You'll want to follow the
[Ansible documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-the-control-node)
for installing Ansible on your machine.

### Clone this repository

With Ansible installed, clone this repo:

```
$ git clone https://github.com/jdw112/SDI_AnsiblePlaybooks.git
$ cd SDI_AnsiblePlaybooks/
```

### Customize connection parameters

Update the supplied inventory.ini file. Authentication credentials are not included, and should be specified either on the CLI, or in the inventory file.

### Customize variable parameters
```
sdi_root_dir=/opt/IBM/TDI/V7.2
sdi_solution_directory=/opt/IBM/TDI/SOLDIR
sdi_rmi_port=1099
sdi_web_port=1098
sdi_system_store_port=1527
dashboard_and_restservice_on=false
fix_pack_package_name=7.2.0-ISS-SDI-FP0008
ibm_java_archive_package_name=ibm-java-jre-8.0-6.25-linux-x86_64.tgz
```

### Install Image directory 
Place the download items in the following directories.
```
playbook/files/SDI_7.2_XLIN86_64_ML.tar  -  SDI Installer Image
playbook/files/7.2.0-ISS-SDI-FP0008.zip  -  SDI Fix pack
playbook/files/ibm-java-jre-8.0-6.25-linux-x86_64.tgz  -  IBM JVM 8 Update
playbook/files/SIA_RMI_7140_SDI_7X_MP_ML.zip  -  ISIM RMI Dispatcher Install Image
```
### Avalable tags 
```
os_update  //Skip the request to update all operating system packages
prereq_update  //Skip the install of prerequisites operating system packages 
```

You're now ready to start using these playbooks.

## Sample Playbooks

You can use these playbooks as a base by cloning this repository.  Each of them is documented with how to run them via
`ansible-playbook` and their customization options.

```
# For Example 
$ cd SDI_AnsiblePlaybooks
$ ansible-playbook playbooks/install_sdi.yml -i inventory.ini

$ ansible-playbook playbooks/install_sdi.yml -i inventory.ini -e fix_pack_package_name=7.2.0-ISS-SDI-FP0008
$ ansible-playbook playbooks/install_sdi.yml -i inventory.ini -e fix_pack_package_name=7.2.0-ISS-SDI-FP0007 --skip-tag os_update,prereq_update
$ ansible-playbook playbooks/collect_versions.yml -i inventory.ini 
$ ansible-playbook playbooks/install_fixpack.yml -i inventory.ini -e fix_pack_package_name=7.2.0-ISS-SDI-FP0007
```

// Primary playbooks 
* install_sdi.yml - Install Security Directory Integrator (SDI) v7.2 on node.
* install_sdi_and_dispatcher.yml - Install Security Directory Integrator (SDI) v7.2 and ISIM Dispatcher on node.

// Secondary playbooks
* shutdown_sdi.yml - Shutdown SDI on node
* undeploy_sdi.yml - Manually Uninstall all instances of SDI on node
* install_fixpack.yml - Install SDI v7.2 product fix pack on node
* install_jvm.yml - Install IBM JVM for SDI on node
* install_dispatcher.yml - Install ISIM RMI Dispatcher product on node
* update_customjars.yml - Upload custom jars to {{ sdi_solution_directory }}/custom_jars
* update_properties.yml - Update specific SDI global and solution properties on node
* update_dashboard_RESTSerivce_state.yml - Update Dashboard and REST state on SDI node
