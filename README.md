# InstallTheGroove
A custom installation of Fedora 21 geared towards arcade cabinets running Stepmania and its derivatives.

### What's in here?
- a simple kickstart file. It is VERY bare-bones, and is what i use for the pre-built ISO.

- spec files for the source tarball of stepmania 5.0, and simply love. dguzek ported the theme.

### How do I use this?

Download a pre-built iso here: `http://teknolust.org/static/InstallTheGroove.iso`. No network connection is required. It will automatically install the base operating system, OpenITG, and Stepmania 5.

# The install disc will automatically format your hard drive. This is by design. You have been warned.

### OK I have it installed, now what?

The system auto-logins to a fluxbox session.
The username is *itg* and the password is *changeme*

Right-click anywhere on the desktop to bring up the menu. *Lilyterm* is the terminal emulator, and *Leafpad* is a text editor. You can also launch OpenITG and Stepmania 5 directly from here. Firefox is included.

#### How do I install the PIU driver?
Open a `lilyterm` session and punch in the following:

```
cd utils
sudo piu.sh
```

it will ask for your password, which if not changed from the default, is `changeme`

#### How do I change the password?

I'm glad you asked! Just enter `passwd` on the command prompt and follow the instructions.

### How do I install just the games on my own Fedora 21 install?
stepmania5 can be installed with a single command:

`sudo yum -y install http://teknolust.org/static/stepmania-5.0.6-1.fc21.x86_64.rpm`

You'll need the `libmad` libraries, which can be obtained via the rpmfusion repos.

And since nobody wants to play on an arcade cabinet without (sighs heavily) Simply Love, I packaged that into an RPM also:

`sudo yum -y install http://teknolust.org/static/stepmania-simplylove-20150201-1.fc21.x86_64.rpm`

Linux philosophy is for packages to leave existing settings in place, so you'll have to pick the theme in-game after installing. This only needs to be done once.

Stepmania is installed in `/opt/stepmania-5.0`

OpenITG is available, although it is probably very buggy. Because of limitations of the RPM format, it's impossible to define a list of dependencies in a spec file for a different arch than your current environment. As such, you'll have to install a bunch of stuff beforehand before attempting to run OpenITG.

```
sudo yum -y install glibc.i686 libX11.i686 libXtst.i686 mesa-libGL.i686 mesa-libGLU.i686 libpng12.i686 libjpeg-turbo.i686 libusb.i686 libXrandr.i686 mesa-dri-drivers.i686 libvorbis.i686 libogg.i686 alsa-lib.i686
sudo yum -y install http://download1.rpmfusion.org/free/fedora/releases/21/Everything/i386/os/libmad-0.15.1b-17.fc21.i686.rpm
sudo yum -y install http://teknolust.org/static/openitg-b2-1.fc21.x86_64.rpm
````

Please be aware this is just a 32-bit build of OpenITG running cleanly on a 64-bit box. The game still runs into the 4GB memory limit.

The game is installed in `/opt/openitg` and will for some reason create a `C:` directory and a massive collection of Windows-based subdirectories in whatever directory you run the game out of.
