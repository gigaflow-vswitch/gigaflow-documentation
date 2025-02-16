---
icon: material/clipboard-check
---

# Usage

- Start the Ansible docker by using the following command.
```sh title="Terminal"
make ansible
```

- Test connectivity between all three machines:
```sh title="Ansible Terminal"
make ping
```

Run all the following commands from within this Ansible docker container.

## Run All Experiments

To setup and run all end-to-end and microbenchmark experiments, run the following sequence of commands:

```sh title="Ansible Terminal"
# retrieve rulesets and traffic from COLLECTOR and place them on OVS and TGEN
# this will also install gvs (gvs with Gigaflow), the traffic generator, and all their dependencies
make setup-gvs-experiment

# run end-to-end (ee) experiments and microbenchmarks (bm)
# and loop over all the available rulesets and microbenchmark configurations
# and for each of them, setup the switch and traffic generators, send/receive the traffic
# and collect OVS/TGEN logs and place them on the COLLECTOR machine
make run-gvs-experiment

# teardown the experiment: this will uninstall gvs and tgen and clear logs from local machines; logs will remain saved on the COLLECTOR machine
make teardown-gvs-experiment
```

## Run End-to-End Experiments

To setup and run only end-to-end experiments:

```sh title="Ansible Terminal"
# retrieve rulesets and traffic from COLLECTOR and place them on OVS and TGEN
# this will also install gvs (gvs with Gigaflow), the traffic generator, and all their dependencies
make setup-gvs-experiment

# run end-to-end (ee) experiments and microbenchmarks (bm)
# and loop over all the available rulesets and for each of them, setup the switch and traffic generators, send/receive the traffic
# and collect OVS/TGEN logs and place them on the COLLECTOR machine
make run-gvs-ee-experiment

# teardown the experiment: this will uninstall gvs and tgen and clear logs from local machines; logs will remain saved on the COLLECTOR machine
make teardown-gvs-experiment
```

## Run Microbenchmarks
To setup and run only microbenchmark experiments:

```sh title="Ansible Terminal"
# retrieve rulesets and traffic from COLLECTOR and place them on OVS and TGEN
# this will also install gvs (gvs with Gigaflow), the traffic generator, and all their dependencies
make setup-gvs-experiment

# run end-to-end (ee) experiments and microbenchmarks (bm)
# and loop over all the available rulesets and for each of them, setup the switch and traffic generators, send/receive the traffic
# and collect OVS/TGEN logs and place them on the COLLECTOR machine
make run-gvs-bm-experiment

# teardown the experiment: this will uninstall gvs and tgen and clear logs from local machines; logs will remain saved on the COLLECTOR machine
make teardown-gvs-experiment
```

## Run Custom Experiment

To setup and run a specific experiment (with a given locality, pipeline, and Gigaflow tables configuration), modify the following variables in `vars/main.yml`.

```yaml title="vars/main.yml" linenums="1"

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

Once these variables are setup, run the following sequence of commands. 

```sh title="Ansible Terminal"
# sync the pipelines/traffic from COLLECTOR to NODES
make install-dataset 

# install the switch (with dependencies)
make install-gvs 

# install the traffic generators (with dependencies)
make install-tgen

# start the gigaflow-virtual-switch
# and install the pipeline rules in the switch
make start-switch-gvs 
make install-rules

# start the traffic (this will stop automatically)
make start-tgen

# cleanup after the traffic is sent
make stop-tgen

# uninstall the rules from the switch and stop it
make uninstall-rules 
make stop-switch-gvs

# copy logs from gvs and tgen to the collector machine
make collect-logs

# uninstall the tgen, gvs, and delete datasets
make uninstall-tgen 
make uninstall-gvs 
make uninstall-dataset
```