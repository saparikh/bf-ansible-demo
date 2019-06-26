# Tutorials for the batfish.base role

This repository contains example playbooks that show how to use Batfish in conjunction with Ansible.

- [tutorial1_extract_facts.yml](playbooks/tutorial1_extract_facts.yml): Shows how to retrieve facts about network devices

- [tutorial2_validate_facts.yml](playbooks/tutorial2_validate_facts.yml): Shows how to validate facts about network devices

- [tutorial3_validate_forwarding.yml](playbooks/tutorial3_validate_forwarding.yml): Shows how to validate the routing and forwarding behavior of the network

- [tutorial4_validate_acls.yml](playbooks/tutorial4_validate_acls.yml): Shows how to validate the behavior of a packet filter(ACL/Firewall rule) 

- [tutorial5_validate_bgp_sessions.yml](playbooks/tutorial5_validate_bgp_sessions.yml): Shows how to validate configuration attributes to find mis-configured BGP sessions and undefined references

- [bf_upload_diagnostics.yml](playbooks/bf_upload_diagnostics.yml): Shows how to upload diagnostic information about your snapshot in the event of issues (e.g. if Batfish fails to fully recognized some lines in your input files)

## Setup

- Ensure that the remote Batfish server is accessible from your machine.

- Install the latest version of Pybatfish & dependencies (we recommend you do this in a virtual environment)

  `python -m pip install --upgrade git+https://github.com/batfish/pybatfish.git`
  `python -m pip install --upgrade -r requirements.txt`
  
- Install the latest version of the `batfish.base` role from Ansible Galaxy.

  `ansible-galaxy install --force batfish.base`
  - If you encounter any issues related to SSL certificates use the `-c` option. 
  

## Running a tutorial

We highly recommend that you run the tutorials in a Python 3 virtual environment. Details on how to set one up can be found [here](https://docs.python.org/3/library/venv.html).

Run specific tutorials via

  `ansible-playbook -i inventory tutorial1_extract_facts.yml`

   Each playbook is a standalone tutorial, it does not depend on other tutorials having been run first. So feel free to execute them in whatever order you think is best.

   Batfish is designed to provide complete network analysis, which is why all tasks calling Batfish modules should set `delegate_to: localhost` and `run_once: true`. The tutorials are set up that way, so you can incorporate non-Batfish tasks that need to run across other hosts in your inventory.


## Documentation

 - [Documentation for the Ansible modules](https://github.com/batfish/ansilbe/tree/master/docs/README.md)

 - [Documentation for Batfish](https://github.com/batfish/batfish)

