macbook-provisioning
====================

Ansible playbook to get a macbook workstation up and running.

| This is a fork of @marvelley's repo, and I thank him for laying the groundwork. I have modified the list of packages to my liking, and updated a couple of things. In addition, this playbook now also handles installing *`npm`* and *`Atom`* packages. |
|--- |
| See http://marvelley.com/blog/2014/04/11/local-provisioning-with-ansible/ for the original author's blog. |

Additionally, I have pulled ideas/techniques from:
  - https://github.com/phillipalexander/ansible-mac
  - http://blog.james-carr.org/2016/03/29/managing-your-macbook-with-ansible/

Below are some notes on usage, as well as what else I have needed to do after running this playbook.


# Todo

1. Clean up brew and brew-cask installs.
1. Clean up and discover how to install software from the Apple Store.
1. Automatic updates for installed software.
1. VPN install, AnyConnect~~/OpenConnect.~~


## Manual Steps (prerequisites):

1. Install **Xcode** via the **Apple App Store**
  - Install the command line tools by opening a terminal and typing

  <!-- language: lang-sh -->
        sudo xcode-select --install

  - Accept the Xcode license with

  <!-- language: lang-sh -->
        sudo xcodebuild -license

  - Verify the install with

  <!-- language: lang-sh -->
        xcode-select -p

  **Output =>** `/Applications/Xcode.app/Contents/Developer`

1. Get this **repo** onto the machine you want to configure. (_traditional download if you don't have `git` on your system._)

  <!-- language: lang-sh -->
       mkdir -p sandbox; cd sandbox;
       git clone https://github.com/zombieprocess/macbook-provisioning.git

1. Modify `playbook.yml` to have your username/email/etc and `group_vars/all` for adjusting desired packages.

  <!-- language: lang-sh -->
       vim playbook.yml;
       vim group_vars/all

## Running the playbook:

1. Run the following to install *ansible*

  <!-- language: lang-sh -->
        sudo bash bootstrap.sh

    **Note:** it may be necessary to manually install brew before running `bootstrap.sh`
    If you encounter permissions errors, re-run with `sudo`.
    It will likely fail when brew attempts to install something as `sudo`, at which point re-run without sudo.
    Wash-rinse-repeat until it runs to completion.
1. Finally, run this

  <!-- language: lang-sh -->
        ansible-playbook -K playbook.yml

## Afterwards...

### Set up Chrome

1. Open Google Chrome
1. **Optional:** Navigate to http://lastpass.com
1. Log in
1. Install plugins in all browsers
1. Open Chrome again, and sign in to:
  1. email account(s)
  1. github
1. Sign in to Chrome to have your extensions populate automatically.
1. **Ad blocker:** `uBlock Origin`

### Set up VPN

1. Go to http://support.mrn.org and log in
1. Click 'Online Support'
1. Click 'Download'
1. Download the VPN client for your OS
1. Install the VPN client.
1. To connect, use `vpn.mrn.org`, and your Active Directory username/pwd

### Sign in to slack

Our domain is `mindresearchnetwork.slack.com`

### Install your SSH keys

Just copy your ssh keys to `~/.ssh`, be sure to update privs to `0600`

### Add apps to list of startup items
System Preferences -> Users -> Login Items

1. Slack

### Set up spaces hotkeys (optional)

1. Open *system preferences*
1. Click on *keyboard*
1. Click on *Shortcuts*
1. Change the shortcut keys for `Move left a space` and `Move right a space`

### Get an Windows 10 VM machine running (optional)

1. Download a Windows 10 image (64 bit): https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/mac/
1. Create a new Virtualbox VM with 2GB RAM and 16GB HD
1. Start new VM and point to ISO file
1. Install Virtualbox Guest Tools:
  1. Once windows is installed, go to http://download.virtualbox.org/virtualbox/
  1. Locate the current version of virtualbox and click it.
  1. Download VBoxGuestAdditions....iso
  1. Open ISO file in windows
  1. Double click the VirtualboxGuestUtilitiesamd64 executable
  1. Install per instructions
1. Allow all guest screen resolutions:
  1. Shutdown Windows guest VM
  1. Open Virtualbox application on Host OS again
  1. Open preferences (CMD + ,)
  1. Go to 'Display' tab
  1. Select 'None' for max resolution
  1. Start the windows VM again
1. Install Chrome
1. Set up browser for VMWare management
  1. In Host OS, connect to VPN
  1. In Windows VM, restart, then open Chrome browser
  1. Navigate to https://vcenter.mind.unm.edu:9443
  1. Do not log in yet: click 'Dowload VMWare Client Integration Plugin'
  1. Open the downloaded executable, and install per instructions
  1. In Chrome, navigate to `chrome://flags/#enable-npapi`, and click `enable`
  1. Click `Relaunch` at bottom left
  1. In Chrome, navigate to `chrome://plugins/`
  1. Locate the two VMWare plugins, and check the 'Always allowed to run'
  1. (Possibly optional): navigate to chrome://settings/content
  1. (Possibly optional): Scroll to 'Unsandboxed Plugins' and select 'Allow all...'
  1. Restart
1. Install Vsphere Desktop client (note, the web client is supposed to replace the
  desktop client in the near future. Unfortunately, Chrome is discontinuing support
  for the kind of plugin that web client relies upon... It is probably best to have
  the web client and the desktop client configured and ready to go...)
