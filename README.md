# Path-to-Prod Champions

This course is designed to:

1. Help users of the Path to Prod platform gain a deeper understanding of how the system works.
2. Encourage better cross team communication and support.
3. Foster a culture of collaboration through; feedback, bug reports, feature/pull requests.
4. Train P2P Champions within development teams

## Course pre-requisites

### Please make sure that you have the following access:

Navigate to: 
https://federation.reedelsevier.com/adfs/ls/IdpInitiatedSignOn.aspx?loginToRp=urn:amazon:webservices

Find: rosetta-lexadvuk-sandbox (233288417281)
Select: ADFS-Developer

### Install the latest AWSCLI


### Connect to the sandbox apps cluster

aws eks update-kubeconfig --name apps

### Install a namespace switching tool

For MacOSX install kubectx (this might be powershell only)
For Windows try kubectxwin / https://github.com/thomasliddledba/kubectxwin
    or use https://github.com/kubernetes-sigs/krew to install a namespace switching tool


## Markdeck Instructions
To view the presentation in a browser, simply enter...
```
$ .start
```
...and navigate to http://localhost:8080.

To view the PDF instead, download [deck/p2p-champions.pdf](https://github.com/LexisNexis/p2p-champions/raw/master/deck/p2p-champions.pdf).
