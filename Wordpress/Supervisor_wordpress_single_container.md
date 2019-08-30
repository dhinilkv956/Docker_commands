<p><strong>Using Supervisor to Run WordPress in a Single Container</strong></p>
<p><strong>Problem</strong><br />would like to run all services needed for your application in a single container. Specifically for running<br />WordPress, you would like to run MySQL and HTTPD at the same time in a con‐<br />tainer. Because Docker executes foreground processes, you need to figure out a way<br />to run multiple &ldquo;foreground&rdquo; processes simultaneously.</p>
<p><strong>Solution</strong></p>
<p>Use Supervisor to monitor and run both MySQL and HTTPD. Supervisor is not an<br />init system, but is meant to control multiple processes and is run like any other pro‐<br />gram.</p>
<p>&nbsp;</p>
[Dockerfile]
