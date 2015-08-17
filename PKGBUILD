pkgname=pyalienfx-m14
realname=pyAlienFX
pkgver=v1.0.2
pkgrel=3
pkgdesc="Multiplataform software to control Alienware LED's written in Python2 with a patch to support m14 R3 (2013) model"
provides=('pyalienfx')
conflicts=('pyalienfx')
arch=('any')
url="http://code.google.com/p/pyalienfx/"
license="GPLv3"
depends=(python2 pygtk gksu)
 
source=("http://pyalienfx.googlecode.com/files/$realname-$pkgver.tar.gz" "libusb-1.0.so.0" "m14R3.patch")
md5sums=('33b2abb3ad56ec5618a1f68698c49a43' '05e36bd689b406367ce32263d3fc624b' 'fad5637dc20e461fa7110bd54087415b')
 
package() {
 #Create Necesary directories
 mkdir -p $pkgdir/opt
 mkdir -p $pkgdir/usr
 mkdir -p $pkgdir/usr/bin

 # Copy necesary files

 cd ${srcdir}/pyalienfx
 cp ${srcdir}/m14R3.patch ${srcdir}/pyalienfx
 git apply m14R3.patch #Patch for Alienware m14 (2013)
 rm -rf .git #Clean up git directory
 cd ${srcdir}
 cp pyalienfx -R $pkgdir/opt/pyAlienFX
 cp libusb-1.0.so.0 $pkgdir/opt/pyAlienFX/
 
 # Generate the bin command
 cd ${pkgdir}/usr/bin
 echo -ne "#!/bin/bash\ncd /opt/pyAlienFX\ngksu LD_PRELOAD=/opt/pyAlienFX/libusb-1.0.so.0 python2 /opt/pyAlienFX/pyAlienFX.py" > pyalienfx
 chmod a+x pyalienfx
}
