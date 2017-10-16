FROM registry.dev.meetup.com/library/phpldapadmin-1.0.1
COPY emerge_pkgs/* /usr/portage/distfiles/
RUN $(qlist -Iv www-servers/apache-2.2.16 | grep www-servers/apache-2.2.16) || emerge -v =www-servers/apache-2.2.16
RUN $(qlist -Iv dev-lang/php-5.2.14 | grep dev-lang/php-5.2.14) || emerge -v =dev-lang/php-5.2.14
RUN $(qlist -Iv virtual/httpd-php-5.2 | grep virtual/httpd-php-5.2) || emerge -v =virtual/httpd-php-5.2
RUN sed -i 's/^PS1.*$/PS1="(oldbugzilla-3.0.2) $PS1"/' /etc/bash/bashrc
COPY apache_conf/etc/apache2 /etc/apache2
RUN rm -f /etc/apache2/vhosts.d/00_default_ssl_vhost.conf
CMD /usr/sbin/apache2 -D USERDIR -D DEFAULT_VHOST -D INFO -D STATUS -D LANGUAGE -D DAV -D PHP5 -D PERL -D STATUS -D PROXY -d /usr/lib64/apache2 -f /etc/apache2/httpd.conf -k start
