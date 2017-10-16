FROM registry.dev.meetup.com/library/mediawiki-1.10.0
COPY emerge_pkgs/* /usr/portage/distfiles/
RUN $(qlist -Iv www-servers/apache-2.2.16 | grep www-servers/apache-2.2.16) || emerge -v =www-servers/apache-2.2.16
RUN $(qlist -Iv dev-lang/php-5.2.14 | grep dev-lang/php-5.2.14) || emerge -v =dev-lang/php-5.2.14
RUN $(qlist -Iv virtual/httpd-php-5.2 | grep virtual/httpd-php-5.2) || emerge -v =virtual/httpd-php-5.2
RUN $(qlist -Iv media-gfx/imagemagick-6.6.5.6 | grep media-gfx/imagemagick-6.6.5.6) || emerge -v =media-gfx/imagemagick-6.6.5.6
RUN $(qlist -Iv dev-python/python-ldap-2.3.9 | grep dev-python/python-ldap-2.3.9) || emerge -v =dev-python/python-ldap-2.3.9
RUN sed -i 's/^PS1.*$/PS1="(mediawiki-1.10.0) $PS1"/' /etc/bash/bashrc
COPY apache_conf/etc/apache2 /etc/apache2
RUN rm -f /etc/apache2/vhosts.d/00_default_ssl_vhost.conf

