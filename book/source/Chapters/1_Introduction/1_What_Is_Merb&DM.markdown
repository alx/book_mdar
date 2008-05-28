## Qu'est ce que Merb, DataMapper et RSpec ?

> Si vous ne vivez pas dans l'intrépidité, vous restez au même endroit. - Alice Bartlett

Merb, DataMapper et RSpec sont tous des projets open-source parfaits pour construire de très bonnes applications. Ils ont tous un développement actif et bien que cela puisse être parfois dur, nous ferons de notre mieux pour vous garder à jour.

### [Merb](http://merbivore.com/)

C'est relativement un nouveau framework (tout comme Ruby on Rails) et a été créé par [Ezra Zygmuntowicz](http://brainspl.at/). Merb veut dire Mongrel + ERB bien qu'il supporte maintenant l'[interface webserver rack](http://rack.rubyforge.org/) ce qui le rend utilisable avec n'importe quel serveur web supportant Rack (Mongrel, Thin, Ebb, etc...).

Si vous connaissez Ruby et que vous avez utilisé Rails vous devriez facilement prendre en mail Merb. Tant que Rails est obstiné, Merb est agnostique - avec respect pour l'ORM, la librairie de javascipt et le language de template. La philosophie de merb ne croit pas avoir un framework monolitique. A la place, cela consiste à avoir plusieurs gems : `merb-core`, `merb-more` et `merb-plugins`. Cela signifie qu'il est possible de prendre et choisir la fonctionnalité dont vous avez besoin, au lieu de s'encombrer avec d'un framework avec des fonctionnalités non essentiel. Le gem `merb` installe les deux `merb-core` et `merb-more`. C'est tout ce dont vous avez besoin pour rapidement démarrer. L'avantage de cette modularité est que le framework reste simple et se spécifie avec l'ajout d'autre gems.

Grâce à la modularité de Merb, vous n'êtes pas obligé d'utiliser certaines librairies en particulier. Merb peut ainsi s'interfacer avec plusieurs RM populaire et fournit un support pour Test::Unit et RSpec.

`merb-core` seul peut fournir un framework très léger (à la [camping](http://code.whytheluckystiff.net/camping/)) qui peux être utilisé pour créer une application web simple comme un serveur d'upload ou un fournisseur d'API où les fonctionnalités d'un framework tout-compris ne sont pas nécessaire.

### [DataMapper](http://datamapper.org/)

DataMapper est un Mappeur relationnel aux objets (ORM) écrit en Ruby par Sam Smoot. Nous utiliserons DataMapper avec Merb. Il est aussi possible d'utiliser le même ORM que Rails (ActiveRecord), mais étant donné la pléthore de tutoriels d'utilisation d'ActiveRecord, nous avons décidé de nous concentrer sur DataMapper.

DataMapper est rempli de belles fonctionnalités qui le rendent plus rapide que ActiveRecord dans certain cas. C'est notamment le cas quand on traite les attributs de la base de donnée. Ainsi, le schéma, les migrations et les attributs sont tous définis au même endroit : vos modèles. Vous n'avez donc plus rien dans votre base de donnée ou dans d'autre fichiers à regarder pour voir ce qui est défini.

Étant donné que DataMapper a des similitudes avec ActiveRecord, seules les différences avec ActiveRecord seront mises en lumière tout au long de ce livre.

### [RSpec](http://rspec.info/)

RSpec est un framework de conduite automatisée de tests par aspect ( en anglais: BDD, Behavious Driven Devlopment) pour Ruby.
Merb supporte actuellement les frameworks de test Test::Unit et RSpec. Ainsi, les specs pour Merb et Datamapper sont écrit avec RSpec. Nous couvrirons plusieurs aspects de RSpec mais cela ne sera pas notre principal but.

RSpec est composé de deux framework - un framework d'histoires (Story) où l'utilisateur peut décrire un scénario au niveau de l'application et un framework de Specs qui est utilisé pour décrire le comportement au niveau d'un object spécifique.
(TODO) Beef up this section a little more?
