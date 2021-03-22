# Configuring Raspberry Pi OS with Ansible

[![Ansible](https://img.shields.io/badge/raspberrypi-3,4-C51A4A?logo=raspberry-pi)](https://www.raspberrypi.org/) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/universalvishwa/raspberrypi-os-config-ansible/blob/master/LICENSE) [![Python](https://img.shields.io/badge/python-3.7-blue?logo=python)](https://www.python.org/downloads/release/python-379/) [![Ansible](https://img.shields.io/badge/ansible-2.10-EE0000?logo=ansible)](https://docs.ansible.com/) [![Molecule](https://img.shields.io/badge/molecule-v3.2.0-3CAFCE)](https://molecule.readthedocs.io/) [![CI](https://github.com/universalvishwa/raspberrypi-os-config-ansible/workflows/CI/badge.svg)](https://github.com/universalvishwa/raspberrypi-os-config-ansible/actions) 

## Overview
- Ansible playbook to perform General OS configuration settings on a Raspberry Pi 3/4.
- Playbook not intented to run as a CI/CD pipeline. But can be integrated to a Github Workflow if needed.
- CI Testing for Ansible roles are configured with Github Actions.
- This work is done as part of a Hobby project on setting up an IoT Stack in a Home network.
- The playbooks are configured to use _SSH Keys_ instead of username/password to connect to Raspberry Pi.
- Pre-requisites:
    - Add the SSH public key `id_rsa.pub` to `/home/pi/.ssh/authorized_keys` in Raspberry Pi.

## Ansible Roles
1. **ping**:
    - This role is used to test connectivity to Raspberry Pi.
2. **docker**:
    - Install Docker and Docker Compose in `Armv7` or `Arm64` architectures.
3. **os-setup**:
    - Disable power saving mode
    - Check WiFi: Detect WiFi connection loss and restart the network service.

### Run Ansible playbooks
1. Generate an Ansible inventory file named `hosts.ini` using the template file `hosts_example.ini`. Update the inventory group _**rpi**_ with Raspberry Pi host information.
    ```ini
    $ mv hosts_example.ini hosts.ini
    $ cat hosts.ini
    [vagrant]
    localhost    ansible_user=vagrant   ansible_port=2222

    [rpi]
    192.168.10.100    ansible_user=pi   ansible_port=22
    ```

1. Run Ansible ping
    ```bash
    $ ansible-playbook -i hosts.ini ansible_ping.yml -l rpi
    ```
2. Run Ansible playbook to configure Raspberry Pi OS.
    ```bash
    $ ansible-playbook -i hosts.ini playbook.yml -l rpi
    ```

#### Notes:
- CI testing for **docker** role using Github Actions cannot be run directly. Because of _Docker-in-Docker_ scenario.
    - User can always run the Molecule testing locally to test and verify the role.

## References
- [Ansible Molecule Testing](https://github.com/universalvishwa/ansible-molecule-testing)
- [geerlingguy.ansible-role-docker_arm](https://github.com/geerlingguy/ansible-role-docker_arm)
- [Installing Docker and Docker Compose on the Raspberry Pi in 5 Simple Steps](https://dev.to/rohansawant/installing-docker-and-docker-compose-on-the-raspberry-pi-in-5-simple-steps-3mgl)
- [Installing Docker on the Raspberry Pi](https://pimylifeup.com/raspberry-pi-docker/)
- [dockerpi](https://github.com/lukechilds/dockerpi)
- [Does Your Raspberry Pi 3 Lose WiFi Connections After a While](http://qdosmsq.dunbar-it.co.uk/blog/2016/03/does-your-raspberry-pi-3-lose-wifi-connections-after-a-while/)
- [Rebooting the Raspberry Pi when it loses wireless connection](https://weworkweplay.com/play/rebooting-the-raspberry-pi-when-it-loses-wireless-connection-wifi/)