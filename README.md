Snap of the Bibata Modern Ice Cursor themes created form  ful1e5 https://github.com/ful1e5/Bibata_Cursor

[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/bibata-modern-ice-cursor/listing)

---

## Attributions  

All credit goes to the original cursor developers

## Building the snap locally

Requirements
* [snapcraft](https://snapcraft.io/snapcraft) (```snap install snapcraft --classic```)
* [multipass](https://snapcraft.io/multipass) (```snap install multipass```)
* Get an copy of Bibata-Modern-Ice.tar.xz https://github.com/ful1e5/Bibata_Cursor/releases extract the tar.xz and create a zip file and place it in the bibata-modern-ice-cursor-snap folder

1. Clone the repository and enter the directory and generate the zip file
```bash
git clone https://github.com/Gabbajoe/bibata-cursors-snap
cd bibata-cursors-snap
wget https://github.com/ful1e5/Bibata_Cursor/releases/download/v2.0.6/Bibata-Modern-Ice.tar.xz
tar xJf Bibata-Modern-Ice.tar.xz
zip -r Bibata-Modern-Ice.zip Bibata-Modern-Ice
rm -r Bibata-Modern-Ice
rm Bibata-Modern-Ice.tar.xz
```

2. Build the snap
```bash
snapcraft
```

3. Install the snap. If you run an `ls -lh` from the build directory (`bibata-modern-ice-cursor`), there should see two files (or one if the optional step was taken). Using the below command, install the snap for the system's architecture

*Note: the `--dangerous` flag is used because this is local snap that hasn't been verified through the snap store [more details here](https://snapcraft.io/docs/install-modes#heading--dangerous)*
```bash
snap install bibata-modern-ice-cursor_2.0.6_amd64.snap --dangerous
```

## Applying the theme

In order to work, the snap package needs to have a '[plug](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)' 
available for 'icon-themes'.

To apply the theme to a single application, perform the following:

```bash
sudo snap connect [snap-you-want-to-theme]:icon-themes bibata-modern-ice-cursor
```

To apply to all applications run the following command. Thanks to @flexiondotorg for the handy loop.

```bash
for plug in $(snap connections | grep gtk-common-themes:icon-themes | awk '{print $2}'); do sudo snap connect ${plug} bibata-modern-ice-cursor:icon-themes; done
```

*NOTE*: Some apps like the Ubuntu Snap Store may require logging out, and back in to load the changes.
