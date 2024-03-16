Snap of the Oxygen cursor themes (from both the oxygen-cursor-theme and oxygen-cursor-theme-extra packages) originally created for KDE 4.

[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/oxygen-cursors)

---

## Attributions  

All credit goes to the original cursor developers of the KDE project and the package maintainers at Kubuntu.  

## Building the snap locally

Requirements
* [snapcraft](https://snapcraft.io/snapcraft) (```snap install snapcraft --classic```)
* [multipass](https://snapcraft.io/multipass) (```snap install multipass```)

1. Clone the repository and enter the directory
```sh
git clone https://github.com/jollygoose/oxygen-cursors-snap
cd oxygen-cursors-snap
```

2. Build the snap
```
snapcraft
```

(Optional) Two snaps packages will be built, one for the `amd64` architecture, and for `arm64`. If only building for a single local system, you can comment out the uneeded architecture in the snapcraft.yaml file. The build is pretty quick and files relatively small ~4MB so skipping this will be fine.
```
architectures:
  - build-on: [arm64, amd64] # remove for amd64 only
    build-for: [arm64] # remove for amd64 only
  - build-on: [arm64, amd64] # remove for arm64 only
    build-for: [amd64] # remove for arm64 only
```

3. Install the snap. If you run an `ls -lh` from the build directory (`oxygen-cursors-snap`), there should see two files (or one if the optional step was taken). Using the below command, install the snap for the system's architecture. If unsure of the 
architecture, check by using `uname -m`. If it outputs `aarch64` using `arm64`. If it says `x86_64` then use `amd64`.

*Note: the `--dangerous` flag is used because this is local snap that hasn't been verified through the snap store [more details here](https://snapcraft.io/docs/install-modes#heading--dangerous)*
```
# arm64 system install 
snap install oxygen-cursors_0.0.2012-06-kde4.8-2.1ubuntu1_arm64.snap --dangerous
# amd64 system install
snap install oxygen-cursors_0.0.2012-06-kde4.8-2.1ubuntu1_amd64.snap --dangerous
```

## Applying the theme

In order to work, the snap package needs to have a '[plug](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)' 
available for 'icon-themes'.

To apply the theme to a single application, perform the following:

```bash
sudo snap connect [snap-you-want-to-theme]:icon-themes oxygen-cursors:icon-themes
```

To apply to all applications run the following command. Thanks to @flexiondotorg for the handy loop.

```bash
for plug in $(snap connections | grep gtk-common-themes:icon-themes | awk '{print $2}'); do sudo snap connect ${plug} oxygen-cursors:icon-themes; done
```

*NOTE*: Some apps like the Ubuntu Snap Store may require logging out, and back in to load the changes.