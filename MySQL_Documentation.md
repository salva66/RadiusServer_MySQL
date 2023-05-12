1. Make installation of MySQL server

$sudo apt-get install mysql-server

2. start mysql service

$sudo systemctl start mysql

3. Create a database user named 'newuser' with password 'password' and grant them all privileges

$sudo mysql -u root -p

>CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';

>GRANT ALL PRIVILEGES ON *.* TO 'newuser'@'localhost';

>FLUSH PRIVILEGES;

>exit;

4. Create a database for radius users

$sudo mysql -u newuser -p

>CREATE DATABASE radius_db;

b) Create a table in the created database that shall have the user login credentials i.e username and password

>USE radius_users;

>CREATE TABLE user_credentials (

>  id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
  
>  username VARCHAR(30) NOT NULL,
  
>  password VARCHAR(30) NOT NULL);

c) Insert some values in the created table

>INSERT INTO user_credentials (username, password)

>VALUES
  
>  ('user1', 'password1'), ('user2', 'password2'), ('user3', 'password3');

_Go to the FreeRadius_Documentation, Implement the final instructed steps




