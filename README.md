# Backup Mariadb
Bash script to backup MariaDB to a USB Drive, using mariabackup and also changed database files

Backing up is always a matter of personal taste and circumstances.
I found it impossible to find a way of detecting any changes to my Maria databases using MariaDB itself.
Things like CHECKSUM and Update didn't work for me.
So I iterate all *.ibd files and do a mysqldump if the date/time has changed.
I chose *.ibd as its possible to restore from just a single ibd file
If the mysql database has a changed ibd file, then I run mariabackup to a streamed gzip file
to capture the whole MariaDB instance.
I also keep track of the changed files in a flag directory /var/lib/mysql-bak on the server.
This allows me to run hourly without backing up if no files have changed.

Feb 2020


References:
Thanks to a lot of examples found via goole searchs, and this one in particular
https://github.com/omegazeng/run-mariabackup

