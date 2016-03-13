# twitterV2
###Basic Twitter-like web app built using Meteor.

Heroku url: http://twitterv2.herokuapp.com/

Tips: Sign In and follow people to populate your feed along with making your own tweets.

##How-to setup and run locally

1.Download meteor onto your machine. (warning: takes a while ~1.5GB)
  On OS X or Linux?
  "curl https://install.meteor.com/ | sh"
  
  Windows
  Get Installer from "https://www.meteor.com/install"

2. Clone repo and run command "meteor run" from inside the twitterV2 repo.

3. Open a web browser and go to "localhost:3000".

4. Remember db will be empty so make a few accounts in the app. The live app will be more full so make an account 
   and follow ohters to see feed.

##How does this app work 

Meteor is very flexible when it comes to structure allows for very modular design and this app will follow the publications and subscriptions design which is one of the primary meteor patterns ie. make template, give it helpers/events, subscribe it to some data it needs, and repeat with next element. The main 4 components comprising twitter and is a User Managment system , the display for who to follow , a tweet box, and a tweet feed all of which have their own seperate behavior and interactions with the DB.

Usually each components can be defined as seperate templates and loaded into the main page using built in Handlebar features.

######Client-side js: 
These templates can then be given "helpers" to add rendering logic by defining keywords {{example}},
for example pulling the correct tweets from the DB in a specific order and matching the ID to the given user.
The template is given "events" to allow for calling of various server-methods.
Templates will "subscribe" to neccesary data in the DB to operate on it ie. followUser template will "subscribe" to the "users" mongodb collection if it has been "published" by the server.

######Server-side js: 
Here data can be published "publications.js" to a given publication ("followers","tweets") which our templates "subscribe" to over in the client code which the helpers will use. Methods will also be defined such as "insertTweet" which will be used when requests occur from events triggered by template "event" code.

######Lib:
Simply one-liners to define the collection for the MongoDB ("users" collection defined by default from "accounts-ui" package).
userUtils created to not produce users who the current user is already following.

##Packages imported and a bit about what they did: meteor add/remove <package name>

  twbs:bootstrap - the bootstrap css lib.
  reywood:publish-composite - helped to add tweets to your feed from following a user by using a reactive join on the collections.
  accounts-password/accounts-ui - provides methods and classes to construct login and JSON data , encrypted passwords etc.



