# Flight Reservation System
---
## Steps to deploy Application
1. Clone this repository
```shell
git clone https://github.com/shubhamkalsait/Flight-reservation.git
```

2. Install Mysql Server and create database
```shell
apt update -y
apt install mysql-server -y
mysql_secure_installation
mysql -uroot -p
>> create user linux identified by "Redhat";
>> grant all privileges on *.* to linux;
>> flush privileges;
>> create database flightdb;
>> exit
```

3. Deploy Backend
```shell
cd flight-reservation-app
cd FlightReservationApplication
apt install openjdk-17-jdk -y
apt install maven -y
#All of this below should edit in application.properties in both file path 1.flight-reservation-app/FlightReservationApplication  2.flight-reservation-app/FlightReservationApplication/src/main/resources
export DATASOURCE_URL="jdbc:mysql://localhost:3306/flightdb" # in here mysql endpoint or same as it is 
export DATASOURCE_USER="linux"
export DATASOURCE_PASSWORD="Redhat" # Your set password during you used in mysql paste here "Redhat"="Your_password"
export FRONTEND_URL="http://localhost:80"
mvn clean package  #   
java -jar target/flight*.jar
cd target
java -jar flightreservationApplication-0.0.1-SNAPSHOT.jar
```

4. Deploy Frontend (open new tab)
```shell
cd Flight-reservation
cd frontend
apt install nodejs npm -y
export VITE_API_URL=http://localhost:8080 # in here you ip
npm install
npm run build
apt install apache2 -y
cp -rvf dist/* /var/www/html/
systemctl start apache2
```

