# magento-docker
## add virtual host  
```
sudo nano /etc/hosts
```
insert string
```
127.0.0.1    docker.webmeridian.local
```
to save press 
```
Ctrl+o
```
then press enter and
```
Ctrl+x
```
to exit
## Setup magento
###### Copy magento files into magento folder. 
###### Replace db config in env.php if have already set up magento project with
```
'db' => [
        'table_prefix' => '',
        'connection' => [
            'default' => [
                'host' => 'wm_mysql',
                'dbname' => 'webmeridian',
                'username' => 'admin',
                'password' => '1234',
                'active' => '1'
            ]
        ]
    ],
```
copy your app(project) in folder "magento"

install Docker and Docker-compose for your computer
```
https://docs.docker.com/install/linux/docker-ce/ubuntu/
```
run command in console core this folder 
```
docker-compose build
```
run command in console core this folder
 ```
docker-compose up -d
 ```
 