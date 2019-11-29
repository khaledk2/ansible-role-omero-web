# Breaking changes when switching to Python 3
***This is for development and testing purposes only. Do not use on a production server.***

When `omero_web_python3: true` the following breaking changes take place.

This will be the default in the next major release of this role.
Note this role should handle upgrades.

## Changes
- `/opt/omero/web/OMERO.web/` is a directory not a symlink.
- The virtualenv path is `/opt/omero/web/venv3` and does not include system-site-packages.
- Home directory of `omero_web_system_user` is changed from `/opt/omero/web` to `/opt/omero/web/OMERO.web/var`.
  This increases security by restricting the directories that are writeable by `omero_web_system_user`.
- The [omero-web-apps](https://galaxy.ansible.com/ome/omero_web_apps) role has been merged into this role.
- `omero_web_release` does not support `latest`, only `present` and full versions.

There may be other breaking changes before release.


# Changes in Version 2

## Removed variables
- `omero_web_upgrade`: This variable is now an internal variable.
  Upgrades are automatically executed depending on the value of `omero_web_release` which can be set to `present`, `latest` or a fixed version.