# Labs


## Prerequisites
  
1. Install VirtualBox - https://www.virtualbox.org/wiki/Downloads
2. Install Vagrant on your computer - https://www.vagrantup.com/downloads.html
3. (Optional) **On Windows**, ensure that Hyper-V is disabled:
   1. Open a new PowerShell
   2. Run the following command:   
      ```
      Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-All
      ```
4. Download the `centos/7` Vagrant box for the **Virtualbox provider**:

  ```
  $ vagrant box add centos/7
  ==> box: Loading metadata for box 'centos/7'
     box: URL: https://vagrantcloud.com/centos/7
  This box can work with multiple providers! The providers that it
  can work with are listed below. Please review the list and   choose
  the provider you will be working with.

  1) hyperv
  2) libvirt
  3) virtualbox
  4) vmware_desktop

  Enter your choice: 3
  ```

## Resources

- In case of impassable resource limit of your local machine you are allowed to use Katacoda environment to work on this lab -  https://www.katacoda.com/jonatanblue/scenarios/1

## Work

### 1. Prepare a virtual environment

Since Ansible can not be installed on Windows host ([see the source](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#control-node-requirements)), to avoid issues associated with the platform on which Ansible is running, we will use a virtual environment.

We will use the [`ansible_local` provisioner](https://www.vagrantup.com/docs/provisioning/ansible_local.html) what will install Ansible on [CentOS 7](https://www.centos.org/) Linux distribution virtual machine by [Vagrant](https://www.vagrantup.com/). So, you don't need Ansible on your computer!

The next step once you’ve installed Vagrant is to create a `Vagrantfile` and customize it to suit your needs. This is covered in detail in [the Vagrant documentation](https://www.vagrantup.com/docs/), and for this lab we will use a prepared `Vagrantfile`.

Take a look at the [`Vagrantfile`](assets/Vagrantfile) and at the YAML files [`playbooks/run.yml`](../assets/lab-8-ansible/playbooks/run.yml). To have more information how the `Vagrantfile` is configured follow this [Vagrant Guide](https://docs.ansible.com/ansible/latest/scenario_guides/guide_vagrant.html)

### 2. Create and provision a VM

```bash
cd assets
vagrant up
```

You should end up with the following error (this is planned): 
 
```bash
TASK [gitlab/install : Install GitLab] *****************************************
fatal: [gitlab_server]: FAILED! => {"changed": false, "msg": "No package matching 'gitlab-ee' found available, installed or updated", "rc": 126, "results": ["No package matching 'gitlab-ee' found available, installed or updated"]}
```

### 3. Check that everything is ok by connecting to the VM through SSH:

```bash
vagrant ssh gitlab_server
```

### 4. Complete the GitLab installation

   1. Fill the blanks in [`gitlab/install/tasks/main.yml`](assets/playbooks/roles/gitlab/install/tasks/main.yml) based on the steps 1. and 2. of the [GitLab installation doc for CentOS 7](https://about.gitlab.com/install/#centos-7)
   2. Update the playbooks on the VM using `vagrant upload`:
      ```
      vagrant upload playbooks /vagrant/playbooks gitlab_server
      ```
   3. Rerun provisioning with the command `vagrant provision`

### 5. Test your installation 

Test by connecting to http://20.20.20.2 (step 3 of the [GitLab installation doc](https://about.gitlab.com/install/#centos-7)):

   1. Choose a password
   2. Login as the user `root` using the password
