# SDI_AnsiblePlaybooks

## Getting Started

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

Update the supplied inventory file. Authentication credentials are not included, and should be specified either on the CLI, or in the inventory file

### Customize variable parameters
```
iam_images: ./install_images
sdi_root_dir: /opt/IBM/TDI/V7.2
sdi_solution_directory: /opt/IBM/TDI/Soldir
```

### Customize Install image directory 
Place the download items in the files/install_images directory.
```
7.2.0-ISS-SDI-FP0008.zip  
CustomInstallRspSDI72.txt  
ibm-java-jre-8.0-6.25-linux-x86_64.tgz  
SDI_7.2_XLIN86_64_ML.tar 
SIA_RMI_7140_SDI_7X_MP_ML.zip
```

You're now ready to start using these playbooks.

## Sample Playbooks

You can use these playbooks as a base by cloning this repository.  Each of them is documented with how to run them via
`ansible-playbook` and their customization options.

```
# For Example 
$ cd SDI_AnsiblePlaybooks/
$ ansible-playbook install_sdi.yml -i inventory.ini
```

* install_sdi.yml - Install Security Directory Integrator (SDI) v7.2 on host.
* uninstall_sdi.yml - Manually Uninstall SDI on host
* install_sdi_fixpack_FP0008.yml - Install product fix pack on host
* install_isim_dispatcher.yml - Install ISIM RMI Dispatcher product on host



