# dnspanel-bind-backend


This is Linux back-end example written in PHP for web based panel: https://github.com/mrfx/dnspanel-bind-frontend<br>
It uses dig, host & /usr/sbin/named-checkzone commands for domain configuration checks and trace.<br>
<br>
/html/srv/ part is responsible for database (MySQL/MariaDB) operations and verify domains configurations and must be placed at the same domain/virtualhost of web server as front-end files.<br>
<br>
/root/skrypty/dns/ part manipulate BIND configuration files and should run as privileged user by CRON daemon.<br><br>
Example:<br><br>
*/5 * * * *     root    php -f /root/skrypty/cron-dns-reload.php &> /dev/null<br><br>
will generate named.conf and zones configuration files and reload dns server. Also there are at the bottom of /root/skrypty/dns/create-bind-files-from-db.php few commands for copy dns configuration files to other directories for export to other dns servers. You should delete/modify these lines to fit your needs.
<br><br>
/root/skrypty/dns/import-domains.php is a tool for import your old  DNS configuration from files at /etc/bind/ to the database. You can run it manually from command line.
