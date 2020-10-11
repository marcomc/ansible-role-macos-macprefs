[![Build Status](https://travis-ci.com/marcomc/ansible-role-macos-macprefs.svg?branch=master)](https://travis-ci.com/marcomc/ansible-role-macos-macprefs)

# ansible-role-macos-macprefs
An Ansible role to install 'macprefs' tool on macOS via Homebrew

If MacPrefs is not installed in the system it will ne installed via Homebrew.

Used in [Splinter, an opinionated provisioning tool for macOS](https://github.com/marcomc/splinter).

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
        macprefs_regular_backup: 720 # every 12 hours
        macprefs_backup_dir: ~/Library/Mobile Documents/com~apple~CloudDocs/Macprefs # use iCloud instead of Dropbox

      roles:
        - marcomc.macos_macprefs

## Variables

    verbose: no
    target_user_id: "{{ ansible_user_id }}"
    target_user_default_shell: ''
    macprefs_update_for_all_shell_types: no
    macprefs_backup_dir: "~/Dropbox/MacPrefsBackup"
    macprefs_regular_backup: 0
    macprefs_log: '~/Library/Logs/macprefs.log'

By default MacPrefs will look for its backup folder in your Dropbox directory, but this assumes that Dropbox is already installed and configured in your system.

My personal preference is to have MacPrefs to backup into iCloud especially if you are using this role to restore your configuration on a new machine in which you have already signed in with iCloud which is part of the Setup Assistant process.

## Setup periodic backup with Cron
Allow Full Disk Access to `cron` (manual operation)

1. Open `System Preferences -> Security & Privacy -> Privacy -> Full Disk Access`
  * Authenticate to unlock the list of allowed applications


2. Open the finder window to show the location of the `cron` binary

        open /usr/sbin/ # will

3. Drag & Drop the `cron` binary file into the `Full Disk Access` list

## Continuous integration
This role has (not yet) a travis basic test (for github) only.

## Troubleshooting & Known issues

## License
[MIT](LICENSE)

## Copyright
Marco Massari Calderone (c) 2020 - marco@marcomc.com
