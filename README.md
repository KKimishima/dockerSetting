# dockerSetting

## redmine
- redmine-mysql
docker run --name=mysql-redmine -d --env='DB_NAME=redmine_production' --env='DB_USER=redmine' --env='DB_PASS=redpass' -v `pwd`:/var/lib/mysql sameersbn/mysql:latest

- redmineData
docker run --name=redmine -p 80:80 --link=mysql-redmine:mysql -v `pwd`/:/home/redmine/data sameersbn/redmine:3.3.1

## gitbukect
docker run -d -p 8080:8080 -p 29418:29418  -v `pwd`/gitbucket:/gitbucket takezoe/gitbucket

## knowledge
docker run -d -p 8000:8080 -v `pwd`/:/root/.knowledge --name knowledge koda/docker-knowledge

## jenkins
sudo chown -R 1000 volume_dir

sudo docker run --name jenkins -d -v `pwd`/:/var/jenkins_home -p 8001:8080 -e JAVA_OPTS='-Duser.timezone=Asia/Tokyo -Dfile.encoding=UTF-8 -Dsun.jnu.encoding=UTF-8' jenkins
