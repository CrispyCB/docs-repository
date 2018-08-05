# Installing HexChat IRC on Ubuntu Linux 16.04

_Note: This guide assumes that you know what Ubuntu Linux and HexChat IRC are. If you don’t, check out the Ubuntu Overview from Tutorialspoint and the Wikipedia article on IRC._

## Why HexChat?

HexChat is an Internet relay chat (IRC) client. HexChat offers a number of features that other IRC clients may not, including:
* Scripting with Perl, Python and Lua
* Multi-network with auto-connect, join, and identify commands
* Use with Twitch.tv and Tor

## What do I need to install HexChat?

In order to install HexChat, you'll need the following:

* A laptop or desktop running Ubuntu 16.04 LTS
* An open web browser (Ubuntu comes bundled native with Firefox)

## Installing HexChat

To begin installing HexChat, navigate to https://hexchat.github.io/downloads.html. This will allow you to download HexChat for Windows, OS X and Linux. 

### Method 1: Installing a Snap via Snapcraft

Since we’re installing for Ubuntu Linux, click the Snapcraft link in the center.

This will open the Snapcraft page for the HexChat Snap file. Snap files are universal packages for Linux – kind of like .exe files for Windows.

Once the Snapcraft page opens, you have two options. You can either install HexChat through the Desktop Store or via the package manager. We'll cover both methods below.

#### 1.1: Installing via the Desktop Store

To install via the Ubuntu Desktop Store:

First, click the 'View in Desktop Store' button.

The 'Launch Application' window will appear.

Click 'Open link'.

The Ubuntu Software page for HexChat will open.

Click 'Install'.

If you have a password enabled on your machine, enter it now.

The application will install.

You will then be presented with two options: 'Remove' and 'Launch'. Click 'Launch' to open HexChat.

For information on how to configure HexChat, see the [documentation](https://hexchat.readthedocs.io/en/latest/appearance.html).

#### 1.2: Installing via the package manager

To install via the package manager:

Open your terminal window.

Type the following command:

    sudo snap install hexchat

HexChat will install.

Run HexChat from the terminal using the 'hexchat' command.

For information on how to configure HexChat, see the [documentation](https://hexchat.readthedocs.io/en/latest/appearance.html).

If the Snapcraft link does not work or errors out, click the Source Archive link to the right of the Snapcraft link and proceed to Method 2.

### Method 2: Compiling HexChat from the Source Archive

In order to compile HexChat from the source, you'll need a few things first:

* Git
* The build dependencies for HexChat

Using your terminal, install Git:

    sudo apt-install git-all

Once Git is installed, clone the HexChat source code onto your machine.

    git clone https://github.com/hexchat/hexchat.git

With the source code cloned onto your machine, it's time to get the build dependencies, after which we'll compile HexChat.

To install all of the build dependencies for HexChat:

    sudo apt-install meson libcanberra-dev libdbus-glib-1-dev libglib2.0-dev libgtk2.0-dev libluajit-5.1-dev libnotify-dev libpci-dev libperl-dev libproxy-dev libssl-dev python3-dev

With build dependencies installed, there's one more item we need to install before we can continue -- pip3, the Python 3 package manager.

To install pip3:

    sudo apt-get install python3-pip

Installing pip3 allows us to update the meson install above.

With both pip3 and meson installed, upgrade meson:

    pip3 install --upgrade meson

This will upgrade the meson build manager to the newest current version.

Now that everything is installed and upgraded, it's time to compile HexChat from source.

First, change directories into your hexchat directory using the 'cd' command:

    cd hexchat

Once inside your hexchat directory, make a build directory for the build files to live in. I named mine 'hexchat-build' and created it using the mkdir command:

    mkdir hexchat-build

With your build directory created, run the meson build command.

    meson build

Meson will run. You can then run the second build manager, Ninja, using the following commands:

    ninja -C build
    sudo ninja -C build install

The first command switches to your build directory, created in the previous step. The second installs the items created by the meson build (residing in your build directory) onto your machine.

This will install HexChat, which can be run from the terminal using the command 'hexchat'.

For information on how to configure HexChat, see the [documentation](https://hexchat.readthedocs.io/en/latest/appearance.html).
