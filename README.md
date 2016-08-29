wireshark-wa
============

Whatsapp dissector plugin for wireshark

***Important*** I'm no longer working on this repo. This plugin works for protocol version 1.6 or older (check out the tags), with whatsapp protocol 2.0 it is probably necessary to perform MITM in order for a machine to capture the protocol data (since it uses an ephemeral shared secret calculated in a DH way) so this plugin becomes essentially useless. Still it is perfect as a base to implement 2.0 protocol.

Get a copy
----------

Ubuntu users may install the plugin using launchpad repo: https://launchpad.net/~wireshark-whatsapp/+archive/ppa

Windows users may find releases at: https://www.gosell.it/product/whatsapp-dissector-for-wireshark-26

Build and install
-----------------

1. Create a build directory and move to it, for example "mkdir build; cd build"
2. Generate Makefile "cmake .."
3. Now build the plugin "make"
4. And the plugin should be built as "whatsapp.so", just copy it to the plugins folder "cp whatsapp.so ~/.wireshark/plugins/"
 
You need the wireshark headers, the glib-2.0 headers, the libcrypto headers (install openssl headers) and of course the gcc C/C++ compiler.

For Windows build:

1. Create a build directory and move to it, for example "mkdir build; cd build"
2. Tweak mingw32-windows.toolchain according to your needs.
3. Generate Makefile "cmake -DCMAKE_TOOLCHAIN_FILE=../mingw32-windows.toolchain .." (set WIRESHARK_INCLUDE_DIRS, GCRYPT_INCLUDE_DIR variables if needed)
4. Now build the plugin "make"
5. And the plugin should be built as "whatsapp.dll", just copy it to the plugins folder "C:\Program Files\Wireshark\Plugins\'version'\whatsapp.dll"

You will probably need libglib-2.0, libwireshark and libgcrypt to properly link the DLL.

Windows builds are currently under test, report any bugs you find please.


Usage
-----

Using the plugin it's easy. You can use it to filter whatsapp packets (although it does not work as well as I'd like) and to dissect the data of the packet.
For decryption support goto to protocol preferences, enable the data decoding and fill some decryption keys (the passwords for the accounts you are sniffing).


