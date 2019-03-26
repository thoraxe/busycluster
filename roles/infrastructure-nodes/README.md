This role requires that a variable `azs` with a list of AZs to create infra nodes be set.

Use of this role requires the `openshift` python module. On RHEL7 you can install `python-openshift`

For example:

```sh
ansible-playbook -e api_url=`oc whoami --show-server` -e '{"azs":["us-east-1"]}' play.yaml
```