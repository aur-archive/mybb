# Maintainer: Stefan Tatschner <stefan@sevenbyte.org>
# Contributor: bslackr <brendan at vastactive dot com>
# Contributor: Piotr Rogoza <rogoza dot piotr at gmail dot com>

pkgname=mybb
pkgver=1.6.14
pkgrel=1
pkgdesc="MyBB is a professional and efficient discussion board"
backup=('etc/webapps/mybb/config.php'
        'etc/webapps/mybb/.htaccess')
install=mybb.install
arch=('any')
url=('http://mybb.com')
license=('GPL')
depends=('php')
optdepends=('apache:      Webserver to deploy mybb'
            'nginx:       Webserver to deploy mybb'
            'mysql:       Databaserver to deploy mybb'
            'postgresql:  Databaserver to deploy mybb'
            'sqlite:      Database-Library to deploy mybb')
# http://stackoverflow.com/a/4332399/2587286
source=("https://github.com/mybb/mybb/archive/${pkgname}_${pkgver//./}.tar.gz")
md5sums=('3d3861fb3090d9a69b909037c247704c')

package() {
  mkdir -p ${pkgdir}/usr/share/webapps
  mkdir -p ${pkgdir}/etc/webapps/mybb
  mkdir -p ${pkgdir}/var/lib/mybb
  mkdir -p ${pkgdir}/var/lib/mybb/admin

  cd ${pkgdir}/usr/share/webapps
  cp -ra ${srcdir}/${pkgname}-${pkgname}_${pkgver//./} mybb
  cd mybb

  mv cache ${pkgdir}/var/lib/mybb/cache
  mv uploads ${pkgdir}/var/lib/mybb/uploads
  mv admin/backups ${pkgdir}/var/lib/mybb/admin/backups
  mv inc/languages ${pkgdir}/var/lib/mybb/languages
  cp inc/config.default.php ${pkgdir}/etc/webapps/mybb/config.php
  cp htaccess.txt ${pkgdir}/etc/webapps/mybb/.htaccess

  rm inc/settings.php

  ln -s /var/lib/mybb/settings.php inc/settings.php
  ln -s /var/lib/mybb/languages inc/languages
  ln -s /var/lib/mybb/cache cache
  ln -s /var/lib/mybb/uploads uploads
  ln -s /var/lib/mybb/admin/backups admin/backups
  ln -s /etc/webapps/mybb/config.php inc/config.php
  ln -s /etc/webapps/mybb/.htaccess .htaccess
}
