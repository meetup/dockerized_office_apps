# dockerized_office_apps

## to restart mediawiki (https://wiki.muphq.com/)
```
ssh to ds2.dev.meetup.com
Note we are bind-mounting the volume (mediawiki-1.10.0_src) so as to have static data persist on the docker host. 
docker run --name mediawiki -itd -p 192.168.0.15:8080:8080 -v /usr/local/docker_apps/mediawiki/mediawiki-1.10.0_src:/var/www/localhost/htdocs registry.dev.meetup.com/library/mediawiki-1.10.0 && docker exec mediawiki /usr/sbin/apache2 -D USERDIR -D DEFAULT_VHOST -D INFO -D STATUS -D LANGUAGE -D DAV -D PHP5 -D PERL -D STATUS -D PROXY -d /usr/lib64/apache2 -f /etc/apache2/httpd.conf -k start

```