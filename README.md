# Ansible Tower tutorials for the batfish.base role

This repository contains example playbooks that you can use in conjunction with Ansible Tower.

- [tutorial1_extract_facts.yml](playbooks/tutorial1_extract_facts.yml): Shows how to retrieve facts about network devices

- [tutorial2_validate_facts.yml](playbooks/tutorial2_validate_facts.yml): Shows how to validate facts about network devices

- [tutorial3_validate_forwarding.yml](playbooks/tutorial3_validate_forwarding.yml): Shows how to validate the routing and forwarding behavior of the network

- [tutorial4_validate_acls.yml](playbooks/tutorial4_validate_acls.yml): Shows how to validate the behavior of a packet filter(ACL/Firewall rule) 

- [tutorial5_validate_bgp_sessions.yml](playbooks/tutorial5_validate_bgp_sessions.yml): Shows how to validate configuration attributes to find mis-configured BGP sessions and undefined references

- [bf_upload_diagnostics.yml](playbooks/bf_upload_diagnostics.yml): Shows how to upload diagnostic information about your snapshot in the event of issues (e.g. if Batfish fails to fully recognized some lines in your input files)

## Setup

- Ensure that the remote Batfish server is accessible from your machine.

- On your Ansible Tower server(s) install the latest version of Pybatfish & dependencies (we recommend you do this in a virtual environment)

  `python -m pip install --upgrade git+https://github.com/batfish/pybatfish.git`
  
  `python -m pip install --upgrade -r requirements.txt`
  

## Running a tutorial

- Import this repository as a project in Ansible Tower
- Create a job template for the playbook that you want to use
  - Select the virtual environment in which you installed Pybatfish and associated dependencies.
  - You will need to pass in the address or FQDN for the batfish server in the job template as an `Extra Variable`
  
     `batfish_server: <name or IP address of server running Batfish or Batfish Enterprise>`
  

Each playbook is a standalone tutorial, it does not depend on other tutorials having been run first. So feel free to execute them in whatever order you think is best.

Batfish is designed to provide complete network analysis, which is why all tasks calling Batfish modules should set `delegate_to: localhost` and `run_once: true`. The tutorials are set up that way, so you can incorporate non-Batfish tasks that need to run across other hosts in your inventory.


## Documentation

 - [Documentation for the Ansible modules](https://github.com/batfish/ansilbe/tree/master/docs/README.md)

 - [Documentation for Batfish](https://github.com/batfish/batfish)

