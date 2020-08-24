
This is the README file for testing changes to the repository.I'm deploying to staging
=======
Deployment using Heroku
=======

Set the following environment variables
~~~
MONGO_URL
NG_CMD="prod"
~~~
=
Install Heroku Command Line Interface (CLI)/ Toolbelt 
=

=
Setup the MongoDB Atlas (make sure to set the IP access setting in mongodb atlas such that everyone can acess that)
=

=
Importing data into MongoDB Atlas
~~~
mongoimport --host <your primary cluster name ending in 27017> --db <database name> --collection <collection name> --type tsv --file <filename> --authenticationDatabase admin --ssl --username <your username> --password <your password> --headerline
~~~
=

From the application folder
Initiate your Heroku session
~~~
heroku login
~~~


Create git remote target for production (creating framework for production)
~~~
git create --remote production
~~~

Connect to cluster 
Set Node.js version 2.2.12 or later
Copy the connection string and enter the required values (while entering parameteers make sure that they are [URL encoded](https://docs.atlas.mongodb.com/troubleshoot-connection/#special-characters-in-connection-string-password))

=
~~~
Setting up the environment variable in Heroku (possible via GUI as well)
heroku config:set MONGO_URL=<MongoDB Atlas connection string> --remote production
heroku config:set NG_CMD=prod --remote production
~~~
=

~~~
heroku git:remote -a guarded-plains-08242
git push heroku master
~~~









