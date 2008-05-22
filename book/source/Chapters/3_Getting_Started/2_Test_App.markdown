## Création d'une application

Maintenant que tout est installé, il est temps de créer une application Merb de test.

Merb-more vient avec un `gem` appelé `merb-gen`, cela fournit un outil en ligne de commande du même nom utilisé par tous les générateurs dont vous aurez besoin. Vous pouvez le considérer comme le `script/generate` de Merb. Lancer la commande `merb-gen` sans arguments vous montreras tous les générateurs disponible.

Merb suit la même convention de nommage que Rails, ainsi 'my\_test\_app' et 'Test2' sont des noms valides mais 'T 3' ne l'est pas (ils ont besoin d'être des noms valides de tables SQL).

    merb-gen app test
    
Cela générera une application Merb vide, allons-y et regarder. Vous remarquerais que la structure des répertoire est similaire à Rails, avec peu de différence.

    # sortie attendu
    RubiGen::Scripts::Generate
      create  app
      create  app/controllers
      create  app/helpers
      create  app/views
      create  app/views/exceptions
      create  app/views/layout
      create  autotest
      create  config
      create  config/environments
      create  public
      create  public/images
      create  public/stylesheets
      create  spec
      create  app/controllers/application.rb
      create  app/controllers/exceptions.rb
      create  app/helpers/global_helpers.rb
      create  app/views/exceptions/internal_server_error.html.erb
      create  app/views/exceptions/not_acceptable.html.erb
      create  app/views/exceptions/not_found.html.erb
      create  app/views/layout/application.html.erb
      create  autotest/discover.rb
      create  autotest/merb.rb
      create  autotest/merb_rspec.rb
      create  config/rack.rb
      create  config/router.rb
      create  config/init.rb
      create  config/environments/development.rb
      create  config/environments/production.rb
      create  config/environments/rake.rb
      create  config/environments/test.rb
      create  public/merb.fcgi
      create  public/images/merb.jpg
      create  public/stylesheets/master.css
      create  spec/spec.opts
      create  spec/spec_helper.rb
      create  /Rakefile

### Configuration de Merb

Avant de lancer le serveur, vous devez éditer le fichier init.rb et décommenter la ligne suivante ( C'est nécessaire si vous avez besoin de vous connecter à une base de donnée, ce que nous ferons dans notre cas):

config/init.rb
    
    use_orm :datamapper
    
Tapez désormais `merb` dans votre console pour démarrer le serveur.

    Started merb_init.rb ...
    No database.yml file found in /Users/work/merb/example_one/config.
    A sample file was created called database.sample.yml for you to copy and edit.

Comme vous pouvez le voir, nous avons oublié de définir la base de donnée. Un fichier d'example à gentiement été généré pour nous. Editez le et renommé le en database.yml:

    # Ceci est un example de fichier database pour l'ORM DataMapper
    development:
       adapter: mysql
       database: test
       username: root
       password: 
       host: localhost
	   socket: /tmp/mysql.sock

N'oubliez pas de spécifier votre socket. Si vous ne connaissez pas son emplacement, vous pouvez chercher en tapant:

	mysql_config --socket

Un redemmarage de Merb vous montreras que tout fonctionne normalement.

La commande suivante vous donnera accés à la console de Merb:

	merb -i

Vous pourrez constater que Merb tourne sur le port 4000, mais vous pouvez le changer avec l'option `-p [numéro du port]`, Toutes les options peuvent être trouvé en tapant:

    merb --help
    
Vous pouvez même lancer avec toutes applications serveur supporté par rack (thin, evented_mongrel, fcgi, mongrel et webrick):
    merb -a thin
