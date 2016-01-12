This repo contains Wii U Internet Browser exploit(s) under PowerPC userland, for libstagefright vuln(s). This was designed for the Internet Browser, but this could be used with anything requesting MP4s over plaintext HTTP in theory(titles which use mvplayer.rpl), if one would update the payload heap addr/etc used in the source. This requires the following repo: https://github.com/yellows8/wiiuhaxx_common

This repo is based on a seperate repo, that repo is from November 2015.

If payload-loading would be implemented in wiiuhaxx_common itself at some point, then the payload-heap-addr mentioned here wouldn't be needed/matter anymore.

Supported system-versions for "browserhax_fright_tx3g_wiiu.php"(Internet Browser 5.5.1 fixed the vuln used by this):
* 5.3.2: This isn't fully supported since the payload-heap-addr is off.
* 5.4.0
* 5.5.0

To use this you must host the exploit script on a server, then you must setup wiiuhaxx_common as documented in that repo. If you're going to use libwiiu with your payload binary, then you must use a coreinit.h which actually supports your system-version. The max size of the final payload(loader included) is 0x4000-bytes, so your input payload max size is a bit less than 0x4000-bytes(the script will throw an error if the size is too large).

Note that issues occur when the final URL you use is too long, so you should keep it short like with the following: "http(s)://{server}/wiiuhaxx.php?sysver={version listed in wiiuhaxx_common}". This hasn't been debugged yet.

The only known time this exploit has ever failed pre-native-code-exec(on a supported system-version), was when the URL was too long as described above. However, this is mostly with testing with just one open tab(in particular with automatically loading the page).

# Credits:
* plutoo for getting exception-dumps / memdumps, etc, on 5.3.2.

