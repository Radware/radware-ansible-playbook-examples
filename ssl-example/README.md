# SSL Example - Ansible Automation

This folder contains playbooks and parameter files for automating the configuration of SSL/TLS setups on Radware devices. Two execution methods are supported:

1. **Cyber Controller Automation Engine**: Upload the files to Radware's Cyber Controller to create and execute an automation template.
2. **External Ansible Engine**: Run the playbook using a standalone Ansible setup.

---

## Cyber Controller Automation Engine

### Overview

The playbook and parameter file in this section are designed for the Cyber Controller Automation Engine. They can be uploaded to create an automation template for configuring SSL services on the managed Radware devices.

### Files

- **ssl-demo-ae.yaml**: The playbook that defines the automation workflow for SSL configuration.
- **ssl_demo_params.json**: Parameter file containing customizable values like IP addresses, NAT settings, and service details.

### How to Use

1. **Log in to the Cyber Controller**:
   - Access the Automation Engine interface.

2. **Upload the Files**:
   - Upload `ssl-demo-ae.yaml` as the playbook.
   - Upload `ssl_demo_params.json` to define parameters for the playbook.

3. **Create an Automation Template**:
   - Link the uploaded playbook and parameter file to form a reusable automation template.

4. **Run the Automation Template**:
   - Execute the template to configure SSL services on the specified devices.

### Key Parameters

The `ssl_demo_params.json` file contains important configuration parameters, including:

- **state**: Specifies the job mode (`present`, `absent`, or `read`).
- **Interface Addresses and Masks**:
  - `interface_1_address` / `interface_2_address`: IPs for the network interfaces.
  - `interface_1_net_mask` / `interface_2_net_mask`: Subnet masks for the interfaces.
- **Real Server Details**:
  - `real_1_address` / `real_2_address`: IPs of the real servers in the backend.
- **VIP Details**:
  - `vip_address`: The virtual IP address.
  - `vip_address_pip`: The NAT address for the VIP.

---

## External Ansible Engine

### Overview

This method allows the SSL configuration to be executed using a standalone Ansible engine. The playbook and variable file are designed for flexibility and external management.

### Files

- **ssl-demo.yaml**: The main playbook for configuring SSL services on Radware devices.
- **vars/alteon_params.yml**: Variable file containing device-specific configuration details.

### How to Use

1. **Set Up Ansible Environment**:
   - Ensure Ansible is installed and the required Radware modules are available.
   - Verify network connectivity to the Radware devices.

2. **Prepare the Files**:
   - Place `ssl-demo.yaml` and `vars/alteon_params.yml` in your Ansible project directory.
   - Edit `vars/alteon_params.yml` to match your environment, including:
     - Device credentials and IPs.
     - SSL service parameters, including real servers, VIPs, and NAT details.

3. **Run the Playbook**:
   Execute the playbook with the following command:

   ```bash
   ansible-playbook ssl-demo.yaml
   ```

### Key Parameters in `vars/alteon_params.yml`

- **radware_provider**:
  - Details of the Radware devices (e.g., IP address, credentials, ports).
- **services**:
  - List of service configurations, including IPs, NATs, and ports.
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
   ansible-playbook ssl-demo.yaml
   ```

This method provides direct control for users familiar with Ansible configurations.

---

Choose the execution method based on your operational preferences and infrastructure setup. Both approaches ensure a reliable and automated SSL configuration on Radware devices.