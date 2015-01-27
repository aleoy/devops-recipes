sudo nano /etc/mysql/my.cnf

[mysqld]
character-set-server=utf8
collation-server = utf8_unicode_ci
init-connect='SET NAMES utf8'
init_connect='SET collation_connection = utf8_unicode_ci'
skip-character-set-client-handshake


mysql> show variables WHERE variable_name like "col%";
+----------------------+-----------------+
| Variable_name        | Value           |
+----------------------+-----------------+
| collation_connection | utf8_unicode_ci |
| collation_database   | utf8_unicode_ci |
| collation_server     | utf8_unicode_ci |
+----------------------+-----------------+

[source](https://rtcamp.com/tutorials/mysql/character-sets-collations/)
