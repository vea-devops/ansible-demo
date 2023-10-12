### How to run the playbook?
```bash
cd ansible
export ANSIBLE_HOST_KEY_CHECKING=False
export DOCKERHUB_USER="YOUR_DOCKERHUB_USERNAME"
export DOCKERHUB_PASS="YOUR_DOCKERHUB_PASSWORD"

# Run any of following ansible-playbook commands
# Runs Petclinic directly on host
ansible-playbook playbook.yml -t ec2

# Runs Petclinic in container with public image
ansible-playbook playbook.yml \
    -t docker \
    -e dockerhub_username=$DOCKERHUB_USER \
    -e dockerhub_password=$DOCKERHUB_PASS

# Runs Petclinic in container with your image
ansible-playbook playbook.yml \
    -t docker \
    -e dockerhub_username=$DOCKERHUB_USER \
    -e dockerhub_password=$DOCKERHUB_PASS \
    -e petclinic_docker_image="$DOCKERHUB_USER/petclinic:5.3.0"

# Removes petclinic from host
ansible-playbook playbook.yml -t clean_ec2_petclinic

# Remove petclinic container and image
ansible-playbook playbook.yml -t clean_docker_petclinic
```