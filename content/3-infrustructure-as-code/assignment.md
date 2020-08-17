# Assignment

## 1. Read the [GitLab Health Check doc](https://docs.gitlab.com/ee/user/admin_area/monitoring/health_check.html)

## 2. Run a healthcheck using `curl`:
   
   1. Connect to the VM using `vagrant ssh`
   2. Run the command:
      ```shell
      $ curl http://127.0.0.1/-/health
      GitLab OK
      ```
## 3. Read [`playbooks/roles/gitlab/healthcheck/tasks/main.yml`](playbooks/roles/gitlab/healthcheck/tasks/main.yml) to understand how it relates

## 4. Run the `gitlab/healthcheck` role
   
   1. Connect to the VM using `vagrant ssh`
   2. Run the playbooks using the right tag (replace `TAG`):
      ```
      ansible-playbook /vagrant/playbooks/run.yml --tags TAG -i /tmp/vagrant-ansible/inventory/vagrant_ansible_local_inventory
      ```
      
## 5. Run the 2 other kind of health checks in the playbook (using the [uri module](https://docs.ansible.com/ansible/latest/modules/uri_module.html)):
   
   1. [Readiness check](https://docs.gitlab.com/ee/user/admin_area/monitoring/health_check.html#readiness).
   2. [Liveness check](https://docs.gitlab.com/ee/user/admin_area/monitoring/health_check.html#liveness)

## 6. Print the results of the health checks in the console

## 7. Bonus task

Print a custom message with only the dysfunctional(s) services in the Readiness check if there are some. To test the printing, stop `redis` using the command `sudo gitlab-ctl stop redis` on the node before running the playbook again. Tip: use the `json` attribute of the response.
