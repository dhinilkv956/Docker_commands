<p><strong>Problem</strong><br />You have data on your host that you would like to make available in a container.</p>
<p><strong>Solution</strong></p>
<p>Use the -v option of docker run to mount a host volume into a container.<br />For example, to share the working directory of your host within a /cookbook directory in a container, do this:</p>
<p><strong>$ ls</strong><br /><strong>data</strong><br /><strong>$ docker run -ti -v "$PWD":/cookbook ubuntu:14.04 /bin/bash</strong><br /><strong>root@11769701f6f7:/# ls /cookbook</strong><br /><strong>data</strong></p>
<p>&nbsp;</p>
By default, Docker mounts the volume in read-write mode. If you want to mount it in read-only mode, you can specify it after the name of the volume, using a colon. For example, to mount the previous working directory to /cookbook as read-only, you would use -v "$PWD":/cookbook:ro

<p>You can inspect your mount mapping with the docker inspect command.</p>
<p>$ docker inspect -f {{.Mounts}} 44d71a605b5b<br />[{ /Users/sebastiengoasguen/Desktop /cookbook true}]</p>
