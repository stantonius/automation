# Proxmox Master

Setup of master node

## Creating a Hookscript

**Update**: while the links below are still valid for creating a hookscript, it turns out that I don't need it for this particular use case (ie. to enable ssh). SSH is enabled for both the Terraform and Ansible method so long as your provide a public key, so a hookscript isn't needed.

There was little information about how to do this. The resources below are what I found in order to make the hookscript work.

* [Proxmox forum post](https://forum.proxmox.com/threads/hookscripts-on-container-to-gracefully-start-stop-docker-images-inside-containers.103083/post-444291) showing the types of hooks you can use in a hookscript. You can also find this example in the Proxmox node at `/usr/share/pve-docs/examples/guest-example-hookscript.pl` 
* [Proxmox forum post](https://forum.proxmox.com/threads/cant-exec-proxmox-usb-hotplug-in-a-vm-hookscript.116199/post-502634) that show how to create a **bash hookscript** instead of using Perl
* [This post](https://forum.proxmox.com/threads/how-to-use-new-hookscript-feature.53388/post-460707) was how I realized that you **load and call the file using two different directories**.
    * You **load** the hookscript to `/var/lib/vz/snippets/hookscript.sh`
    * You **call** the hookscript at `local:snippets/hookscript.sh`
* [A good article](https://codingpackets.com/blog/proxmox-hook-script-port-mirror/) on this hookscript setup

