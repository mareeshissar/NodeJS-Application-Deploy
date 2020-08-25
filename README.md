# Deploying NodeJS application using Heroku☁️


Initial setup
1. Download and install [Heroku Command Line Interface (CLI)](https://devcenter.heroku.com/articles/heroku-cli) 
2. Setup your MongoDB Atlas account (make sure to set the IP access setting such that anyone can access)
3. Create a new user, database and collection

Connecting to MongoDB Atlas cluster (via command line)
1. Click the connect button (after selecting your cluster) and set Node.js version 2.2.12 or later
2. Copy the connection string and fill in the required parameter values, making sure they are [URL encoded](https://docs.atlas.mongodb.com/troubleshoot-connection/#special-characters-in-connection-string-password)

Setting up environment variables
~~~
MONGO_URL=<MongoDB Atlas connection string>
NG_CMD=prod
~~~

Importing data into MongoDB Atlas
~~~
mongoimport --host <your primary cluster name ending in 27017> --db <database name> --collection <collection name> --type tsv --file <filename> --authenticationDatabase admin --ssl --username <your username> --password <your password> --headerline
~~~

Installing dependencies 
~~~
npm install
~~~

Deploying application on localhost:8080
~~~
node app.js
~~~

Initiating Heroku session
~~~
heroku login
~~~

Creating framework for production
~~~
git create --remote production
~~~

Configuring the environment variable in Heroku (GUI based option also availaible)
~~~
heroku config:set MONGO_URL=<MongoDB Atlas connection string> --remote production
heroku config:set NG_CMD=prod --remote production
~~~

Setting remote and pushing  
~~~
heroku git:remote -a <your unique heroku website name e.g. guarded-plains-08242>
git push heroku master
~~~

Congratulations, your website should be [live](https://guarded-plains-08242.herokuapp.com/) now🎉!!

Reference:
[Node.js: Deploying Applications](https://www.linkedin.com/learning/node-js-deploying-applications/welcome)




