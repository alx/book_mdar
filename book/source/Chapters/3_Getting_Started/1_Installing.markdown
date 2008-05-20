## Démarrer

<a href="http://xkcd.com/303/" target="_blank"> <img src="http://imgs.xkcd.com/comics/compiling.png" alt="XKCD - Compiling"> </a>

Avant de commencer assurez vous d'avoir bien installer les outils suivants:

* [Ruby](http://www.ruby-lang.org/) 
* [RubyGems >= 1.1.0](http://www.rubygems.org/)
* [SVN](http://subversion.tigris.org/) et [git](http://git.or.cz/) (sur OSX, l'installation du port `git-core` fonctionne pour moi)

### La solution facile

 * Installing Merb, DataMapper and RSpec
 * Creating a temporary test app
 * The basic directory structure for the framework


Si vous êtes sur un système d'explotation *nix (comprenant Mac OS X) alors garder les mises à jours de toutes les versions de ces gems peux être fait simplement en utilisant le [Edgy sake tasks](http://edgy.4ninjas.org).

Tout ce dont vous avez besoin `RSpec`, `merb-core`, `merb-more`, `dm-core`, `dm-more`, `data_objects` et toutes les dépendances sont installé automatiquement..

		sudo gem install sake
		sake -i 'http://edgy.4ninjas.org/edgy.sake'
		sake edgy:install packages="merb-stack"
		

Une fois cela réalisé, pour garder une version à jour vous pouvez executer la commande suivante :

		sake edgy:update

### La solution plus compliqué

#### Installation de Merb

***
Si vous avez une ancienne version de Merb (<0.9.2) vous devez supprimer tous les gems de merb et datamapper avant de continuer. Utilisez `gem list` pour voir vos gems d'installé.

    sudo gem uninstall merb
***
L'installation des gems `merb` est aussi simple que:
    
    sudo gem install merb --source http://merbivore.org
    
*ou pour JRuby:*
    
    jruby -S gem install merb mongrel 
    
__Malheureusement__ nous vivons sur une version en dévelopement alors nous aurons besoin recuperer et compiler notre propre gems à partir des sources. Heureusment c'est plus simple que ce que l'on aurait pu croire...

Commençons par installer les `gems` en dépendances:

    sudo gem install rack mongrel json erubis mime-types rspec hpricot \
        mocha rubigen haml markaby mailfactory ruby2ruby

*ou pour JRuby:*

    jruby -S gem install rack mongrel json_pure erubis mime-types rspec hpricot \
        mocha rubigen haml markaby mailfactory ruby2ruby

Ensuite téléchargez les sources de `merb`:

    git clone git://github.com/wycats/merb-core.git
    git clone git://github.com/wycats/merb-plugins.git
    git clone git://github.com/wycats/merb-more.git

Enfin, installation des gems grâce à rake:

   	cd merb-core ; rake install ; cd ..    
    cd merb-more ; rake install ; cd ..
    cd merb-plugins; rake install ; cd ..

Le gem `json_pure` est nécessaire pour installer merb sur [JRuby](http://jruby.codehaus.org/) (l'implémentation Java de l'interpréteur Ruby), sinon l'utilisation du gem `json` est plus rapide.

Merb est ORM agnostic, mais comme le titre de ce livre le suggère, nous allons utiliser DataMapper.
Si vous souhaitez utilisé ActiveRecord ou vous amuser avec Sequl, consulter la [documentation de merb](http://merb.rubyforge.org/files/README.html) pour les instructions d'installation.

#### Installation de DataMapper


***
DataMapper est séparé entre `dm-core` et `dm-more`. Ainsi `datamapper 0.3` est dépassé depuis peu.
Si vous avez d'ancienne version de  `datamapper`, `data_objects` ou  `do_mysql`, `merb_datamapper` (< 0.9) vous devez les supprimé en premier. Supprimer le gem `merb_datamapper` avant d'installer `dm-merb` de `dm-more`.
***

Nous allons utilisé MySQL dans les exemples suivant, mais vous pouvez utiliser sqlite3 ou PostgreSQL après l'installation du gem approprié. Vous devez aussi vous assurez que MySQL est dans votre path système pour installer correctement le gem.

(TODO) - JDBC_do install

Récupérer les gems par les sources:

	git clone git://github.com/sam/do.git

	cd do
	cd data_objects
	rake install ; cd ..
	cd do_mysql  # || do_postgres || do_sqlite3
	rake install

    git clone git://github.com/sam/dm-core.git
    git clone git://github.com/sam/dm-more.git

    cd dm-core ; rake install ; cd ..
    cd dm-more
    cd merb_datamapper ; rake install ; cd ..    
    cd dm-migrations ; rake install ; cd ..
    cd dm-validations ; rake install ; cd ..
    
Pour mettre à jour les gems à partir des sources, lancer `git pull` et encore une fois `rake install`.

#### Installation de RSpec

Le gem `rspec` a été installé précédement avec l'installation de Merb. Néanmoins, si pour quelque raison que ce soir, vous ne l'avez pas installer, ou que vous souhaitez l'installer à partir des source, lancez les commandes suivantes:

    gem install rspec
    svn checkout http://rspec.rubyforge.org/svn/trunk rspec_trunk

(TODO) RSpec moved to http://github.com/dchelimsky/rspec/tree/master

