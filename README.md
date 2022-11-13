# Craig's Automation Files

Terraform, Ansible, and bash scripts used for automation.

Anything that is not for a private repo goes here.

## Notes

### Terraform

* `*.auto.tfvars` is in `.gitignore` but it needs to be created in every TF script
* Other Terraform files and dirs such as `.tfstate` and `.terraform/` are hidden via `.gitignore`

### Bash Scripting

* Need to download the `jq` program on the orchestrating computer in order to parse json state output from Terraform
    * For Mac, you just run `brew install jq` (or `arch -arm64 brew install jq`)

### ssh

In order for any of this to work, we need the ssh keys on our hosts. As a reminder, we take these steps:
1. Generate a new proxmox ssh key using the command: `ssh-keygen -t ed25519 -f ~/.ssh/proxmox`
    * Yes, you could just use a key you already have. But for some reason I like to make them specific to a service.
2. We then pass the key to the remote machine via: `ssh-copy-id -i ~/.ssh/proxmox.pub user@host`
3. To use the key when connecting: `ssh -i proxmox root@IP_ADDRESS`
