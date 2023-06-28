# Ansible Playbook: Install Kubernetes and Join Worker Nodes

 

This Ansible playbook automates the installation and configuration of Kubernetes, including setting up the control plane and joining worker nodes to the cluster. It simplifies the process of deploying Kubernetes, saving time and effort.

 

## Prerequisites

 

Before running this playbook, ensure that you have met the following prerequisites:

 

1. Ansible is installed on the control node.
2. SSH access is configured between the control node and target hosts.
3. The control node has sudo privileges to install software and execute commands as root on the target hosts.

 

## Usage

 

Follow the steps below to use this playbook:

 

1. Create an inventory file: Specify the IP addresses or hostnames of the control node and worker nodes in an inventory file. For example:

 

   ```
   [control]
   control_node ansible_host=192.168.0.100

 

   [workers]
   worker1 ansible_host=192.168.0.101
   worker2 ansible_host=192.168.0.102
   ```

 

2. Customize the playbook: If needed, modify the playbook variables to match your environment. Open the playbook file, `kubernetes.yml`, and update the following variables:

 

   - `kube_version`: Specify the desired Kubernetes version.
   - `pod_subnet`: Specify the pod network subnet.
   - `control_plane_endpoint`: Specify the IP address or hostname of the control plane endpoint.

 

3. Run the playbook: Execute the playbook using the `ansible-playbook` command:

 

   ```bash
   ansible-playbook -i inventory.ini kubernetes.yml
   ```

 

   Replace `inventory.ini` with the path to your inventory file.

 

4. Monitor the playbook execution: Ansible will run the tasks on all hosts specified in the inventory file. The playbook will install Docker, add the Kubernetes apt repository, install Kubernetes components, initialize the control plane, set up the kubeconfig file for the non-root user, deploy the pod network (Flannel), and generate the join command for worker nodes (if the control node is part of the 'master' group).

 

5. Join worker nodes: If you see the join command printed as output, copy it and run it on each worker node to join them to the Kubernetes cluster.

 

## License

 

This playbook is licensed under the [MIT License](LICENSE). Feel free to modify and adapt it to suit your needs.

 

## Disclaimer

 

Please note that this playbook is provided as-is without any warranty. Use it at your own risk. Review the code and customize it according to your environment before running it.

 

## Contributions

 

Contributions, improvements, and bug fixes are welcome! Feel free to open issues or submit pull requests on the [GitHub repository](https://github.com/your-repo).

 

## Acknowledgments

 

This playbook was inspired by the community's efforts to simplify the installation and configuration of Kubernetes using Ansible. Special thanks to all the contributors who have made this playbook possible.

 

## References

 

For more information on Kubernetes, Ansible, and the modules used in this playbook, refer to the following resources:

 

- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Ansible Documentation](https://docs.ansible.com/)
- [Ansible Apt Module](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)
- [Ansible Command Module](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/command_module.html)
- [Ansible Debug Module](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/debug_module.html)
- [Ansible File Module](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/file_module.html)
- [Ansible Package Module](https://docs

has context menu
Compose
