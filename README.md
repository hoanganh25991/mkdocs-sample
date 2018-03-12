# Documentation with mkdocs

## Installation
#### 1. mkdocs

mkdocs based on `python`, install with `pip`

```
  # Make sure python & pip already installed
  # Installing MkDocs
  # Installing Material Design theme for MkDocs
  pip install mkdocs
  pip install mkdocs-material
```  

#### 2. Serve docs files
Common `mkdocs.yml` config

```
site_name: MkDocs
theme:
  name: material
pages:
  - Blockchain:
    - Truffle Boilerplate: blockchain/truffle-boilerlate.md
markdown_extensions:
  - admonition
docs_dir: docs
dev_addr: 0.0.0.0:8000
```

```
mkdocs serve
```

#### 3. Build static files

```
mkdocs build
```