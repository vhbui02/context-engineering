# context-engineering

Auto fetch 3rd-party tools docs and build into clean LLM-feedable content.

```sh
$ git clone --depth=1 https://github.com/vhbui02/context-engineering.git
```

## Prerequisites

System packages:

```sh
$ sudo apt install -y git rsync python3 python3-venv
```

Populate local `vars.yml`:

```sh
$ cp host_vars/localhost/vars.yml.example host_vars/localhost/vars.yml
```

Set up Python environment and Ansible tools:

```sh
$ python -m venv .venv
$ .venv/bin/pip install ansible-dev-tools
```

Install Ansible collection dependencies:

```sh
$ .venv/bin/ansible-galaxy collection install -r requirements.yml
```

## Usage

Extract documentation for all configured repositories:

```sh
$ .venv/bin/ansible-playbook extractor.yml
```

Extract documentation for a specific repository using its tag:

```sh
$ .venv/bin/ansible-playbook extractor.yml --tags axios
```

Verify playbooks and tasks with `ansible-lint`:

```sh
$ .venv/bin/ansible-lint
```

## Output

Generated documentation files are stored in `build/` as single markdown files named `build/<YYYY-MM-DD>-<repo_name>-<version>.md`.
