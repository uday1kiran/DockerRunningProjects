db creation testdb, is strucking in the background as it will prompt another console and which won't get exited even after command completeion.
RUN cd C:\\SQLLIB\\BIN;Start-Process db2cmdadmin.exe -ArgumentList 'db2setcp db2 create database testdb' -Wait;cd C:\\

So, created a container from mcr.microsoft.com/windows/servercore:ltsc2019 and by attaching the volume of the setup files.
docker run  --volume=image:C:\image -it mcr.microsoft.com/windows/servercore:ltsc2019


And, after installation using below command, create db as in above command and kill it after sometime by checking the process list from another window using docker exec.
RUN Start-Process C:\\image\\setup.exe -ArgumentList '/f /u C:\\image\\PROD_SERVER.rsp /m /l install.log' -Wait


docker commit container_id new_image
ex: docker commit ac9 tempdb

Then, using that image create another DB with remaining part of docker file(dockerfile_2ndpart).

---
rsp files is created using the 3rd option during installation.


