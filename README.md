# brainfree-bedrock-server

> Zero Afterthought Required, Automagic Updates, Unpriviliged by Default

## About

## Installing

### Prerequisites

- Ubuntu Host or VM
  Tested On
  
  - Digital Ocean Ubuntu VPS
  
  - Ubuntu 22.04
  
  - WSL2

### Dependencies

```bash
sudo apt install wget screen unzip
```

### User Configuration

```bash
sudo adduser minecraft
sudo loginctl enable-linger minecraft
```

### Unpacking

```bash
sudo -iu minecraft
wget -O brainfree-bedrock-server.tgz https://api.github.com/repos/vt520/brainfree-bedrock-server/tarball/master
tar xzf brainfree-bedrock-server.tgz
```

### Optional: Updating an Existing Server

Stop your existing `bedrock-server and create a tar archive of the folder.  For Example:

```bash
cd path/to/minecraft
tar cf ../minecraft-backup.tar ./
```

Copy that `tar` file to your new minecraft host or account

```bash
scp ../minecraft-backup.tar minecraft@minecraft.houseonhill.net
```

Then from the new server, extract the `tar` file into the `minecraft-backup` folder

```bash
ssh minecraft@minecraft.houseonhill.org
mkdir minecraft-backup
cd minecraft-backup
tar xf ../minecraft-backup.tar
cd ..
ln -s ~/minecraft-backup ~/previous-bedrock-version
```

### Installing brainfree-bedrock-server

Execute the following to install and configure `brainfree-bedrock-server` with the most current release of `bedrock-server`

```bash
source ~/.profile
bedrock_install
```

## tl/dr; I want it now!

> Installation Procedure for the Grossly Impatient

This will overwrite things you may want to keep in in the given profile.  It will probably install properly; well bedrock-server will install, but who knows what else it just clobbered... don't be a braindead, rather use a service account the brainfree way.

```bash
cd ~
sudo loginctl enable-linger $(id -un)
wget -q --show-progress\
  -O brainfree-bedrock-server.tgz \
  https://github.com/vt520/brainfree-bedrock-server/tarball/master 
tar xzf brainfree-bedrock-server.tgz
source ~/.profile
bedrock_install
```

# 

## Core Utilities

- **`bedrock_activate_release`** _`release-id`_ 
  Selects the `bedrock-server` identified by `release-id` to the `current-version` 

- **`bedrock_active_release`**
  Reports the `bedrock-server` `release-id` that is currently selected for use

- **`bedrock_apply_previous_configuration`**
  Copies configuration files from the `previous-bedrock-server` to `bedrock-server`

- **`bedrock_clone_server_as`** `release-id`
  Duplicates `bedrock-server` to the given `release-id`  in `INSTALL_BASE`

- **`bedrock_console`**
  Attaches to the currently running `bedrock-server` admin console

- **`bedrock_current_release`**
  Retrives the current *`release-id`* and downloads the current `release-archive`

- **`bedrock_daemon`**
  Starts the currently active `bedrock-server` using `screen`  that can be attached to using `bedrock_console`

- **`bedrock_http_request`** *`wget-options`* `url`
  `wget` wrapper for http requests

- **`bedrock_install`**
  Installs and activates the current stable `bedrock-server` 

- **`bedrock_install_release`** *`release-id`*
  Installs a `bedrock-server` `release-archive` identified by `release-id` so that is is ready to be activated

- **`bedrock_install_services`**
  Installs the `systemd` units for `brainfree-bedrock-server`

- **`bedrock_release_installed`** **`release-id`**
  Report if `release-id`  has been installed and is available for activation

- **`bedrock_server_can_linger`**
  Report if `systemd` has been configured properly for the `brainfree-bedrock-server` units.

- **`bedrock_server_running`**
  Reports if the `systemd` service for `bedrock-server` is running

- **`bedrock_start_serverices`**
  Initiates all services required to run and update `bedrock-server`

- **`bedrock_stop_server`**
  Sends a `stop` command to the `bedrock-server`

- **`bedrock_stop_services`**
  Stops `systemd` services that execute `bedrock-server`

- **`bedrock_update_server`**
  Tests if a new version of `bedrock-server` is available and if so automatically install and activate it

- **`bedrock_update_brainfree`**
  Downloads and extracts the most current release of the `brainfree-bedrock-sever` scripts and reinitialized services.
  **Note**: this command must be manually run, never automatically update *production alpha* software (read: this).  Only update when you really need to (ie: Microsoft significantly alters the download process, it's otherwise broken).
