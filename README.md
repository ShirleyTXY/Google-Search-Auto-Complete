# Google-Search-Auto-Complete
This project is to implement the basic function of auto complete. The input from users can be completed automatically and the probable results can be ordered according to the frequency of appearance.
# Usage
1. Get the conifguration of PC to build connection between map reduce and PC.

   ` $ ifconfig | grep inet | grep broadcast `

2. Get MySQL port and password

   ` $ SHOW VARIABLES WHERE Variable_name = 'port' ; `

   or

   ` $ status; `
   
### Build Database
1. Open Terminal

   ` cd /Applications/MAMP/Library/bin/ `

2. Create Database

   `$ create database test; `
   
   `$ use test; `
    
   `$ create table output(starting_phrase VARCHAR(250), following_word VARCHAR(250), count INT);`
    
   `$ GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '**_your-password_** ' WITH GRANT OPTION;   //enable remote data transfer`
   
   `$ FLUSH PRIVILEGES`
   
### Open Hadoop
 1. Start container and Hadoop
 2. Get into source of Hadoop
 
    `$cd src`
   
 3. Download the mysql-connector and put into hdfs
 
    `$ hdfs dfs -mkdir /mysql`
    
    `$ hdfs dfs -put mysql-connector-java-*.jar /mysql/`
    
 4. Edit the argument of the code to connect PC to MySQL
 
    `$ hdfs dfs -mkdir -p /input`
    
    `$ hdfs dfs -rm -r /output`
    
    `$ hdfs dfs -put bookList/*  /input/`
    
    `$ cd src`
 5. Open Driver.java and edit the arguments
 6. Run Auto-Complete
    
    `$ hadoop com.sun.tools.javac.Main *.java`
    
    `$ jar cf ngram.jar *.class`
    
    `$ hadoop jar ngram.jar Driver /input /output ngram_size threashold_size following_word_size`
  
### Run Auto-Complete User Interface
1. Download autocomplete.tar and put into path of web server

   `open XAMP -> preference -> web server`
   
2. Edit the argument in Autocomplete/ajax_refresh.php
3. Restart the server.
4. Run in localhost:8888.

# Scalibility
When the data is too big, we can use trie tree to optimize.
