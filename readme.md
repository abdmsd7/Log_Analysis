## Log analysis
In this project, we create a internal tool by using python that interacts with a portgese sql database to retrieve some information.
### This project aims for:
1. what are the most popular three articles of all time?
2. who are the most popular article authors of all time?
3. On which day more than 1% of requests leads to errors?
### Before making this project we need to have knowledge about some tools and languages:
1. [python]('http://www.python.org')
2. [vagrant]('https://www.vagrantup.com/')
3. [virtual box]('https://www.virtualbox.org/')
### Set up the vagrant:
1. Install Vagrant and virtualbox
2. Download or clone the fullstack-nanodegree-vm repository. Make sure that you downloaded this folder because it has some inbuilt packages if we install ubuntu manually by using “vagrant init trusty/ubuntu64” which doesn’t  contains all the packages that we goanna need in this project and in order to use them we need to install each and every project manually instead of that all the package available ubuntu version given in that file.
3. Download the data from here.
4. Make a new directory and unzip the folder “FSND-Virtual-Machine” into it.
5. Now open the vagrant folder in FSND-Virtual-Machine and unzip the data file “newdata”  to vagrant folder.
### Installing the virtual machine:
1. Install the vagrant and virtual Box.
2. After installing both of them open the terminal and change to the directory where vagrant folder is present
```
 C:\Users\windows>
C:\Users\windows> cd Downloads/FSND-Virtual-Machine/vagrant
C:\Users\windows\Downloads\FSND-Virtual-Machine\vagrant>
```
3. Now use the vagrant up to create and download the virtual machine
4. Virtual machine got installed and use `vagrant ssh` to use the virtual machine.
### Access the virtual machine:
1. Make sure you have changed to the path where you installed vagrant
2. First use, this command to start the virtual box
`$vagrant up`
3. use this command to access the ubuntu terminal
`$vagrant ssh`
4. Afterwards you are provided with ubuntu.
5. vagrant has given us the option to share a particular location to access the files both in host system and virtual machine i.e the place where ‘.vagrant’ file found it is the shared location in which we can create or copy files and access them  both on host and virtual systems.(generally .vagrant file is present in vagrant folder in our project).
6. To access that directory “cd /vagrant”. It will change to shared directory
7. To view all the files use
 `$ ls`
8. To create a database
`$psql #super user vagrant .``
* create database database-name
**Database created.**
To access this use `\c database-name`. or you can use this command `psql databsename`
9. Push the _newsdata.sql_ into database news
   `$psql -d news -f newsdata.sql`
   Data got dumped to the news database
### code using python:
1. `def get(query)`: This function is for opening the desired database,execute the query and display the output.
	* `connect(database= ”databasename”)` – This command is used to connect to our database.
	* `cursor()` -It is used to fetch record row by row.
2. `def top_three_articles_of_all_time()`: This function is used to find the most popular three articles of all time
3. `def top_three_articles_authors_of_all_time()`: This function is used to find the most popular author of all time.
4. `def days_errors_percentage()`: This function is used to find the day in which http requests are leads to errors more than 1%.
### To execute the tool:
`$python code.py`
It will connect to our database and performs the operation and output will be displayed as

### Output:
`vagrant@vagrant:/vagrant$ python code.py`
Most popular three articles of all time
=======================================
"Candidate is jerk, alleges rival" - 338647 views
"Bears love berries, alleges bear" - 253801 views
"Bad things gone, say good people" - 170098 views

Most popular article authors of all time
================================
Ursula La Multa - 507594 views
Rudolf von Treppenwitz - 423457 views
Anonymous Contributor - 170098 views
Markoff Chaney - 84557 views

More than 1% of request leads to errors
================================
July 17, 2016 - 2.26%
