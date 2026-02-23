# Flight Reservation System
---
## Steps to deploy Application
1. Clone this repository
```shell
1-- git clone https://github.com/shubhamkalsait/Flight-reservation.git
```

2. Install Mysql Server and create database
```shell
2-- apt update -y
3-- apt install mysql-server -y
4-- mysql_secure_installation          # y , ctrl+c , 4 cmd again then --> , n ,  y , y , y
5-- mysql -uroot -p
    >> create user linux identified by "Shridhar@123";  # your password in here
    >> grant all privileges on *.* to linux;
    >> flush privileges;
    >> create database flightdb;
    >> exit
```

3. Deploy Backend
```shell
6-- cd flight-reservation-app
7-- cd FlightReservationApplication
8-- apt install openjdk-17-jdk -y
9-- apt install maven -y
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

