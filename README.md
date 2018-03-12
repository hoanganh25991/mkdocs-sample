# DevOps Documentation


## 1. MkDocs Development

- 1.1. [Env] Installing MkDocs

```
  sudo -i
  
  # python --version
  
  # if pip not installed
  easy_install pip
  # show current pip version
  pip --version
  # upgrade pip
  pip install --upgrade pip
  
  # Installing MkDocs
  pip install mkdocs
  
  # Installing Material Design theme for MkDocs
  pip install mkdocs-material
```  

- 1.2. [Dev] Initial Project

```
  # cd /home/ubuntu/devops/ &
  # mkdocs new devopsdocs
  
  sudo git clone https://DigitalBusiness@bitbucket.org/DevOpsDEC/devopsdocs.git
```

## 2. MkDocs Deployment 

```
  cd /home/ubuntu/devops/devopsdocs/ &&
  mkdocs serve
```