# molecule example

Example project of how to use molecule based upon:

- [Developing and Testing Ansible Roles with Molecule and Podman - Part 1](https://www.ansible.com/blog/developing-and-testing-ansible-roles-with-molecule-and-podman-part-1)
- [Developing and Testing Ansible Roles with Molecule and Podman - Part 2](https://www.ansible.com/blog/developing-and-testing-ansible-roles-with-molecule-and-podman-part-2)

## Usage

### Clone repository & install requirements

```bash
$ git clone https://github.com/AnwarYagoub/molecule-example.git
$ python3 -m venv molecule-venv
$ source molecule-venv/bin/activate
(molecule-venv) $ pip install --upgrade pip
(molecule-venv) $ pip install -r requirements.txt
```

### Verify installation

```bash
(molecule-venv) $ molecule --version
molecule 3.5.2 using python 3.6 
    ansible:2.9.27
    delegated:3.5.2 from molecule
    podman:1.0.1 from molecule_podman requiring collections: containers.podman>=1.7.0 ansible.posix>=1.3.0
```

### Configure SELinux to allow containers to run Systemd

```bash
(molecule-venv) $ sudo setsebool -P container_manage_cgroup 1
(molecule-venv) $ getsebool -a | grep container_manage_cgroup
container_manage_cgroup --> on
```

### Login to Red Hat registry

```bash
(molecule-venv) $ podman login registry.redhat.io
Username: YOUR-USERNAME-GOES-HERE
Password: 
Login Succeeded!
```

### Execute tests

```bash
(molecule-venv) $ cd mywebapp
(molecule-venv) [mywebapp] $ molecule test
```
