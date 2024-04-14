[![Build Status](https://github.com/panda3d/panda3d/workflows/Continuous%20Integration/badge.svg?branch=master)](https://github.com/panda3d/panda3d/actions?query=branch%3Amaster+workflow%3A%22Continuous+Integration%22)
[![OpenCollective](https://opencollective.com/panda3d/backers/badge.svg)](https://opencollective.com/panda3d)
[![OpenCollective](https://opencollective.com/panda3d/sponsors/badge.svg)](https://opencollective.com/panda3d)

Panda3D
=======

<img src="https://avatars2.githubusercontent.com/u/590956?v=3&s=500" align="right" width="200" />

Panda3D is a game engine, a framework for 3D rendering and game development for
Python and C++ programs.  Panda3D is open-source and free for any purpose,
including commercial ventures, thanks to its
[liberal license](https://www.panda3d.org/license/). To learn more about
Panda3D's capabilities, visit the [gallery](https://www.panda3d.org/gallery/)
and the [feature list](https://www.panda3d.org/features/).  To learn how to
use Panda3D, check the [documentation](https://www.panda3d.org/documentation/)
resources. If you get stuck, ask for help from our active
[community](https://discourse.panda3d.org).

Panda3D is licensed under the Modified BSD License.  See the LICENSE file for
more details.

Building Panda3D
================

### Note:

Please ensure that you build Panda3D with Python 3.11.9.

Windows
-------

You can build Panda3D with the Microsoft Visual C++ 2015, 2017, 2019 or 2022
compiler, which can be downloaded for free from the [Visual Studio site](https://visualstudio.microsoft.com/downloads/).
You will also need to install the [Windows SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-sdk),
and if you intend to target Windows Vista, you will also need the
[Windows 8.1 SDK](https://go.microsoft.com/fwlink/p/?LinkId=323507).

You will also need the thirdparty dependency libraries available for
the build scripts to use.  These are available from one of these two URLs,
depending on whether you are on a 32-bit or 64-bit system, or you can
[click here](https://github.com/rdb/panda3d-thirdparty) for instructions on
building them from source.

- https://www.panda3d.org/download/panda3d-1.10.14/panda3d-1.10.14-tools-win64.zip
- https://www.panda3d.org/download/panda3d-1.10.14/panda3d-1.10.14-tools-win32.zip

After acquiring these dependencies, you can build Panda3D from the command
prompt using the following command.  Change the `--msvc-version` option based
on your version of Visual C++; 2022 is 14.3, 2019 is 14.2, 2017 is 14.1, and
2015 is 14.  Remove the `--windows-sdk=10` option if you need to support
Windows Vista, which requires the Windows 8.1 SDK.

```bash
makepanda\makepanda.bat --everything --installer --msvc-version=14.3 --windows-sdk=10 --no-eigen --threads=2
```

When the build succeeds, it will produce an .exe file that you can use to
install Panda3D on your system.

**Note:** you may choose to remove `--no-eigen` and build with Eigen support in
order to improve runtime performance.  However, this will cause the build to
take hours to complete, as Eigen is a heavily template-based library, and the
MSVC compiler does not perform well under those circumstances.

Linux
-----

Building Panda3D on Linux is easy.  All you need is to invoke the makepanda
script using the version of Python that you want Panda3D to be built against.

Run makepanda.py with the --help option to see which options are available.
Usually, you will want to specify the --everything option (which builds with
support for all features for which it detects the prerequisite dependencies)
and the --installer option (which produces an installable .deb or .rpm file
for you to install, depending on your distribution).

The following command illustrates how to build Panda3D with some common
options:
```bash
python3 makepanda/makepanda.py --everything --installer --no-egl --no-gles --no-gles2 --no-opencv
```

You will probably see some warnings saying that it's unable to find several
dependency packages.  You should determine which ones you want to include in
your build and install the respective development packages.  You may visit
[this manual page](https://docs.panda3d.org/1.11/python/distribution/thirdparty-licenses)
for an overview of the various dependencies.

If you are on Ubuntu, this command should cover the most frequently
used third-party packages:

```bash
sudo apt-get install build-essential pkg-config fakeroot python3-dev libpng-dev libjpeg-dev libtiff-dev zlib1g-dev libssl-dev libx11-dev libgl1-mesa-dev libxrandr-dev libxxf86dga-dev libxcursor-dev bison flex libfreetype6-dev libvorbis-dev libeigen3-dev libopenal-dev libode-dev libbullet-dev nvidia-cg-toolkit libgtk-3-dev libassimp-dev libopenexr-dev
```

Once Panda3D has built, you can either install the .deb or .rpm package that
is produced, depending on which Linux distribution you are using.  For example,
to install the package on Debian or Ubuntu, use this:

```bash
sudo dpkg -i panda3d*.deb
```

If you are not using a Linux distribution that supports .deb or .rpm packages, you
may have to use the installpanda.py script instead, which will directly copy the
files into the appropriate locations on your computer.  You may have to run the
`ldconfig` tool in order to update your library cache after installing Panda3D.

Alternatively, you can add the `--wheel` option, which will produce a .whl
file that can be installed into a Python installation using `pip`.

macOS
-----

On macOS, you will need to download a set of precompiled thirdparty packages in order to
compile Panda3D, which can be acquired from [here](https://www.panda3d.org/download/panda3d-1.10.14/panda3d-1.10.14-tools-mac.tar.gz).

After placing the thirdparty directory inside the panda3d source directory,
you may build Panda3D using a command like the following:

```bash
python makepanda/makepanda.py --everything --installer
```

You may target a specific minimum macOS version using the --osxtarget flag
followed by the release number, eg. 10.9 or 10.14.

If the build was successful, makepanda will have generated a .dmg file in
the source directory containing the installer.  Simply open it and run the
package file in order to install the SDK onto your system.





Supporting the Project
======================

If you would like to support the project financially, visit
[our campaign on OpenCollective](https://opencollective.com/panda3d).  Your
contributions help us accelerate the development of Panda3D.

For the list of backers, see the [BACKERS.md](BACKERS.md) file or visit the
[Sponsors page](https://www.panda3d.org/sponsors) on our web site.  Thank you
to everyone who has donated!

<a href="https://opencollective.com/panda3d" target="_blank">
  <img src="https://opencollective.com/panda3d/contribute/button@2x.png?color=blue" width=300 />
</a>
