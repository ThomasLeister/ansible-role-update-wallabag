# update-wallabag Ansible Role

## Purpose

This role updates a Wallabag instance by checking the current local version and comparing it to the latest official Wallabag version. If a newer version is available, the role will update Wallabag by running "make update" on the instance.

## Configuration

There are two configuration parameters:

* `wallabag_root_dir`:  Root directory where Wallabag is located
* `wallabag_php_user`:  Owner of the Wallabag files / user who's running Wallabag.

## Example 

Example of a Playbook which is making use of the role:

```
- name: Update Wallabag
  hosts: wallabag-server
  roles:
    - update-wallabag
  vars:
    wallabag_root_dir: /var/www/myserver.tld/wallabag.myserver.tld/wallabag
    wallabag_php_user: www-data
```


## Limitations

This ansible role is pretty dumb and does not do a lot of checks, e.g. the version string comparison is just a simple "not equals". Also don't forget that updates might not always be as simple as `make update` as Wallabag's [upgrade page](https://doc.wallabag.org/en/admin/upgrade.html) shows. 

_In case the update failed you will probably run `make update` manually on the server because the script will not recognize if a previous update attempt has been successful. It will assume that you already are running the latest version because it just compares Git tags._




