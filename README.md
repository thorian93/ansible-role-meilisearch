# Ansible Role: MeiliSearch

This role installs and configures [MeiliSearch](https://docs.meilisearch.com/) on Debian/Ubuntu, RHEL/CentOS, Fedora and openSUSE servers.

[![Ansible Role: MeiliSearch](https://img.shields.io/ansible/role/55138?style=flat-square)](https://galaxy.ansible.com/thorian93/meilisearch)
[![Ansible Role: MeiliSearch](https://img.shields.io/ansible/quality/55138?style=flat-square)](https://galaxy.ansible.com/thorian93/meilisearch)
[![Ansible Role: MeiliSearch](https://img.shields.io/ansible/role/d/55138?style=flat-square)](https://galaxy.ansible.com/thorian93/meilisearch)

## Here be Dragons!

This role is a first approach on this matter. Use with caution!

## Known issues

None.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: foobar
      roles:
        - role: thorian93.meilisearch
          become: yes

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    meilisearch_state: started
    meilisearch_enabled_at_boot: true

Start and enable MeiliSearch at boot.

    meilisearch_user: 'meilisearch'
    meilisearch_group: 'meilisearch'

Configure the user and group to run meilisearch as. **These will be created, so do not use existing users, as they will be modified!**

    meilisearch_exe_path: '/usr/bin/meilisearch'

Configure the path where the binary should be placed.

    meilisearch_db_path: '/var/lib/meilisearch'

Configure the path where the database should be placed.

    meilisearch_listen_ip: 127.0.0.1
    meilisearch_listen_port: 7700

Configure the IP and port on which MeiliSearch should listen.

    meilisearch_master_key: 'Y0urVery-S3cureAp1K3y'

The MeiliSearch master key. This should be changed obviously. For more information see [this link](https://docs.meilisearch.com/reference/features/configuration.html#master-key).

## Dependencies

None.

## OS Compatibility

This role ensures that it is not used against unsupported or untested operating systems by checking, if the right distribution name and major version number are present in a dedicated variable named like `<role-name>_stable_os`. You can find the variable in the role's default variable file at `defaults/main.yml`:

    role_stable_os:
      - Debian 10
      - Ubuntu 18
      - CentOS 7
      - Fedora 30

If the combination of distribution and major version number do not match the target system, the role will fail. To allow the role to work add the distribution name and major version name to that variable and you are good to go. But please test the new combination first!

Kudos to [HarryHarcourt](https://github.com/HarryHarcourt) for this idea!

## Example Playbook

    ---
    - name: "Run role."
      hosts: all
      become: yes
      roles:
        - ansible-role-meilisearch

## Contributing

Please feel free to open issues if you find any bugs, problems or if you see room for improvement. Also feel free to contact me anytime if you want to ask or discuss something.

## Disclaimer

This role is provided AS IS and I can and will not guarantee that the role works as intended, nor can I be accountable for any damage or misconfiguration done by this role. Study the role thoroughly before using it.

## License

MIT

## Author Information

This role was created in 2021 by [Thorian93](http://thorian93.de/).
