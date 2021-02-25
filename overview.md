## What is Ansible?

Ansible is a simple, open-source, IT automation engine that automates cloud provisioning, configuration management, application deployment, intra-service orchestration, and many other IT needs.


## Why Ansible?

Ansible is simple enough for everyone in an IT team to use, yet powerful enough to automate even the most complex deployments. It handles repetitive tasks, giving the team more time to focus on innovation.

Key Advantages:
- Free : It is Open Source
- Simple : Simple to set up and use (no special coding skills needed)
- Flexible : We can orchestrate the entire application environment no matter where it’s deployed
- Agentless : We don’t need to install any other software or firewall ports


## Elements in Ansible

### Inventories:

Inventories are basically the list of managed nodes or “hosts” we want to automate.

The default location for inventory is : /etc/ansible/hosts. We can specify a different inventory file at the command line using the -i <path> option.

The inventory file can be in one of many formats, depending on the inventory plugins we have. The most common formats are INI and YAML.

sample INI file:
```
mail.example.com

[webservers]
foo.example.com
bar.example.com

[dbservers]
one.example.com
two.example.com
three.example.com
```

sample YAML file:
```
  hosts:
    mail.example.com:
  children:
    webservers:
      hosts:
        foo.example.com:
        bar.example.com:
    dbservers:
      hosts:
        one.example.com:
        two.example.com:
        three.example.com:
```

> src: https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html


### Modules:

Ansible ships with a number of modules. These are standalone scripts that can be executed on remote hosts directly or through Playbooks. These modules can control system resources, like services, packages, or files (anything really), or handle executing system commands. 

Users can also write their own modules. All modules return JSON format data.

**examples**:

- execute ping module from the command line
```
$ ansible webservers -m ping
```
- restart server
```
$ ansible webservers -m command -a "/sbin/reboot -t now"
```

> src: https://docs.ansible.com/ansible/latest/user_guide/modules.html


### Playbook:

The core of Ansible is the Playbook. Playbook allows us to describe our automation jobs using a very simple language (YAML). We can launch the tasks synchronously and asynchronously with playbooks.

A playbook consists of a play, and a play consists of tasks.

Sample Playbook:
```
- hosts: webservers
  serial: 5 # update 5 machines at a time
  roles:
  - common
  - webapp

- hosts: content_servers
  roles:
  - common
  - content
```

> src : https://docs.ansible.com/ansible/latest/dev_guide/overview_architecture.html#playbooks

#### Plugins:

...

#### APIs:

...


## Ansible Tower

It allows us to manage ansible automation using UI and REST API.


## References

- https://www.ansible.com/resources/videos/quick-start-video?extIdCarryOver=true&sc_cid=701f2000001OH7YAAW
- https://medium.com/@madhukaudantha/ansible-and-ansible-architecture-2f309fe53fa
- https://www.youtube.com/watch?v=wgQ3rHFTM4E
