# HA Example - Ansible Automation

This folder contains playbooks and parameter files for automating the configuration of a High Availability (HA) setup using Radware devices. Two execution methods are supported:

1. **Cyber Controller Automation Engine**: Upload the files to Radware's Cyber Controller to create and execute an automation template.
2. **External Ansible Engine**: Run the playbook using a standalone Ansible setup.

---

## Cyber Controller Automation Engine

### Overview

The playbook and parameter file in this section are designed for the Cyber Controller Automation Engine. They can be uploaded to create an automation template for configuring HA on the managed Radware devices.

### Files

- **ha-demo-ae.yaml**: The playbook that defines the automation workflow for HA setup.
- **ha_demo_params.json**: Parameter file containing customizable values like IP addresses, peer interfaces, and network masks.

### How to Use

1. **Log in to the Cyber Controller**:
   - Access the Automation Engine interface.

2. **Upload the Files**:
   - Upload `ha-demo-ae.yaml` as the playbook.
   - Upload `ha_demo_params.json` to define parameters for the playbook.

3. **Create an Automation Template**:
   - Link the uploaded playbook and parameter file to form a reusable automation template.

4. **Run the Automation Template**:
   - Execute the template to configure HA on the specified devices.

### Key Parameters

The `ha_demo_params.json` file contains important configuration parameters, including:

- **state**: Specifies the job mode (`present`, `absent`, or `read`).
- **peer_interface_va_1** / **peer_interface_va_2**: HA interface IPs for devices 1 and 2.
- **network_mask**: Subnet mask for both HA interfaces.

---

## External Ansible Engine

### Overview

This method allows the HA configuration to be executed using a standalone Ansible engine. The playbook and variable file are designed for flexibility and external management.

### Files

- **ha-demo.yaml**: The main playbook for configuring HA on Radware devices.
- **vars/alteon_params.yml**: Variable file containing device-specific configuration details.

### How to Use

1. **Set Up Ansible Environment**:
   - Ensure Ansible is installed and the required Radware modules are available.
   - Verify network connectivity to the Radware devices.

2. **Prepare the Files**:
   - Place `ha-demo.yaml` and `vars/alteon_params.yml` in your Ansible project directory.
   - Edit `vars/alteon_params.yml` to match your environment, including:
     - Device credentials and IPs.
     - HA interface details and other required parameters.

3. **Run the Playbook**:
   Execute the playbook with the following command:

   ```bash
   ansible-playbook ha-demo.yaml
   ```

### Key Parameters in `vars/alteon_params.yml`

- **radware_provider**:
  - Contains details of the Radware devices (e.g., IP addresses, credentials, and ports).
- **ha**:
  - Defines HA configuration parameters, including:
    - `peer_interface_va_1` and `peer_interface_va_2`: HA IPs for each device.
- **state**:
  - Specifies the job mode (`present`, `absent`, or `read`).

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
   ansible-playbook ha-demo.yaml
   ```

This method provides direct control for users familiar with Ansible configurations.

---

Choose the execution method based on your operational preferences and infrastructure setup. Both approaches ensure a reliable and automated HA configuration on Radware devices.