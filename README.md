# Ansible Jemalloc Role

This role installs `Jemalloc`. For `CentOS`, it will install from the repo, for everything else it will compile it.

## Install Example

Assuming the directory looks like this:

```
.
├── ansible
│   └── roles
├── requirements.yml
```
In your `requirements.yml` file:

```yaml
---
- src: https://github.com/mikechau/ansible-jemalloc.git
  path: ansible/roles
  name: jemalloc
```

Install:

```
ansible-galaxy -r install requirements.yml
```

Alternatively, clone the repo and do whatever you need to do!

## Configuration

```yaml
# Specify the git repo to clone from.
# Default is https://github.com/jemalloc/jemalloc.git.
jemalloc_git_repo: https://github.com/jemalloc/jemalloc.git

# Version of jemalloc, this is actually a git repo tag.
# Default is 4.0.3.
jemalloc_version: 4.0.3

# The source path to download to.
# Default is /usr/local/src/jemalloc.
jemalloc_src_path: /usr/local/src/jemalloc

# NOTE: Must be defined inline with the role in the playbook.
# Valid options:
#   - source - download the repo and make install.
#   - package - install from a repo (CentOS only atm).
jemalloc_install_from: source

# Full path to where libjemalloc.so is located.
# Default is /usr/lib/libjemalloc.so.
jemalloc_lib_path: /usr/lib/libjemalloc.so

# This will make jemalloc be reinstalled everytime.
# Default is false.
jemalloc_force_install: false
```

## Usage

In your `playbook`:

```yaml
roles:
  - role: jemalloc
    jemalloc_install_from: source
    sudo: yes
```

## LICENSE

MIT
