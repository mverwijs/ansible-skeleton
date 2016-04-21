# ansible-skeleton

This is my default skeleton for implementing Ansible for small and large
environments.

First install Ansible:

    apt-get install python-virtualenv
    virtualenv demo
    . demo/bin/activate
    pip install ansible
    which ansible

You should now have ansible installed. Go clone this repo.

    git clone git@github.com:mverwijs/ansible-skeleton.git my-first-ansible-environment
    cd my-first-ansible-environment

Create an inventory to toy with
    mkdir -p tenants/self/demo
    vim  tenants/self/demo/inventory
    

Your inventory should look like this:

    [toys]
    1.2.3.4

Where `1.2.3.4` is an actual ipaddress you can ssh to and become root.


Test ansible.

    ansible -m setup -i tenants/self/demo -l toys -u mverwijs -k
                            |                        |     |- you   |
                            |--- the inventory file  |              |- Your sudo password on the remote machine.
                                                     |- the hosts you will want to run this on.

Run a playbook.

    ansible-playbook -i tenants/self/demo -l toys -u mverwijs -k some_playbook.yml

You are done. You can now manage thousands of machines.
