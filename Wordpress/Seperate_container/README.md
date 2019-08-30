<p><strong>Running a WordPress Blog Using Two Linked Containers</strong></p>
<p><strong>Problem</strong></p>
<p>run a WordPress site with containers, but you do not want to run the MySQL database in the same container as WordPress. You want to keep the concept of separation of concerns in mind and decouple the various components of an application as much as possible.</p>
<p><strong>Solution</strong></p>
<p>You start two containers: one running WordPress using the official image from the Docker Hub, and one running the MySQL database. The two containers are linked using the --link option of the Docker CLI</p>
<p>Start by pulling the latest images for WordPress and MySQL:</p>
<p>pulling the latest images for WordPress and MySQL:<br /><strong>$ docker pull wordpress:latest</strong><br /><strong>$ docker pull mysql:latest</strong></p>
<p>Start a MySQL container, give it a name via the --name CLI option, and set the MYSQL_ROOT_PASSWORD via an environment variable:</p>
<p><strong>$ docker run --name mysqlwp -e MYSQL_ROOT_PASSWORD=wordpressdocker -d mysql</strong></p>
<p>You can now run a WordPress container based on the wordpress:latest image. It will be linked to the MySQL container using the --link option, which means that Docker will automatically set up the networking so that the ports exposed by the MySQL container are reachable inside the WordPress container:</p>
<p><strong>$ docker run --name wordpress --link mysqlwp:mysql -p 80:80 -d wordpress</strong></p>
<p>Both containers should be running in the background, with port 80 of the WordPress<br />container mapped to port 80 of the host:</p>
