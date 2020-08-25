# Deploying NodeJS application using Heroku☁️


Initial setup
1. Download and install [Heroku Command Line Interface (CLI)](https://devcenter.heroku.com/articles/heroku-cli) 
2. Setup your MongoDB Atlas account (configure appropriate IP access settings)
3. Create a new user, database and collection

Connecting to MongoDB Atlas cluster (via command line)
1. Click the connect button (after selecting your cluster) and set Node.js version 2.2.12 or later
2. Copy the connection string and fill in the required parameter values, making sure they are [URL encoded](https://docs.atlas.mongodb.com/troubleshoot-connection/#special-characters-in-connection-string-password)

### NOTE: Replace <text> with appropriate value

Setting up environment variables
~~~
MONGO_URL=<MongoDB Atlas connection string>
NG_CMD=prod
~~~

Importing data into MongoDB Atlas
~~~
mongoimport --host <primary cluster name ending in 27017> --db <database name> --collection <collection name> --type tsv --file <filename> --authenticationDatabase admin --ssl --username <username> --password <password> --headerline
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

Configuring environment variables in Heroku (GUI based option also available)
~~~
heroku config:set MONGO_URL=<MongoDB Atlas connection string> --remote production
heroku config:set NG_CMD=prod --remote production
~~~

Setting remote and pushing  
~~~
heroku git:remote -a <unique heroku website name e.g. guarded-plains-08242>
git push heroku master
~~~

Congratulations, your website should be [live](https://guarded-plains-08242.herokuapp.com/) now🎉!!

Reference:
[Node.js: Deploying Applications](https://www.linkedin.com/learning/node-js-deploying-applications/welcome)




