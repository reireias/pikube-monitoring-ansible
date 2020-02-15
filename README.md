# pikube-monitoring-ansible
Ansible for monitoring system (Grafana + InfluxDB) on GCE

## setup

- create `inventory` directory while refering to `inventory.sample`

- create `.envrc` and enabled `direnv`

```
export INFLUX_USER="<your_influxdb_user>"
export INFLUX_PASS="<your_influxdb_pass>"
```

- run commands

```console
# setup nginx
$ ansible-playbook -i inventory init.yml

# setup let's encrypt with over writing nginx conf
$ gcloud compute ssh <your_gce_instance_name> --zone <your_zone>
$ sudo certbot --nginx -d <your_domain> -m <your_email> --agree-tos -n

# setup grafana and influxdb
$ ansible-playbook -i inventory main.yml
```
