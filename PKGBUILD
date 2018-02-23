# GRU Mali GL Driver (Based on ODROID-C2 Mali GL PKGBUILD)
# Maintainer: Apokalypz <(my screen name)@gmail.com>
# Contributor: Kevin Mihelich <kevin@archlinuxarm.org>

buildarch=8

pkgbase=gru-libgl
pkgname=("${pkgbase}") #"${pkgbase}-headers")
pkgver=r14p0
pkgrel=1
_commit=12daf22c405a4f8faf6cbc4d2e88b85b36dc61d9
arch=('aarch64')
license=('Proprietary')
depends=('mesa-libgl')
makedepends=('git')
source=("git+https://github.com/rockchip-linux/libmali.git#commit=${_commit}"
	'mali-gru.conf'
	'99-mali.rules')
md5sums=('SKIP'
	 'SKIP'
	 'SKIP')

package_gru-libgl() {
  pkgdesc="LibGL for the Mali T860 in the RK3399 SoC in gru." 
  conflicts=('gru-libgl')
  provides=('gru-libgl')

  install -d "${pkgdir}"/usr/lib/maligl
  install -d "${pkgdir}"/etc/ld.so.conf.d
  install -d "${pkgdir}"/etc/OpenCL/vendors
  install -d "${pkgdir}"/etc/udev/rules.d

  cp libmali/include/mali.icd "${pkgdir}"/etc/OpenCL/vendors
  cp libmali/lib/aarch64-linux-gnu/libmali-midgard-t86x-r14p0.so \
	"${pkgdir}"/usr/lib/maligl/libMali.so
  cp "${srcdir}"/mali-gru.conf "${pkgdir}"/etc/ld.so.conf.d
  cp "${srcdir}"/99-mali.rules "${pkgdir}"/etc/udev/rules.d
  cd "${pkgdir}"/usr/lib/maligl/

  ln -sf libMali.so libEGL.so
  ln -sf libMali.so libEGL.so.1
  ln -sf libMali.so libEGL.so.1.0.0
  ln -sf libMali.so libGLESv2.so
  ln -sf libMali.so libGLESv2.so.2
  ln -sf libMali.so libGLESv2.so.2.0.0
  ln -sf libMali.so libgbm.so
  ln -sf libMali.so libgbm.so.1
  ln -sf libMali.so libgbm.so.1.0.0
  ln -sf libMali.so libmali.so
  ln -sf libMali.so libMaliOpenCL.so
  ln -sf libMali.so libOpenCL.so
}

#ToDo: Find a way to copy the header files without killing the ones 
#that mesa already put there.
#package_gru-libgl-headers() {
#  pkgdesc="LibGL headers for the Mali T860 in the RK3399 SoC in gru."
#  install -d "${pkgdir}"/usr/include
#  cp -a libmali/include/* "${pkgdir}"/usr/include
#}
