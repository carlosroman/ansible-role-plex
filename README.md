Plex
====

An Ansible role for installing Plex.

Requirements
------------

This role requires Ansible 2.21 or higher.

Role Variables
--------------

| Variable | Default | Description |
|---|---|---|
| `plex_repo_uri` | `https://repo.plex.tv/deb/` | Plex APT repository URI (Debian/Ubuntu) |
| `plex_repo_suite` | `public` | Plex APT repository suite |
| `plex_repo_key_url` | `https://downloads.plex.tv/plex-keys/PlexSign.v2.key` | GPG key used to sign the repository |
| `plex_package` | `plexmediaserver` | Package to install |
| `plex_service_name` | `plexmediaserver` | Service name to manage |
| `plex_service_state` | `started` | Desired service state |
| `plex_service_enabled` | `true` | Whether the service starts at boot |

Dependencies
------------

None.

Example Playbook
----------------

```yaml
- hosts: all
  roles:
    - role: carlosroman.plex
```

License
-------

MIT

Author Information
------------------

[Carlos Roman](https://github.com/carlosroman)
