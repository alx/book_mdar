## A little blog

#### What will be covered

 * Setting up the example blog application
 * Creating the models
 * Configuring your routes
 * RESTful controllers
 * Some of the view helpers in `merb_helpers`
 * Configuring and sending emails

In the examples, we'll be developing a small blogging application. It's a good
idea to grab the source code from [http://github.com/deimos1986/book_mdar/tree/master/code](http://github.com/deimos1986/book_mdar/tree/master/code), 
so you can follow along with the examples.

First of all, let's define some of the functionality we would expect from any 
blogging application. 

* Publishing posts
* Leaving comments
* Sending email notifications
* Attaching images
* Authentication

We're going to call our app `golb`. Think of it as a backward blog. Feel free 
to change the name of your app, but if you do, remember to replace the word
`golb` with the name of your app.

To make a new app we'll use the command

    merb-gen app golb

Set up the configuration files for your application, this lets Merb know what 
gems to load for plugins and generators.

`config/init.rb`

    use_orm :datamapper

    use_test :rspec

  	dependencies "dm-validations"


Now add a `config/database.yml` file with the following:
    
	---
	# Edit this file:
	:development: &defaults
	    # These are the settings for repository :default
	    :adapter:  mysql
	    :database: golb
	    :host: localhost
	    :encoding: utf8
	    :username: root
	    :password:
	    :socket: 

	test: &defaults
	    # These are the settings for repository :default
	    :database: golb_test
      
Now we're ready to rock and roll ...