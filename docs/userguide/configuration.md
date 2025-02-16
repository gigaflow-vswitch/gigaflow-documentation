---
icon: material/list-box
---

# Project Configuration

## Testbed Configuration

We use Ansible to orcherstrate all experiments using these three machines. Therefore, we require `root` access to each of them. To populate for each machine, update the `inventory.ini` file as following:

```yaml title="inventory.ini" linenums="1"
[NODES]
TGEN ansible_host=<tgen-ip> ansible_user=<tgen-username> ansible_password=<tgen-password> ansible_sudo_pass=<tgen-root-password>
GVS ansible_host=<ovs-ip> ansible_user=<ovs-username> ansible_password=<ovs-password> ansible_sudo_pass=<ovs-root-password>

[STORAGE]
COLLECTOR ansible_host=<collector-ip> ansible_user=<collector-username> ansible_password=<collector-password> ansible_sudo_pass=<collector-root-password> ansible_ssh_user=<collector-username> ansible_ssh_pass=<collector-root-password>
```

## Experiment-Specific Configuration

To setup and run a specific experiment (with a given locality, vSwitch pipeline, and Gigaflow tables configuration), modify the following variables in `vars/main.yml`.

```yaml title="vars/main.yml"

# the locality (high/low) to pick the correct traffic
# choose an option from locality_static
locality_dynamic:
  current:
    locality: "high-locality"

# the pipeline to install and send traffic for
# choose an option from pipelines_static
pipelines_dynamic: 
  current: 
    name: "cord-ofdpa"
    sub_path: "cord/ofdpa"

# the Gigaflow tables and entries limit in each of them
# choose an option from gigaflow_static
gigaflow_dynamic:
  experiment: "ee" # this is just the name for the logs directory
  options:
      gigaflow_tables_limit: 4
      gigaflow_max_entries: 8000
```