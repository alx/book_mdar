## Un petit blog

#### Ce qui sera couvert

 * Configuration de l'application de blog d'exemple
 * Création des Models
 * Configuration des routes
 * Controllers RESTful
 * Quelque helpers de vue de `merb-helper`
 * Configuration et envoi de mails

Dans cette example nous allons développer une petite application de blogging. C'est une bonne 
idée de récupérer le code source de [http://github.com/deimos1986/book_mdar/tree/master/code](http://github.com/deimos1986/book_mdar/tree/master/code), 
ainsi suivre avec l'exemple.

Premièrement, nous allons définir quelques fonctionnalités que nous attendons 
d'une application de blogging.

 * Puublication de billets
 * Laisser des commentaires
 * Envoyer des notifications par email
 * Attacher des Images
 * Authentification

Nous allons appeler notre application `glob`, qui est le mot blog à l'envers. Vous pouvez 
tout à fait changer de nom pour votre application, mais souvenez vous de changer le mot 
`glob` pour le nom de votre application.

Pour réaliser une nouvelle application, nous allons utiliser la commande

    merb-gen app golb

Set up the configuration files for your application, this lets Merb know what 
gems to load for plugins and generators.

`config/init.rb`

    use_orm :datamapper

    use_test :rspec

  	dependencies "dm-validations"


Maintenant ajouter un fichier config/dataase comme ci suit:

    ---
    # This is a sample database file for the DataMapper ORM
    development: &defaults
      # These are the settings for repository :default
      adapter:  mysql
      database: golb
      encoding: utf8
      username: root
      password: 
      host:     localhost

      # Add more repositories
      # repositories:
      #   repo1:
      #     adapter:  postgresql
      #     database: sample_development
      #     username: the_user
      #     password: secrets
      #     host:     localhost
      #   repo2:
      #     ...

    test:
      <<:       *defaults
      database: golb_test

      # repositories:
      #   repo1:
      #     database: sample_development

    production:
      <<:       *defaults
      database: golb_production

      # repositories:
      #   repo1:
      #     database: sample_development
  
	---
	    
	    
Note: DataMapper has a rake task to generate a default database.yml file:
    
    dm:db:database_yaml
    
You can also put a database URI in development.rb (or other environments) just as easily:

    Merb::BootLoader.after_app_loads do
      DataMapper.setup(:default, 'mysql://user:pass@localhost/database')
    end
      
Maintenant nous sommes pret, rock and roll…
