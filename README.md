# cod-magento-docker
## add virtual host  
```
sudo nano /etc/hosts
```
insert string
```
127.0.0.1    docker.customentities.com
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
                'host' => 'customentities_mysql',
                'dbname' => 'customentities',
                'username' => 'admin',
                'password' => '1234',
                'active' => '1'
            ]
        ]
    ],
```
