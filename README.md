# Ansible Project for Radware Automation - Playbook examples

This project contains Ansible playbooks designed to automate and manage various configurations and use cases with Radware devices. Each folder within this project represents a unique setup or configuration managed via Radware's Ansible modules, aimed at different networking scenarios such as GSLB, HA, and SSL.

## Project Structure

The project is structured into several folders, each containing a different playbook setup for specific automation tasks. Here is an overview of each root folder and its purpose:

```
├── gslb-example/
│   ├── cyber-controller-engine/
│   └── external-ansible-engine/
├── ha-example/
│   ├── cyber-controller-engine/
│   └── external-ansible-engine/
└── ssl-example/
    ├── cyber-controller-engine/
    └── external-ansible-engine/
```

### Folder Descriptions

- **gslb-example**: Contains playbooks and parameters for configuring a Global Server Load Balancing (GSLB) setup. It automates the configuration of load balancing and failover across multiple data centers.
  - [gslb-example README](gslb-example/README.md)
  - **cyber-controller-engine**: Includes the core Ansible playbook (`gslb-demo-cc-ae.yaml`) and associated parameter file (`gslb_demo_params.json`) for running the GSLB demo directly on the Cyber Controller.
  - **external-ansible-engine**: Provides a standalone playbook (`gslb-demo.yaml`) and variable definitions (`vars/alteon_params.yml`) for executing the GSLB configuration using an external Ansible engine.

- **ha-example**: Contains playbooks and parameters for setting up High Availability (HA) configurations. This setup ensures reliable service delivery through redundant paths and failover mechanisms.
  - [ha-example README](ha-example/README.md)
  - **cyber-controller-engine**: Contains the primary HA Ansible playbook (`ha-demo-ae.yaml`) and its parameter file (`ha_demo_params.json`) for running the HA demo via the Cyber Controller.
  - **external-ansible-engine**: Includes the HA playbook (`ha-demo.yaml`) and variable configurations (`vars/alteon_params.yml`) for deploying HA configurations using an external Ansible engine.

- **ssl-example**: Focuses on automating SSL/TLS configurations, such as certificate management and secure traffic handling.
  - [ssl-example README](ssl-example/README.md)
  - **cyber-controller-engine**: Contains the SSL configuration playbook (`ssl-demo-ae.yaml`) and parameter file (`ssl_demo_params.json`) for Cyber Controller-based SSL automation.
  - **external-ansible-engine**: Includes the SSL configuration playbook (`ssl-demo.yaml`) and variable file (`vars/alteon_params.yml`) for an external Ansible engine deployment.

## Getting Started

Each root folder (`gslb-example`, `ha-example`, `ssl-example`) corresponds to a specific configuration. Before running any playbooks, ensure you have the necessary permissions, access to Radware devices, and proper configurations defined in each `vars` file.

**Prerequisites**:
- Ansible installed on your system
- Access to Radware Cyber Controller or external environment as required
- Radware modules installed for Ansible

## License

This project is intended for Radware network automation. Please ensure compliance with your organization’s policies when deploying these configurations.
Contact Radware™ sales department for licensing https://www.radware.com/contactus