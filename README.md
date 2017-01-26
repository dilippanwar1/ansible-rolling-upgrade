# Infrastructure Orchestration Demo

This is a Continuous Integraton / Continuous Deployment demonstration leveraging the concept of Infrastructure-as-Data provided by Ansible.

A sufficiently complex multi-tier application is orchestrated across multiple systems, networks and load balancers stood up in an OpenStack environment. The deployment process is covered in Ansible Plays and Roles end-to-end. Updates to the application are enabled by a rolling re-deployment of the application.

Requirements

  - OpenStack environment with Glance, Cinder, Nova, Neutron and LBaaS v2
  - Two OpenStack Tenants with Keys, Images and Security Groups
  - Ansible 2.2.0.1
  - python-shade

To initially deploy the app:

```sh
$ ansible-playbook -e "target=staging" site.yml
```

with an existing tenant named demo-staging.

To initiate the rolling upgrade:

```sh
$ ansible-playbook -e "target=staging" rolling_upgrade.yml
```

To cleanup a deployment and remove all components:

```sh
$ ansible-playbook -e "target=staging" destroy.yml
```
