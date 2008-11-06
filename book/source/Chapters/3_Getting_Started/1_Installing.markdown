## Démarrer

<a href="http://xkcd.com/303/" target="_blank"> <img src="http://imgs.xkcd.com/comics/compiling.png" alt="XKCD - Compiling"> </a>

Avant de commencer assurez vous d'avoir bien installer les outils suivants:

* [Ruby](http://www.ruby-lang.org/) 
* [SVN](http://subversion.tigris.org/) et [git](http://git.or.cz/) (sur OSX, l'installation du port `git-core` fonctionne pour moi)
* [RubyGems >= 1.1.0](http://www.rubygems.org/)
* Un DBMS (nous utiliserons [MySQL](http://mysql.org/))

#### Ce que ça couvre

 * Installation de Merb, DataMapper et RSpec
 * Création d'une application de test temporaire
 * Les base de la structure des fichiers pour le framework

### La solution facile

Si vous êtes sur un système d'explotation *nix (comprenant Mac OS X) alors garder les mises à jours de toutes les versions 
de ces gems peux être fait simplement en utilisant les tâches Sake.

Merb sake tasks can be found in merb-more repository under tools directory.
Sake tasks for DataMapper are in dm-dev repository at
http://github.com/dkubb/dm-dev/.

To install Sake tasks run sake -i PATH where PATH is path to Sake tasks file
on your local machine. For example,

    sake -i ~/dev/opensource/merb/merb-more/tools/merb-dev.rake

To do a fresh clone of all repositories use sake dm:clone and	merb:clone,
respectively. And then to keep up to date you just need to execute:

    sake dm:update

and

    sake merb:update

to update Merb and DataMapper gems.

But what you really want is probably to wipe out Merb and DM gems before update,
do the update and install new updated gems. Use sake merb:gems:refresh and dm:gems:refresh to do so.

### If You're Hardcore

#### Installation de Merb

***
Si vous avez une ancienne version de Merb (<0.9.2) vous devez supprimer tous les gems de merb et 
datamapper avant de continuer. Utilisez `gem list` pour voir vos gems d'installé.
The following command will uninstall the gem you specify:

    sudo gem uninstall the_gem_name
***
L'installation des gems `merb` est aussi simple que:
    
    sudo gem install merb --source http://merbivore.org
    
*ou pour JRuby:*
    
    jruby -S gem install merb mongrel 
    
__Malheureusement__ nous vivons sur une version en dévelopement alors nous aurons besoin 
recuperer et compiler notre propre gems à partir des sources. Heureusment c'est 
plus simple que ce que l'on aurait pu croire...

Commençons par installer les `gems` en dépendances:

    sudo gem install rack mongrel json erubis mime-types rspec hpricot \
        mocha rubigen haml markaby mailfactory ruby2ruby templater

*ou pour JRuby:*

    jruby -S gem install rack mongrel json_pure erubis mime-types rspec hpricot \
        mocha rubigen haml markaby mailfactory ruby2ruby

Ensuite téléchargez les sources de `merb`:

    git clone git://github.com/sam/extlib.git
    git clone git://github.com/wycats/merb-core.git
    git clone git://github.com/wycats/merb-plugins.git
    git clone git://github.com/wycats/merb-more.git

Enfin, installation des gems grâce à rake:

    cd extlib ; rake install ; cd ..
    cd merb-core ; rake install ; cd ..    
    cd merb-more ; rake install ; cd ..
    cd merb-plugins; rake install ; cd ..

Note that Merb and DataMappers share Extlib library since after 0.9.3 release of DM.
Le gem `json_pure` est nécessaire pour installer merb sur [JRuby](http://jruby.codehaus.org/) (l'implémentation Java de l'interpréteur Ruby), sinon l'utilisation du gem `json` est plus rapide.

Merb est ORM agnostic, mais comme le titre de ce livre le suggère, nous allons utiliser 
DataMapper. Si vous souhaitez utilisé ActiveRecord ou vous amuser avec Sequel, 
consulter la [documentation de merb](http://merb.rubyforge.org/files/README.html) pour les instructions d'installation.

#### Installation de DataMapper

***
DataMapper est séparé entre `dm-core` et `dm-more`, l'ancien gem `datamapper` 
est maintenant dépassé.

Si vous avez d'ancienne version de `datamapper`, `data_objects` ou  `do_mysql`, 
`merb_datamapper` (< 0.9) vous devez les supprimé en premier. 
***

Nous allons utilisé MySQL dans les exemples suivant, mais vous pouvez utiliser sqlite3 ou 
PostgreSQL après l'installation du gem approprié. Vous devez aussi vous assurez que 
MySQL est dans votre path système pour installer correctement le gem.

Récupérer les gems par les sources:


    git clone git://github.com/sam/extlib.git  
    git clone git://github.com/sam/do.git
    
    cd extlib
    rake install ; cd ..
    cd do
    cd data_objects
    rake install ; cd ..
    cd do_mysql  # || do_postgres || do_sqlite3
    rake install

    git clone git://github.com/sam/dm-core.git
    git clone git://github.com/sam/dm-more.git

    cd dm-core ; rake install ; cd ..
    cd dm-more
    rake install
    
Pour mettre à jour les gems à partir des sources, lancer `git pull` et encore une fois `rake install`.

#### Installation de RSpec

Le gem `rspec` a été installé précédement avec l'installation de Merb. Néanmoins, si pour quelque raison 
que ce soit, vous ne l'avez pas installer, ou que vous souhaitez l'installer à partir des source, lancez les commandes suivantes:

    gem install -r rspec
    
    # or
    
    git clone git://github.com/dchelimsky/rspec.git
    cd rspec
    rake gem
    sudo gem install pkg/rspec-*.gem
