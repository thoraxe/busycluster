This role requires that a variable `azs` with a list of AZs to create infra nodes be set.

For example:

```sh
ansible-playbook -e api_url=`oc whoami --show-server` -e '{"azs":["us-east-1"]}' play.yaml
```