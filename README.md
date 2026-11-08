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
| `plex_rpm_repo_uri` | `https://repo.plex.tv/rpm/` | Plex YUM/DNF repository URL (RedHat/Fedora) |
| `plex_repo_key_url` | `https://downloads.plex.tv/plex-keys/PlexSign.v2.key` | GPG key used to sign the repositories |
| `plex_package` | `plexmediaserver` | Package to install |
| `plex_service_name` | `plexmediaserver` | Service name to manage |
| `plex_service_state` | `started` | Desired service state |
| `plex_service_enabled` | `true` | Whether the service starts at boot |
| `plex_data_dir` | `null` | Library/application-support directory (created, owned by `plex`) |
| `plex_temp_dir` | `null` | Transcoding temp directory (created, owned by `plex`) |
| `plex_run_user` | `null` | Run the service as this user (must already exist) |
| `plex_run_group` | `null` | Run the service as this group (must already exist) |
| `plex_service_overrides` | `{}` | Any additional `[Service]` directives |

Service Configuration
---------------------

Customisation is applied as a systemd drop-in at
`/etc/systemd/system/plexmediaserver.service.d/override.conf` (the method
Plex documents; the packaged unit is never edited). Changing any of these
options restarts the service; clearing them all removes the drop-in.

```yaml
- hosts: all
  roles:
    - role: carlosroman.plex
      vars:
        plex_data_dir: /mnt/media/plex-library
        plex_temp_dir: /mnt/nvme/plex-transcode
        plex_service_overrides:
          LimitNOFILE: 65536
```

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
