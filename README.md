macbook-provisioning
====================

A mirror of the Ansible scripts used to provision my Macbook, minus any private stuff.

See http://marvelley.com/blog/2014/04/11/local-provisioning-with-ansible/ for details.

# Usage

1. Get this repo onto the machine you want to configure.
2. Install X-Code via the App Store
3. Install the command line tools by opening a terminal and typing `xcode-select --install`
4. Open the X-Code app, and agree to terms, and allow it to complete installation.
5. Run `bootstrap.sh` to install ansible
6. Run `ansible-playbook -i hosts playbook.yml`

### Set up alfred

1. Open Alfred preferences, click 'advanced'
1. Change hotkey settings as desired
1. Click `Rebuild Application Cache`.
1. Click `Reindex OSX Metadata`
1. It may take a  while, but your installed apps should be searchable within Alfred

### Set up Chrome

1. Open Google Chrome
1. Navigate to http://lastpass.com
1. Log in
1. Install plugins in all browsers
1. Open Chrome again, and sign in to:
  1. email account(s)
  1. github

### Set up VPN
1. Go to http://support.mrn.org and log in
1. Click 'Online Support'
1. Click 'Download'
1. Download the VPN client for your OS
1. Install the VPN client.
1. To connect, use `vpn.mrn.org`, and your Active Directory username/pwd

### Sign in to slack
Our domain is mrncode.slack.com

### Set up spaces hotkeys
1. Open *system preferences*
1. Click on *keyboard*
1. Click on *Shortcuts*
1. Change the shortcut keys for `Move left a space` and `Move right a space`

### Install your SSH keys
Just copy your ssh keys to `~/.ssh`, be sure to update privs to `0600`
