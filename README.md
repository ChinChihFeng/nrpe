[![Build Status](https://travis-ci.org/ChinChihFeng/nrpe.svg?branch=master)](https://travis-ci.org/ChinChihFeng/nrpe)

# Summary

This Ansible role has the following features for installing nrpe. It is tested on CentOS 6 and 7.

## Usage

ansible-playbook nrpe.yml

```yaml
---
- hosts: all
  roles:
    - nrpe
```

## Role Variables
The most varibles are default. If you want to change any version of modules or cores, you would modify number or string in the default configuration under the this path `default/main.yml`. Now, the version of nrpe is `3.2.1`, and the version of nagios plugins is `2.2.1`. I use the most stable verison of openssl is `1.0.2n`. You can change any version should ensure that it is match with nrpe version which you are using now. 


### To Do
 -

