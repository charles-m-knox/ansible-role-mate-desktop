# mate-desktop

Configures Mate Desktop the way I want.

## Requirements

There are no requirements for this, it should work out of the box with Ansible.

## Role Variables

There are a few variables. See `defaults/main.yml` for values that can be tweaked on a per-host basis.

## Dependencies

<!-- A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles. -->

None at the moment.

## Usage

First, create a `requirements.yml` in your Ansible setup if you haven't already, here's an example:

```yaml
---
collections:
  - name: community.general
  - name: ansible.posix
  - name: community.crypto

roles:
  - name: charles-m-knox.mate-desktop
    src: https://github.com/charles-m-knox/ansible-role-mate-desktop.git
    scm: git
    version: main
```

Next, install it:

```bash
# include the -f flag to forceably re-install and get the latest (equivalent to
# upgrading)
ansible-galaxy role install -f -r requirements.yml
```

Now, in your `site.yml` (or whatever your playbook is named), use the role - note that root access is required for some of the steps:

```yaml
- name: mate-desktop
  hosts: all
  roles:
    - charles-m-knox.mate-desktop
  tags:
    - mate-desktop
```

Some tasks may not be desirable, in which case you may want to step through instead:

```bash
ansible-playbook site.yml --tags mate-desktop --step
```

## Development tips

You can test out `dconf load` on the commandline like this:

```bash
dconf load /org/mate/pluma/ <<EOF
[/]
bottom-panel-size=160

[plugins/filebrowser/on-load]
tree-view=true
EOF
```

## License

MIT

## Author Information

<https://charlesmknox.com>
