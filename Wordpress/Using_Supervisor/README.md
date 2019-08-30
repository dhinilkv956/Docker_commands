<p><strong>Problem</strong></p>
<p>would like to run all services needed for your application in a single container. Specifically for running WordPress, you would like to run MySQL and HTTPD at the same time in a container. Because Docker executes foreground processes, you need to figure out a way to run multiple &ldquo;foreground&rdquo; processes simultaneously.</p>
<p><strong>Solution</strong></p>
<p>Use Supervisor to monitor and run both MySQL and HTTPD. Supervisor is not an<br />init system, but is meant to control multiple processes and is run like any other pro‐<br />gram.</p>

[Dockerfile](https://github.com/dhinilkv956/Docker_commands/blob/master/Wordpress/Using_Supervisor/Dockerfile)

<p>To run WordPress, you will need to install MySQL, Apache 2 (i.e., httpd ), and PHP, and grab the latest WordPress release. You will need to create a database for Word‐Press. In the configuration file used in this recipe, the WordPress database user is root , its password is root , and the database is wordpress . Change these settings to your liking in the wp-config.php file and edit the Dockerfile accordingly.</p>

<p>Supervisor is configured via the supervisord.conf file like so:</p>

[Supervisordconf](https://github.com/dhinilkv956/Docker_commands/blob/master/Wordpress/Using_Supervisor/supervisord.conf)

<p>Two programs are defined to be run and monitored: mysqld and httpd . Each program can use various options like autorestart and autostart . The most important directive is command , which defines how to run each program. With this configuration, a Docker container needs to run only a single foreground process: supervisord .Hence the line in the Dockerfile, CMD <strong>["/usr/bin/supervisord"] .</strong></p>
