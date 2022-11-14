# Kubernetes vs Docker Swarm

**TL;DR**
If you need nodes auto-scaling - adding and removing servers on a high scale depending on the load proceessed by the application, managed Kubernetes from a cloud provider of your choice is the way to go.In all other cases, Docker Swarm is just enough.

**Kubernetes pro's**
- servers auto-scaling with the load (adding and removing servers as the traffic or calculations grow or decrease);
- flexibility to build programmed environments that serves very complex and huge scenarios, without manual intervention, if done right.

**Kubernetes cons**
- it's a complex and expensive thing, separate domain expertise - prepare for a steep learning curve or a significant paycheck for the DevOps / SRE services;
- Kubernetes version update is a manual procedure, could cause service interruption and shall happen every year at least: API is only stable between the patch versions ('z' in x.y.z version name), a release is supported for a year and some apps have direct requirements for a specific Kubernetes version;
- as Kubernetes was designed to be stateless, hosting stateful applications (all sort of databases) is a risk - so much could go wrong here, so if you have to use it that way, make sure you invest into choosing a proper architecture, regular and reliable backup & functional testing.

**Swarm pro's**
- ease of setup and configuration, especially with tools like CapRover
- easy (automatic) updates
- capable of executing single or multiple app(s) on a single or multiple server(s) - for load spikes and/or fail tolerance.

**Swarm con's**
- complex cluster configuration is a hassle...
- ...and servers auto-scaling is the biggest one.

It's not impossible, though you can create your own scripts with the tools like cadvisor, which will call cloud provider API, Terraforming new servers, or calling your scripts via cloud-init, but... so many could go wrong here...

**What if it has to be Kubernetes?**

If you still got to use it, here are some of my findings that could be of help:
- I found Lens Kubernetes IDE as of great use - it runs as an app from your computer (MacOS, Linux & Windows) - no need to open extra port/service at production + it helps to navigate and troubleshoot the cluster; k9s is a bit less functional but a very nice option for the command line;
- Do GitOps. Don't do direct 'root' (default kubeconfig) access, especially if you manage the cluster across the team - let Git be the only source of truth - a golden rule of thumb for any complex system anyway;
- Use Terraform to describe your cluster.If you have a significant dynamic part created at run-time, having a dedicated logging mechanism - that stores all YML commands for an easy issues investigation and roll-back is another great thing to do.
- Hypothesis - not yet battle-tested: microk8s and Rancher could be of use in some cases, as they both provide a fixed, most commonly required set of features and are relatively easy to maintain.Rancher even has Hetzner drivers (and an unofficial configuration guide), which means it brings auto-scale cluster at the cost of relatively cheap quite reliable physical machines.

**Tools:**
- CapRover - https://caprover.com - a very nice and handy single or multi-server cluster formation and management tool.Quick start I used to use is https://github.com/Potemkin-Co/quickies
- Lens (The Kubernetes IDE) - https://k8slens.dev
- k9s - https://k9scli.io - a command-line tool to check and manage your cluster.Quick start guide:  sudo snap install k9s (Linux) / brew install k9s (MacOS) followed by k9s --kubeconfig=$your-kubeconfig -n all
- Microk8s - https://microk8s.io/docs
- Rancher - https://rancher.com/docs/