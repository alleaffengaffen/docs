# alleaffengaffen

![wip](https://img.shields.io/badge/Status-Work%20in%20Progress-important)

Kubernetes & Cloud lab of the-technat

We separate this logically and technically where possible to avoid damage to important stuff. Here are some timeless statements to make this happen and general guidelines to protect resources

## General
- banane@alleaffengaffen.ch is the mail address used for accounts and contacts
- dedicated orgs or accounts have to be used
- exception to above is GH which is used for code and as IDP 
- dedicated DNS alleaffengaffen.ch
- dedicated credit card (Visa) 
- Automation where possible or effective, but not everywhere (we want to understand things before automating them)
- prefered cloud providers are Hetzner or Infomaniak (GH for everything else)
- relies on my private DR to keep access to important accounts and data
- Github as IDP is preferred over dedicated accounts
- track things in issues directly in the coresponding repository

## Data
- S3 for all backups where backup is needed (configs shall be stored in git or docs)
- use automatic nuking to keep costs low (based on tags if possible)
- uses akeyless.io for sensitive data (e.g secrets for terraform, kubernetes, github) 

## Networking
- tailnet alleaffengaffen should be use for networking
- uses the public network with appropriate zero-trust security, hidding behind a FW is a no-go.

## Bucketlist

- Extend chezmoi install scripts to skip if already installed & pin versions
- Cluster-API management cluster using kind moved to openstack
- Implement Azure-nuke (& Hetzner) in account-nuker
- Postgresql Operator (Crunchydata or Zalando)
- Production-ready K3s Cluster on tailscale (for services that are better self-hosted)
- Try Crossplane to provision EKS clusters
- Install cluster using kubespray (and maybe Terraform + ansible provider inventory)
- Figure out if kOps should be used and with which platform (e.g add CI)
- Try Paralus for kubectl access
- Try Flatcar Linux (and get to know it)
- Linux from Scratch
- Kubernetes IPv6 (e.g use the /64 net of each host to create a truly public IPv6 cluster)
