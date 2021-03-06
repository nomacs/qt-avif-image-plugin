QT imageformats plug-in for AV1 Image File Format (AVIF)

This is a plug-in for QT based applications to enable them to open/save images in AVIF format.

Format support:
AVIF (AV1 Image File Format - image/avif): read/write support
AVIFS (AVIF image sequence - image/avif-sequence): ready only

Software requirements:
yasm – needed to build optimized libaom
cmake – needed to build libaom and libavif
qmake (or qt5-qmake) – to build the QT plugin
QT5 development packages (for example qtbase5-dev on Ubuntu)
qt5-image-formats-plugins (or qt5-imageformats, dev-qt/qtimageformats, …)
The plug-in use libavif library internally ( https://github.com/AOMediaCodec/libavif ).

How to build the plug-in (two possibilities):

1) Dynamic linking with libavif (ONLY for systems with >=libavif 0.6.0 installed!!!)
Run:
./build_libqavif_dynamic.sh

2) Static linking (should work everywhere but resulting plug-in with be larger)
Run:
./build_libqavif_static.sh
The static version takes longer time to build because libaom and libavif libraries will be compiled locally.

The result of building process is libqavif.so

How to install:
Copy libqavif.so into the folder where other plug-ins from qt5-image-formats-plugins are installed. It could be one of the following locations:
Gentoo: /usr/lib/qt5/plugins/imageformats
Archlinux: /usr/lib/qt/plugins/imageformats/
Ubuntu: /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats

Further recommend steps:
If you don’t have "image/avif" and "image/avif-sequence" mime types installed, copy avifs.xml, avif.xml to:
/usr/share/mime/packages
And run:
update-mime-database /usr/share/mime

AVIF Thumbnails in KDE’s dolphin
Copy avif.desktop, avifs.desktop to:
/usr/share/kservices5/qimageioplugins/

Update imagethumbnail.desktop (in /usr/share/kservices5/ ):
Add ;image/avif;image/avif-sequence to the MimeType= list.

How to test:
Associate image/avif (*.avif) with gwenview and it should be able to display test images:
https://github.com/AOMediaCodec/av1-avif/tree/master/testFiles
