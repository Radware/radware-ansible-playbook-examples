# GSLB Demo - Ansible Automation

This folder contains playbooks and parameter files for automating the setup of a Global Server Load Balancing (GSLB) configuration using Radware devices. Two execution methods are supported:

1. **Cyber Controller Automation Engine**: Upload the files to Radware's Cyber Controller to create and execute an automation template.
2. **External Ansible Engine**: Run the playbook using a standalone Ansible setup.

---

## Cyber Controller Automation Engine

### Overview

The playbook and parameter file in this section are designed for the Cyber Controller Automation Engine. They can be uploaded to create an automation template for configuring GSLB on the managed Radware devices.

### Files

- **gslb-demo-cc-ae.yaml**: The playbook that defines the automation workflow for GSLB setup.
- **gslb_demo_params.json**: Parameter file containing customizable values like IP addresses, server details, and job state.

### How to Use

1. **Log in to the Cyber Controller**:
   - Access the Automation Engine interface.
   
2. **Upload the Files**:
   - Upload `gslb-demo-cc-ae.yaml` as the playbook.
   - Upload `gslb_demo_params.json` to define parameters for the playbook.

3. **Create an Automation Template**:
   - Link the uploaded playbook and parameter file to form a reusable automation template.

4. **Run the Automation Template**:
   - Execute the template to configure GSLB across the specified sites.

### Key Parameters

The `gslb_demo_params.json` file contains important configuration parameters, including:

- **state**: Specifies the job mode (`present`, `absent`, or `read`).
- **fqdn**: The Fully Qualified Domain Name for the GSLB application (e.g., `app.demo.lab`).
- **IP Addresses**:
  - Server and client-side interfaces for Site A and Site B.
  - Virtual IPs (VIPs) for both sites.
- **Reals**:
  - Lists of real server IPs for Site A and Site B.
- **DNS Responders**:
  - IP addresses for DNS responders at each site.

---

## External Ansible Engine

### Overview

This method allows the GSLB configuration to be executed using a standalone Ansible engine. The playbook and variable file are designed for flexibility and external management.

### Files

- **gslb-demo.yaml**: The main playbook for configuring GSLB on Radware devices.
- **vars/alteon_params.yml**: Variable file containing site-specific configuration details.

### How to Use

1. **Set Up Ansible Environment**:
   - Ensure Ansible is installed and the required Radware modules are available.
   - Verify network connectivity to the Radware devices.

2. **Prepare the Files**:
   - Place `gslb-demo.yaml` and `vars/alteon_params.yml` in your Ansible project directory.
   - Edit `vars/alteon_params.yml` to match your environment, including:
     - Device credentials and IPs.
     - Site-specific configurations such as VIPs, real server details, and DNS responder addresses.

3. **Run the Playbook**:
   Execute the playbook with the following command:

   ```bash
   ansible-playbook gslb-demo.yaml
   ```

### Key Parameters in `vars/alteon_params.yml`

- **radware_provider**:
  - Contains details of the Radware devices (e.g., IP addresses, credentials, and ports).
- **gslb_srv**:
  - Defines the GSLB configuration, including:
    - FQDN for the application.
    - Interface details for Site A and Site B.
    - Local real servers and DNS responders.

---

## Native Ansible Execution

### Overview

For users who prefer running Ansible directly without templates or predefined parameter files, the playbook can be executed using inline variables or through simple modifications to the variable files.

### Steps

1. **Edit `vars/alteon_params.yml`**:
   - Update the file with the necessary configuration details for your environment.

2. **Execute the Playbook**:
   Run the following command to execute the playbook with the provided variables:

   ```bash
   ansible-playbook gslb-demo.yaml
   ```

This method gives flexibility for advanced users who want direct control over playbook execution and variables.