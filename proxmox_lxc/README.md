# Proxmox LXC

We can set up an LXC using both Terraform and Ansible

## Using Terraform

Check out [this video](https://youtu.be/dvyeoDBUtsU) instructions on this setup. This includes getting API credentials from Proxmox.

Docs for the provider are [here](https://registry.terraform.io/providers/Telmate/proxmox/latest/docs).

### Authenticated User

In the video above, the suggestion is to use the Proxmox API user and token - this is a good suggestion and is best practice (because we can easily revoke a token). ~~However because we needed to use a custom `hookscript`, [we couldn't use this method](https://forum.proxmox.com/threads/acme-api-endpoint-403-permission-check-failed-user-root-pam-despite-user-being-root-pam.111745/post-482006) we instead had to use the `root@pam` user and password.~~

We do need to use the `root@pam` user and password - but not because of why I thought. It turns out that the hookscript doesn't work as I thought, but so long as you authenticated with `root@pam` and you provide a public token, ssh is enabled. 