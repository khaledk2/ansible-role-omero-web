# Changes in Version 5

## Summary of breaking changes

-  New optional variable `python_version` enables Python upgrades/downgrades. This variable is consumed in the included `ansible-role-python3-virtualenv` which will make a symlink to the virtualenv directory if symlink is not present. As indicated by `python_version`, `ansible-role-python3-virtualenv` also upgrades/downgrades the python version accordingly, creating a new venv directory to which the symlink is pointing to, and renaming the old one if present.

Note: if `python_version` is not specified in playbook, its default value `"3.12"` will cause an upgrade from e.g. pre-existing `"3.9"` Python version, renaming of the existing venv folder and creation of a symlink.

-   `omero_web_python_requirements_ice_package` is simplified, i.e. not a nested dictionary anymore.

# Changes in Version 4

## Summary of breaking changes

-   Python 2 support is now dropped
-   `omero_web_python_requirements_ice_package` is now a nested dictionary to
    support multiple versions per distribution

## Removed variables

- `omero_web_python3`: the role only installs OMERO.web with Python 3

# Changes in Version 3

## Summary of breaking changes
- Default to installing and running under Python 3.6.
  Set `omero_web_python3: false` to use Python 2.7.
- `/opt/omero/web/OMERO.web/` is a directory not a symlink.
- The virtualenv path is `/opt/omero/web/venv3` and does not include system-site-packages.
- Home directory of `omero_web_system_user` is changed from `/opt/omero/web` to `/opt/omero/web/OMERO.web/var`.
  This increases security by restricting the directories that are writeable by `omero_web_system_user`.
- The [omero-web-apps](https://galaxy.ansible.com/ome/omero_web_apps) role has been merged into this role.
- `omero_web_release` does not support `latest`, only `present` and full versions.

## Removed variables
- `omero_web_ice_version`: This is now an internal variable and must always be `3.6`.


# Changes in Version 2

## Removed variables
- `omero_web_upgrade`: This variable is now an internal variable.
  Upgrades are automatically executed depending on the value of `omero_web_release` which can be set to `present`, `latest` or a fixed version.
