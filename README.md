# ansible-role-macos-macprefs
An Ansible role to install 'macprefs' tool on macOS via Homebrew

If MacPrefs is not installed in the system it will ne installed via Homebrew.


## (Soft) Requirements & Dependencies
* [Jeff Geerling](https://github.com/geerlingguy)'s' [geerlingguy.homebrew](https://github.com/geerlingguy/ansible-role-homebrew) which is defined as Ansible Galaxy dependency

### Ansible
It was tested on the following versions:
 * 2.9

### Operating systems
Target MacOS 10.15 possibly earlier versions too (not yet tested)

## Example Playbook
Just include this role in your list.
For example

    - host: all
      vars:
        macprefs_backup_dir: ~/Library/Mobile Documents/com~apple~CloudDocs/Macprefs/
      roles:
        - marcomc.macos_macprefs_restore

## Variables

    macprefs_backup_dir: "~/Dropbox/MacPrefsBackup" # Directory where the MacPrefs are stored

By default MacPrefs will look for its backup folder in your Dropbox directory, but this assumes that Dropbox is already installed and configured in your system.

My personal preference is to have MacPrefs to backup into iCloud especially if you are using this role to restore your configuration on a new machine in which you have already signed in with iCloud which is part of the Setup Assistant process.

## Continuous integration
This role has (not yet) a travis basic test (for github) only.

## Troubleshooting & Known issues

## Copyright
Marco Massari Calderone (c) 2020

## License
MIT
