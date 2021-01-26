pkgname=arm-linux-gnueabihf-armv6-gcc
pkgver=1.0
pkgrel=1
arch=('any')
depends=('arm-linux-gnueabihf-gcc')

# source=(arm-linux-gnueabihf-armv6-gcc)
# md5sums=('34b8f468480f4b2b9fd758ae4c3ae71d')

orig_prefix=arm-linux-gnueabihf-
prefix=arm-linux-gnueabihf-armv6-
gen_progs=(gcc g++)
orig_progs=(ar)

gen_script() {
	echo '#!/bin/bash' > $srcdir/$prefix$1
	echo '/usr/bin/'$orig_prefix$1 '-march=armv6 $@' >> $srcdir/$prefix$1
}

gen_orig_script() {
	echo '#!/bin/bash' > $srcdir/$prefix$1
	echo '/usr/bin/'$orig_prefix$1 '$@' >> $srcdir/$prefix$1
}

prepare() {
	for prog in "${gen_progs[@]}"
	do
		gen_script $prog
	done

	for prog in "${orig_progs[@]}"
	do
		gen_orig_script $prog
	done
}

package() {
	for prog in "${gen_progs[@]}"
	do
		install -Dm755 $prefix$prog "$pkgdir/usr/bin/"$prefix$prog
	done

	for prog in "${orig_progs[@]}"
	do
		install -Dm755 $prefix$prog "$pkgdir/usr/bin/"$prefix$prog
	done
}
