# AI Odyssey 2025 demo-project
<div align="center">
<img src="./VirtualAIOdysseyLogo.png" width="150" height="150">
</div>
<br/>

<br/><b>[AI Odyssey Demo AI Starter Kit - RAG and NL2SQL](https://docs.google.com/presentation/d/1hNml-zEJ53uW1xOFJHf4zDsSAr4EoOBY0MFTheHTV5I/edit?usp=sharing)</b>

## Infrastructure Deployment Instructions
We are using the demo system to setup the ROSA Workshop environment. 
This environment will be modified by replacing the worker nodes with instances that provide the needed accelerators and vRAM.

As part of the setup we deploy OpenShift AI, Dev Spaces, Pipelines, MinIO and setup users into groups with dedicated namespaces. This allows for collaboration in isolated groups such as during a build-a-thon event.

#### The environment is setup to
 * run the AI Starter Kit (RAG and NL2SQL) demo showcased below (after running ./setup.sh, you will run ./app.sh for the AI Starter Kit installation) as well as the Fraud Detection demo incl. S3 connections
 * show the inner/outer loop for application development/deployment
 * serve models
 * integrate models into the application during development/deployment

![Ecosystem Overview](img/ecosystem-overview.png)

### Steps to get started
> Start with https://demo.redhat.com
* Search for and deploy [`ROSA Workshop`](https://catalog.demo.redhat.com/catalog/babylon-catalog-prod/order/sandboxes-gpte.rosa-mobb.prod) 
* Using **Hosted Control Plane**
* Set up **cluster admin** in ROSA

> This repo contains `setup.sh` to kick off the set-up process via ssh access to the bastion (be sure to have ssh-agent running)

> Pre-requisites for the setup are:
- [ ] ssh key with git access ready to copy to bastion

> Questions asked during setup (`grep '_?' setup.sh`):
- [ ] demo cluster information
  - [ ] bastion hostname
  - [ ] bastion ssh password
  - [ ] rosa api url
  - [ ] rosa admin password
- [ ] instance type and min/max # of nodes desired
- [ ] ROSA version to upgrade to (next highest version)

It will start on your local machine by gathering initial information and then copying your public ssh key to the bastion host for future access. There it will run following steps (can be re-started on bastion by providing the step number to `setup.sh` such as `./setup.sh 4`)

> To see all steps `grep 'Step' setup.sh`

1. Local ssh access setup
2. Setup ROSA
3. Configure ROSA machine pool
4. Upgrade ROSA
5. Finish Openshift Setup
6. Install Operators
   * Web Terminal Operator
   * OpenShift Service Mesh
   * OpenShift Serverless
   * Authorino
   * OpenShift AI
   * OpenShift Pipelines
   * OpenShift Dev Spaces
     * CheCluster
7. Install Hardware Accellerators
8. Create namespace and roles for each team, setup users (10 per group) into groups (up to 30)
   * DevSpaces Application development 
   * OpenShift AI 
     * Minio OBS and two connections
     * Routes
     * Workbench

> You will find the user/group details in the `~/ai-starter/scratch/` folder in the `rosa` home directory on the bastion host

**Preview Output:**
```
source tools/format.sh; eval "$(egrep '\s_{2}\s' setup.sh)"
```

## AI Demo Architecture
![ai-hackathon-starter](architecture.png)

## AI Demo Deployment Instructions
After ```./setup.sh``` completes, simply run ```./app.sh``` to kick off the demo application installation

## Testing The Application
Once ./app.sh completes successfuly you can [follow these instructions to try the application](testing-the-application-readme)

