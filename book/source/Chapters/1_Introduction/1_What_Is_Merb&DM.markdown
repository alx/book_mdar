## Qu'est ce que Merb, DataMapper et RSpec ?

> Si vous ne vivez pas dans l'intrépidité, vous restez au même endroit. - Alice Bartlett

Merb, DataMapper et RSpec sont tous des projets open-source parfaits pour construire de très bonnes applications. Ils ont tous un développement actif et bien que cela puisse être parfois dur, nous ferons de notre mieux pour vous garder à jour.

### [Merb](http://merbivore.com/)

Merb est relativement un nouveau framework avec une première version 0.0.1 sortie en Octobre 
2006. [Ezra Zygmuntowicz](http://brainspl.at/) est le créateur de Merb et 
continue à développer activement Merb avec une équipe dédié à son développement chez 
[Engine Yard](http://www.engineyard.com) et de nombreux autres contributeurs.

Merb a évidemment puisé son inspiration dans le 
framework Web [Ruby on Rails](http://www.rubyonrails.com). Si vous connaissez Ruby et 
que vous avez utilisé Rails vous devriez facilement prendre en mail Merb. 




Bien qu'il existe des similitudes, Merb n'est pas Ruby on Rails. Il y a 
des différences fondamentales dans la conception et la philosophie. Dans de nombreux domaines où Rails choisit 
d'avoir des avis sur tout, Merb est agnostique - avec respect pour l'ORM, la librairie de javascipt 
et le language de template. La philosophie de merb ne croit pas avoir un framework monolitique. 
A la place, cela consiste à avoir plusieurs gems : `merb-core`, `merb-more` et 
`merb-plugins`. Cela signifie qu'il est possible de prendre et choisir la 
fonctionnalité dont vous avez besoin, au lieu de s'encombrer avec d'un framework avec des fonctionnalités non 
essentiel. 



Le gem `merb` installe les deux `merb-core` et `merb-more`. C'est tout ce dont vous avez besoin pour 
rapidement démarrer. L'avantage de cette modularité est que le framework 
reste simple et se spécifie avec l'ajout d'autres gems.



Thanks to Merb's modularity, you are not locked into using any particular 
libraries. For example, Merb ships with plugins for several popular ORMs and 
provides support for both Test::Unit and RSpec.

`merb-core` alone provides a lightweight framework 
(a la [camping](http://code.whytheluckystiff.net/camping/)) that can be used to 
create a simple web app such as an upload server or API provider where the 
functionality of an all-inclusive framework is not necessary.

### [DataMapper](http://datamapper.org/)

DataMapper est un Mappeur relationnel aux objets (ORM) écrit en Ruby par Sam Smoot.
Nous utiliserons DataMapper avec Merb. Comme mentionné précédemment, Merb ne requiert pas
l'utilisation de DataMapper. Vous pouvez très bien utiliser le même ORM que Rails 
(ActiveRecord) si vous préférez


Nous avons choisi d'utiliser DataMapper à cause de toutes ses fonctionnalités et ses performances. L'une
des différences entre lui et ActiveRecord que je trouve utile, est la manière 
dont il traite les attributs de la base de données. Ainsi, le schéma, les migrations et les attributs sont tous 
définis au même endroit : vos modèles. Vous n'avez donc plus rien à regarder dans 
votre base de donnée ou dans tout autres fichiers pour voir ce qui est défini.

Étant donné que DataMapper a des similitudes avec ActiveRecord, seules les différences avec ActiveRecord seront mises en lumière tout au long de ce livre.

### [RSpec](http://rspec.info/)

RSpec is a Behaviour Driven Development framework for Ruby. It consists of two
main pieces, a Story framework for integration tests and a Spec framework for
object tests. Both these components are implemented as Domain Specific
Languages which help to make the stories and specs created more readable.

TRANSLATION
RSpec est un framework de conduite automatisée de tests par aspect ( en anglais: BDD, Behavious Driven Devlopment) pour Ruby.
Merb supporte actuellement les frameworks de test Test::Unit et RSpec. Ainsi, les specs pour Merb et Datamapper sont écrit avec RSpec. Nous couvrirons plusieurs aspects de RSpec mais cela ne sera pas notre principal but.

Merb currently supports the Test::Unit and RSpec testing frameworks. Both Merb
and Datamapper use the RSpec testing frameworks and so we will be covering some
aspects so that you may use it for your own applications.

TRANSLATION
RSpec est composé de deux framework - un framework d'histoires (Story) où l'utilisateur peut décrire un scénario au niveau de l'application et un framework de Specs qui est utilisé pour décrire le comportement au niveau d'un object spécifique.
(TODO) Beef up this section a little more?
