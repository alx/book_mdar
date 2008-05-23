## Un petit blog

#### Ce qui sera couvert

 * Configuration de l'application de blog d'exemple
 * Création des Models
 * Configuration des routes
 * Controllers RESTful
 * Quelque helpers de vue de `merb-helper`
 * Configuration et envoi de mails

Dans cette example nous allons dévelloper une petite application de blogging. C'est une bonne idée de récupérer le code source de [http://github.com/deimos1986/book_mdar/tree/master/code](http://github.com/deimos1986/book_mdar/tree/master/code), ainsi suivre avet l'exemple.

Premièrement, nous allons définir quelques fonctionnalités que nous attendons d'une application de blogging.

 * Puublication de posts
 * Laisser des commentaires
 * Envoyer des notifications par email
 * Attacher des Images
 * Authentification

Nous allons appeler notre application `glob`, qui est le mot blog à l'envers. Vous pouvez tout à fait changer de nom pour votre application, mais souvenez vous de changer le mot `glob` pour le nom de votre application.

Pour réaliser une nouvelle application, nous allons utiliser la commande

    merb-gen app golb

Nous allons utiliser le gem Linguistics plus tard, vous pouvez l'installer : 
    
    gem install Linguistics

Créer le fichier de configuration pour votre application pour permettre à Merb quel Plugins et generateur doit charger. 

config/init.rb

    use_orm :datamapper

    use_test :rspec

	dependencies "Linguistics", "dm-validations"


Maintenant ajouter un fichier config/dataase comme ci suit:
    
	---
	# Editer ce fichier:
	:development: &defaults
	    # Ce sont les configurations du repository :default
	    :adapter:  mysql
	    :database: golb
	    :host: localhost
	    :encoding: utf8
	    :username: root
	    :password:
	    :socket: /opt/local/var/run/mysql5/mysqld.sock

	test: &defaults
	    # Ce sont les configurations du repository :default
	    :database: golb_test
      
Maintenant nous sommes pret, rock and roll…
