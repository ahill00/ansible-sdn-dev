ansible-sdn-dev
==

This is a collection of ansible roles and a playbook that sets them up and starts.

Getting Started
==

1. Clone this repo.
2. `vagrant up` / `vagrant ssh`
3. Start mininet!
4. Hack away!

Customization
==

There are a couple of options to customize the roles included in this repository.

- Uncomment the x11 forwarding line in Vagrantfile to use xterm and mininet
- Uncomment the file sharing line in Vagrantfile to sync folders between your local machine and the VM
- Specifying versions of OVS/Mininet/Ryu can be done in the Vagrantfile or via Ansible extra args.
- mininet installation and startup arguments can be passed as Ansible variables as well. This is done in `sdn.yaml`

Known Issues
==

1. Some environments do not allow outbound SSH connections. Unfortunately, the mininet installer reaches out to some sources in this manner. It's recommended to set up your VMs in a trusted environment.
2. The playbooks are not idempotent. Rerunning `vagrant provision` can cause problems. It's recommended to `vagrant destroy -f` and `vagrant up`
