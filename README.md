====
Deployment NodeJS application using Heroku
====

Initial setup
1. Install Heroku Command Line Interface (CLI)/ Toolbelt 
2. Setup the MongoDB Atlas (make sure to set the IP access setting in mongodb atlas such that everyone can acess that)
3. Create a new database and collection

Connecting to MongoDB Atlas cluster 
1. After clicking the connect button, set Node.js version 2.2.12 or later
2. Copy the connection string and enter the required parameter values (while entering parameters, make sure that they are [URL encoded](https://docs.atlas.mongodb.com/troubleshoot-connection/#special-characters-in-connection-string-password))

Setting up the environment variables
~~~
MONGO_URL=<MongoDB Atlas connection string>
NG_CMD=prod
~~~

Importing data into MongoDB Atlas
~~~
mongoimport --host <your primary cluster name ending in 27017> --db <database name> --collection <collection name> --type tsv --file <filename> --authenticationDatabase admin --ssl --username <your username> --password <your password> --headerline
~~~

Deploying application on localhost(port:8080)
~~~
node app.js
~~~

Initiating the Heroku session (from your applicaiton folder)
~~~
heroku login
~~~

Create framework for production
~~~
git create --remote production
~~~

Setting up the environment variable in Heroku (GUI based option also present)
~~~
heroku config:set MONGO_URL=<MongoDB Atlas connection string> --remote production
heroku config:set NG_CMD=prod --remote production
~~~

Setting remote and pushing  
~~~
heroku git:remote -a <your unique heroku website name ex. guarded-plains-08242>
git push heroku master
~~~

Congratulations, your website should be live now!!







