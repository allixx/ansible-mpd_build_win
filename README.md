# MPD for Windows builder

A simple Ansible role to automate a tedious process of building MPD for Windows.

It's been developed and tested against Ubuntu 22.04. Since it was designed to run on a disposable VM, there's no care taken for proper privilege separation and control: the process runs under root account.

Build state between runs are not kept intentionally.

MPD is built with build script using mingw-w64 as documented in https://mpd.readthedocs.io/en/stable/user.html#compiling-for-windows

## Configuration

Specify connection parameters for builder host in inventory.ini.

Customize build options in `host_vars/builder/builder.yml`. Consult `roles/mpd_build_win/defaults/main.yml` for possible configuration values. For example, you can select which 3rd party libs to include by editing `mpd_build_win_libs` variable.

## Running a build

```
ansible-playbook mpd_build_win.yml
```

At the end of playbook run you'll have `mpd.exe` delivered to `/tmp/` on controller system.
