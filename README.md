# ADV360-PRO-ZMK

## To build Firmware in GitHub Actions

### Setup

1. Fork this repo.
2. Enable GitHub Actions on your fork.

### Build firmware

1. Push a commit to trigger the build.
2. Download the artifact.

## Local building in a container

### Setup

#### Software

Either Podman or Docker is required, Podman is preferred if both are present.\
Make is also required

#### Windows specific
If compiling on Windows use WSL2 and Docker [Docker Setup Guide](https://docs.docker.com/desktop/windows/wsl/).\
Install make using `sudo apt-get install make`.\
The repository can be cloned directly into the WSL2 instance or accessed through the C: mount point WSL provides by default (`/mnt/c/path-to-repo`).

### Build firmware

1. Execute `make`.
2. Check the `firmware` directory for the latest firmware build.

### Cleanup

The built docker container and compiled firmware files can be deleted with `make clean`.

## Flashing firmware

Follow the programming instruction on page 8 of the [Quick Start Guide](https://kinesis-ergo.com/wp-content/uploads/Advantage360-Professional-QSG-v8-25-22.pdf) to flash the firmware.

## Other support

Further support resources can be found on Kinesis.com
https://kinesis-ergo.com/support/kb360pro/#firmware-updates
https://kinesis-ergo.com/support/kb360pro/#manuals


## Generate Keymap SVG




1. install [`pipx`](https://pypa.github.io/pipx/)
```
brew install pipx
pipx ensurepath
```

2. install [`keymap-drawer`](https://github.com/caksoylar/keymap-drawer)
```
pipx install keymap-drawer
keymap --help
```

3. parse `.keymap` file to yaml
```
 keymap parse -z config/adv360.keymap > config/adv360.yaml
```

4. draw `.svg` using parsed keymap yaml + QMK layout format info.json
```
keymap draw -j config/info.json config/adv360.yaml > adv360.svg
```

Repeat steps 3-4 after every modification to `config/adv360.keymap` to keep the `adv360.svg` up to date

#### TODO - automate this process