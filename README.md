This repo contains Wii U Internet Browser exploit(s) under PowerPC userland, for libstagefright vuln(s). This was designed for the Internet Browser, but this could be used with anything requesting MP4s over plaintext HTTP in theory(titles which use mvplayer.rpl), if one would update the payload heap addr/etc used in the source. This requires the following repo: https://github.com/yellows8/wiiuhaxx_common

This repo is based on a seperate repo, that repo is from November 2015.

If payload-loading would be implemented in wiiuhaxx_common itself at some point, then the payload-heap-addr mentioned here wouldn't be needed/matter anymore.

Supported system-versions for "browserhax_fright_tx3g_wiiu.php":
* 5.3.2: This isn't fully supported since the payload-heap-addr is off.
* 5.4.0
* 5.5.0
* 5.5.1: Originally this exploit was thought to be fixed via doing manual code-RE(hence why it was released when it was). However, that was actually wrong due to misreading that code: this exploit works fine as-is on 5.5.1(no testing on 5.5.1 was done before release, only code-RE).

To use this you must host the exploit script on a server, then you must setup wiiuhaxx_common as documented in that repo. If you're going to use libwiiu with your payload binary, then you must use a coreinit.h which actually supports your system-version. The max size of the final payload(loader included) is 0x4000-bytes, so your input payload max size is a bit less than 0x4000-bytes(the script will throw an error if the size is too large). Once all setup, just access an URL like the below one where "browserhax_fright_tx3g_wiiu.php" is hosted, with the browser.

Note that issues occur when the final URL you use is too long, so you should keep it short like with the following: "http(s)://{server}/wiiuhaxx.php?sysver={version listed in wiiuhaxx_common}". This hasn't been debugged yet.

The only known time this exploit has ever failed pre-native-code-exec(on a supported system-version), was when the URL was too long as described above. However, this is mostly with testing with just one open tab(in particular with automatically loading the page).

# Browser HTTP(S) URLs
As of 5.5.1 the only HTTP(S) URLs for code-binaries under Internet Browser "code/" are: internal-testing URLs, web-searching, "favorites" URLs, the Wii U version of the browser-filter also used for JPN-New3DS(https://3dbrew.org/wiki/Internet_Browser#New_3DS_Internet_Browser), etc.
That is, as of 5.5.1 there's no known Wii U equivalent to the following with 3DS: https://3dbrew.org/wiki/Internet_Browser#Forced_system-update 

# Credits:
* plutoo for getting exception-dumps / memdumps, etc, on 5.3.2.

