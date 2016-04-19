# sonar-runner-setup-ubuntu

Java JRE and a DBMS(postgresql,sql) must be already there

1) create a user called sonar

createuser –interactive
then role :sonar
give superuser privilages
2)Create Sonar database with the user sonar
CREATE DATABASE sonar
WITH OWNER = sonar
ENCODING = ‘UTF8′
TABLESPACE = pg_default
LC_COLLATE = ‘en_US.UTF-8′
LC_CTYPE = ‘en_US.UTF-8′
CONNECTION LIMIT = -1;
GRANT CONNECT, TEMPORARY ON DATABASE sonar TO public;
GRANT ALL ON DATABASE sonar TO sonar;
 
3)Download and unzip SonarQube distribution

wget http://dist.sonar.codehaus.org/sonarqube-5.1.zip
unzip sonarqube-5.1.zip
or click here then unzip the downloaded file
 
4)Then move sonarqube-5.3 in to /opt/sonar folder

mv sonarqube-5.1 /opt/sonar

5)open opt/sonar/conf/sonar.properties and edit the following lines as follows

sonar.jdbc.username=sonar
sonar.jdbc.password=sonar
sonar.jdbc.url=jdbc:postgresql://localhost/sonar
sonar.web.host=127.0.0.1
sonar.web.context=/sonar
sonar.web.port=9000
6)start the sonarQube

sudo /opt/sonar/bin/linux-x86-64/sonar.sh start
(the you can access sonar qube through the browser using http://localhost:9000/sonar)
