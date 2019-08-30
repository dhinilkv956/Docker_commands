<ul>
<li><strong>To run busybox container</strong></li>
</ul>
<p>$ docker run busybox echo hello world</p>
<ul>
<li><strong>To see the running container</strong></li>
</ul>
<p>$ docker ps</p>
<ul>
<li><strong>To see the running and stopped container</strong></li>
</ul>
<p>$ docker ps -a</p>
<ul>
<li><strong>Run a container that executes /bin/bash</strong></li>
</ul>
<p>$ docker run -t -i ubuntu:14.04 /bin/bash</p>
<p>&nbsp;</p>
<ul>
<li><strong>Running a Docker Container in Detached Mode</strong></li>
</ul>
<p>run a simple HTTP server with Python in a python:2.7 and If you open your browser at the IP of your Docker host on port 1234</p>
<p>$ docker run -d -p 1234:1234 python:2.7 python -m SimpleHTTPServer 1234</p>
<p>&nbsp;</p>
<ul>
<li><strong>connect to the container by using the exec command and running a bash shell:</strong></li>
</ul>
<p>$ docker exec -ti 9d7cebd75dcf /bin/bash<br />root@9d7cebd75dcf:/# ps -ef | grep python<br />root 1 0 0 15:42 ?&nbsp; 00:00:00 python -m SimpleHTTPServer 1234</p>
<p>&nbsp;</p>
<ul>
<li><strong>Creating, Starting, Stopping, and Removing Containers</strong></li>
</ul>
<p>$ docker create -P --expose=1234 python:2.7 python -m SimpleHTTPServer 1234</p>
<p>$ docker ps</p>
<p>CONTAINER ID IMAGE COMMAND ... NAMES<br />a842945e2414 python:2.7 "python -m SimpleHTT ...fervent_hodgkin</p>
<p>$ docker start a842945e2414</p>
<p>$ docker restart a842945e2414</p>
<p>$ docker kill a842945e2414</p>
<p>$ docker rm a842945e2414</p>
