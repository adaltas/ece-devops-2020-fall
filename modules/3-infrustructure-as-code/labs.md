# Labs 

Infrastructure as code 

## Objectives

This workshop can be done **on your own, or in groups of 2-3 people**.

1. Part 1 - Using Vagrant with Shell Provisioner
2. Part 2 - GitLab installation using Vagrant and Ansible Provisioner

## Before starting
  
1. Install VirtualBox - https://www.virtualbox.org/wiki/Downloads
2. Install Vagrant on your computer - https://www.vagrantup.com/downloads.html
3. (Optional) **On Windows**, ensure that Hyper-V is disabled:
   - Open a new PowerShell
   - Run the following command:   
      ```bash
      Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-All
      ```
4. Download the `centos/7` Vagrant box for the **Virtualbox provider**, run:

  ```bash
  vagrant box add centos/7
  ```
  
  It will output:
  ```bash
  
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

5. Clone the lab repository to your computer:

```bash
git clone https://github.com/adaltas/ece-devops-2020-fall.git
```

## Part 1 - Using Vagrant with Shell Provisioner

### 1. Prepare a virtual environment

The next step once you’ve installed Vagrant is to create a `Vagrantfile` and customize it to suit your needs. This is covered in detail in [the Vagrant documentation](https://www.vagrantup.com/docs/), and for this lab we will use a prepared `Vagrantfile`.

Go to the `modules/3-infrustructure-as-code/assets/part-1` directory and take a look at the [`Vagrantfile`](assets/part-1/Vagrantfile):

```bash
cd ece-devops-2020-fall/modules/3-infrustructure-as-code/assets/part-1
```

### 2. Create a virtual machine (VM)

Run the command:

```bash
vagrant up
```

Try also other Vagrant commands that manage the VMs:

```bash
# will check VMs status
vagrant status 

# stop the VMs
vagrant halt

# will destroy VMs
vagrant destroy
```

### 3. Check that everything is ok by connecting to the VM via SSH

1. To enter inside the VM via SSH:

```bash
vagrant ssh centos_server
```

It will open a session in the VM and you can run any bash commands being inside the Linux VM (like `ls`, `pwd` , etc.) 
 
2. Open VirtualBox (or VMware) and check the installed virtual machine.

### 4. Play with different commands for Shell Provisioner

Find more instructions [here](https://www.vagrantup.com/docs/provisioning/shell).

1. To configure the `/etc/hosts` file replace "Start provisioning" section in the `Vagrantfile` with this:

```ruby
# Start provisioning
config.vm.provision "shell",
  inline: "echo '127.0.0.1  mydomain-1.local' >> /etc/hosts"
```

Then run:

```
vagrant provision
```

**Note!** You need to run it with your laptop OS terminal, not being inside the VM via SSH.

2. To print a current date into the `/etc/vagrant_provisioned_at` file replace in the `Vagrantfile` with this:

```ruby
# Start provisioning
$script = <<-SCRIPT
echo I am provisioning...
date > /etc/vagrant_provisioned_at
SCRIPT

config.vm.provision "shell", inline: $script
```

Then run:

```
vagrant provision
```

## Part 2 - GitLab installation using Vagrant and Ansible Provisioner 

We will install Gitlab on CentOS as described in [the official documentation](https://about.gitlab.com/install/#centos-7). You can try repeat those steps manually one after another on the VM configured in the part 1 of the lab. Usually, when we are installing first time a new software on a testing environment, we do it manually to test each step and then, after clarifying all the installation process we automatize it using tools like Vagrant and Ansible. 

We will use [`ansible_local` provisioner](https://www.vagrantup.com/docs/provisioning/ansible_local.html) what will install Ansible on [CentOS 7](https://www.centos.org/) Linux distribution virtual machine by [Vagrant](https://www.vagrantup.com/). So, you don't need Ansible on your host OS!

### 1. Prepare a virtual environment

Go to the `modules/3-infrustructure-as-code/assets/part-2` directory and take a look at the [`Vagrantfile`](assets/part-2/Vagrantfile) and at the YAML files [`playbooks/run.yml`](assets/part-2/playbooks/run.yml). To have more information how the `Vagrantfile` is configured follow this [Vagrant Guide](https://docs.ansible.com/ansible/latest/scenario_guides/guide_vagrant.html)

In the `assets/part-2` directory, you will find:
- A `Vagrantfile` that defines the VMs to be managed by Vagrant (1 CentOS 7 VM named `gitlab_server` in our case)
- A `playbooks/` directory that contains Ansible playbooks to install GitLab and run health checks

### 2. Create and provision a virtual machine (VM)

Run the command:

```bash
vagrant up
```

It will take 5-10 min to install all the necessary software including required packages, GitLab instance and databases.

### 3. Test the installation 

To test the installation of GitLab you can just open a URL in a browser and make sure it answers with any GitLab page (this is a step 3 of the [GitLab installation doc](https://about.gitlab.com/install/#centos-7)).

So, open in your browser the URL - http://20.20.20.2

Once it is open the login page you can login and explore GitLab:

 1. Choose a password
 2. Login as the user `root` using the password

### 4. Instructions for updating playbooks

If you need to change something in our installation, you have to modify your playbooks, upload them on the VMs and run provisioning:

1. Update the playbooks on the VM using `vagrant upload`:

```
vagrant upload playbooks /vagrant/playbooks gitlab_server
```

2. Rerun provisioning with the command:

```
vagrant provision
```
