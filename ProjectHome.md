The Archos 7 Home Tablet was released with the 1.5 Android OS (Cupcake). This project is dedicated to the effort of porting Android Froyo 2.2.x to the device.

## Current Building Instructions from Source ##

We have forked the modified Android OS projects into github. Therefore, instead follow directions on the wiki page for initializing the repo and getting the source.

Since all the changes have been merged into the github source repository. There is **NO** need to patch:

  * build/target/product/generic.mk
  * build/target/board/generic/BoardConfig.mk
  * external/wpa\_supplicant/Android.mk
  * frameworks/base/telephony/java/com/android/internal/telephony/gsm/GSMPhone.java

That's it. Build a release user build for better performance overall.


When copying files from the Archos original image... only copy these:
  * cp /bin/wlan\_loader bin;
  * cp /bin/busybox bin;
  * cp -r /etc/asound.conf etc;
  * cp -r /etc/vold.conf etc;
  * cp -r /etc/firmware etc;
  * cp -r /etc/wifi etc;
  * cp -r /lib/modules lib;
  * cp -r /lib/hw lib;
  * cp /etc/dhcpcd/dhcpcd.conf etc/dhcpcd;

Use init.rk28board.rc and default.prop from the Downloads section in your boot.img


## Github ##

`http://github.com/thaplague`

## For the Haters ##
http://www.youtube.com/watch?v=felupJ-NGcU