user_add
=========

Create a user and add it to sudoers.d

Role Variables
--------------

`rv_user_add_user_primary_group`

* Type: `String`
* Required: `false`
* Default: `{{ rv_user_add_username }}`
* Description: Group Name : Primary Group of the user

`rv_user_add_user_primary_gid`

* Type: `int`
* Required: `false`
* Default: `omit`
* Description: Group ID : GID for primary group

`rv_user_add_username`

* Type: `String`
* Required: `true`
* Description: Username

`rv_user_add_uid`

* Type: `int`
* Required: `false`
* Default: `omit`
* Description: User ID : UID

`rv_user_add_password`

* Type: `String`
* Required: `false`
* Description: Clear text password for the user

`rv_user_add_user_extra_groups`

* Type: `List<String>`
* Required: `false`
* Description: Groups : Extra groups for user

`rv_user_add_ssh_access_public_key`

* Type: `String`
* Required: `false`
* Description: Public key for remote ssh access

`rv_user_add_user_nopasswd_commands`

* Type: `List<String>`
* Required: `false`
* Description: Commands user will be able to run without password

Example Playbook
----------------

* Requirements

```yaml
- src: git@github.com:arpanrec/ansible-role-user-add.git
  scm: git
  name: arpanrec.user_add
```

* Uses

```yaml
- name: Add application user
  include_role:
    name: arpanrec.user_add
  vars:
    rv_user_add_username: 'arpan'
    rv_user_add_ssh_access_public_key: ssh-rsa yc2E
```

Testing
-------

Prerequisite: `docker`, `python3-pip`

```bash
git clone git@github.com:arpanrec/ansible-role-user-add.git arpanrec.user_add
cd arpanrec.user_add
pip install --user --upgrade virtualenv
virtualenv venv
source venv/bin/activate
pip install -r requirements.txt
molecule test
```

License
-------

`MIT`
