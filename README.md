# SET Fusion Pre-requisites
## Configure the required Databases
SET Fusion requires MySQL and MongoDB databases to be installed prior to starting the SET Fusion installation.  
### MySQL
1. Login to MySQL as root user  
```mysql -uroot -p<root password>```

2. Create setfusion user  
```<<command>>```

3. Create setfusion schema  
```setfusion-security```

4. Grant the privileges on setfusion schema to the setfusion user  
```<< command >>```
    
### MongoDB
No special configurations required.  

## Required dependencies
### git 2.7.4
 ```sudo apt-get install git```
 
### Docker Engine 17.09.0-ce
``` command ``` 
 
### Docker Compose 1.16.1
``` command```
 
## Other requirements
The SET Fusion host should be able to connect to SET NEXUS repository  

---
# SET Fusion Installation

## Prepare the release
### Clone the SET Fusion Release repository
```git clone  https://git.digitalharbor.us/set/set-fusion-release```

When logging in for the first time, the above command will prompt for GIT credentials, provide your GIT credentials.

### Update the setfusion.properties file with the environment details
Change the directory to set-fusion-release- and update setfusion.properties with Environment Name, MySQL and MongoDB database details.    
```        
        SET_FUSION_ENVIRONMENT=set-env
        SET_FUSION_MYSQL_HOST=1.2.3.4
        SET_FUSION_MYSQL_PORT=3306
        SET_FUSION_MYSQL_USER=setfusion
        SET_FUSION_MYSQL_PASSWORD=setfusion
        SET_FUSION_MONGO_HOST=1.2.3.4
        SET_FUSION_MONGO_PORT=11607
```      
### Install SET Fusion
Change the directory to set-fusion-release and execute the configure script.    
```
cd set-fusion-release
./install-setfusion.sh
```
 
## Start Set-Fusion
Open a new terminal.  
Change the directory to set-fusion-release.  
```
cd set-fusion-release
```

Login to the SET NEXUS Repository by running the following command:  
```
docker login -u <<username>> -p <<password>> set-nexus.digitalharbor.us:18444
```

Execute SET Fusion startup command  
```docker-compose up -d```
    
##  Verify SET Fusion is started and functioning as expected
Open a new terminal.  
Execute to following command:
```
docker run --env SET_FUSION_HOST=<SET-FUSION-HOST> --env SET_FUSION_PORT=<SET-FUSION-PORT>  set-nexus.digitalharbor.us:18444/set-fusion/fusion.validate:1.5
```
    
## Shutdown SET Fusion
Run the following command to stop SET Fusion
```
docker-compose stop
```

    
    
    
    
    

