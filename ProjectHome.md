**Tired of trying to find online versions of OpenSSL, libEtPan, zlib, libssh2 or cURL ready to use in your iOS project, or even a working method to build them? Then this project is for you!**

This project provides a single-step [build-script](http://code.google.com/p/ios-static-libraries/source/browse/build-all.sh) as well as ready to use [binaries](http://code.google.com/p/ios-static-libraries/downloads/list) for iOS devices and simulator of the following libraries:
  * [OpenSSL](http://www.openssl.org/)
  * [Cyrus SASL](http://asg.web.cmu.edu/sasl/sasl-library.html)
  * [libEtPan](http://libetpan.sourceforge.net/)
  * [zlib](http://www.zlib.net/)
  * [libssh2](http://www.libssh2.org/)
  * [cURL](http://curl.haxx.se/)

How to build everything yourself:
  1. Clone the repository and cd into it
  1. Run build-all.sh {iOS\_SDK\_Version}

How to use the binaries directly:
  1. [Download](http://code.google.com/p/ios-static-libraries/downloads/list) the binaries corresponding to your target iOS SDK
  1. Configure the Xcode project build settings to point to the headers and libraries, as such (assuming the iOS 4.2 SDK in this example):
```
HEADER_SEARCH_PATHS[sdk=iphoneos4.2][arch=*] = ${SRCROOT}/../iPhoneOS-4.2/include
HEADER_SEARCH_PATHS[sdk=iphonesimulator4.2][arch=*] = ${SRCROOT}/../iPhoneSimulator-4.2/include
LIBRARY_SEARCH_PATHS[sdk=iphoneos4.2][arch=*] = ${SRCROOT}/../iPhoneOS-4.2/lib
LIBRARY_SEARCH_PATHS[sdk=iphonesimulator4.2][arch=*] = ${SRCROOT}/../iPhoneSimulator-4.2/lib
OTHER_LDFLAGS = -Wl,-search_paths_first -lz -lcrypto -liconv -lssl -lsasl2 -letpan -lgcrypt -lgpg-error -lssh2 -lcurl
```
> With iOS 4.3 SDK and later, you will need to use the armv7 version of the libraries when building your application for armv7 or Xcode will fail linking:
```
HEADER_SEARCH_PATHS[sdk=iphoneos4.3][arch=armv7] = ${SRCROOT}/../iPhoneOS-V7-4.3/include
HEADER_SEARCH_PATHS[sdk=iphoneos4.3][arch=armv6] = ${SRCROOT}/../iPhoneOS-V6-4.3/include
HEADER_SEARCH_PATHS[sdk=iphonesimulator4.3][arch=*] = ${SRCROOT}/../iPhoneSimulator-4.3/include
LIBRARY_SEARCH_PATHS[sdk=iphoneos4.3][arch=armv7] = ${SRCROOT}/../iPhoneOS-V7-4.3/lib
LIBRARY_SEARCH_PATHS[sdk=iphoneos4.3][arch=armv6] = ${SRCROOT}/../iPhoneOS-V6-4.3/lib
LIBRARY_SEARCH_PATHS[sdk=iphonesimulator4.3][arch=*] = ${SRCROOT}/../iPhoneSimulator-4.3/lib
OTHER_LDFLAGS = -Wl,-search_paths_first -lz -lcrypto -liconv -lssl -lsasl2 -letpan -lgcrypt -lgpg-error -lssh2 -lcurl
```

Notes:
  * All libraries are built "release"
  * The pre-iOS 4.3 version of the libraries use the armv6 architecture (compatible with all iPhones and iPads)
  * The iOS 4.3 and later version of the libraries use the armv6 or armv7 architectures for increased compatibility with all iOS devices
  * The libEtPan and cURL libraries are built without IPv6 support

Thanks to:
  * [Remail-iPhone](http://code.google.com/p/remail-iphone/) for providing some build scripts to learn from
  * [The Rare Air](http://www.therareair.com/2009/01/01/tutorial-how-to-compile-openssl-for-the-iphone/) for providing an OpenSSL for iPhone tutorial
  * [olipion](http://sites.google.com/site/olipion/cross-compilation/libssh2) for sharing build instructions for libssh2

_Contributors welcomed: send email to project owner to participate!_