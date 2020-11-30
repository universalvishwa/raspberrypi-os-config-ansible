# Configuring Raspberry Pi OS with Ansible

[![Ansible](https://img.shields.io/badge/raspberrypi-3,4-C51A4A?logo=raspberry-pi)](https://www.raspberrypi.org/) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/universalvishwa/raspberrypi-os-config-ansible/blob/master/LICENSE) [![Python](https://img.shields.io/badge/python-3.7-blue?logo=python)](https://www.python.org/downloads/release/python-379/) [![Ansible](https://img.shields.io/badge/ansible-2.10-EE0000?logo=ansible)](https://docs.ansible.com/) [![Molecule](https://img.shields.io/badge/molecule-v3.2.0-3CAFCE)](https://molecule.readthedocs.io/) [![CI](https://github.com/universalvishwa/raspberrypi-os-config-ansible/workflows/CI/badge.svg)](https://github.com/universalvishwa/raspberrypi-os-config-ansible/actions) 

## Overview
- Ansible playbook to perform General OS configuration settings on a Raspberry Pi 3/4.
- Playbooks are not developed with intention to run as a CI/CD pipeline. But can be integrated to a Github Workflow if needed.
- CI Testing for Ansible roles is configured with Github Actions.
- This work is done as part of a Hobby project on setting up an IoT Stack in a Home network.

## Ansible Roles
1. **ping**:
    - This role is used to validate connectivity to Raspberry Pi.


## References
- [Ansible Molecule Testing](https://github.com/universalvishwa/ansible-molecule-testing)
- https://dev.to/rohansawant/installing-docker-and-docker-compose-on-the-raspberry-pi-in-5-simple-steps-3mgl
- https://pimylifeup.com/raspberry-pi-docker/
- https://github.com/lukechilds/dockerpi