## Qu'est ce que Merb, DataMapper et RSpec ?

> Si vous ne vivez pas dans l'intrépidité, vous restez au même endroit. - Alice Bartlett

Merb, DataMapper et RSpec sont tous des projets open-source parfaits pour construire de très bonnes applications. Ils ont tous un développement actif et bien que cela puisse être parfois dur, nous ferons de notre mieux pour vous garder à jour.

### [Merb](http://merbivore.com/)

Merb is a relatively new web framework with an initial 0.0.1 release in October
2006.  [Ezra Zygmuntowicz](http://brainspl.at/) is Merb's creator, and 
continues to actively develop Merb along with a dedicated development team at 
[Engine Yard](http://www.engineyard.com) and many other community contributors.  

TRANSLATION
C'est relativement un nouveau framework (tout comme Ruby on Rails) et a été créé 
par [Ezra Zygmuntowicz](http://brainspl.at/). Merb veut dire Mongrel + ERB 
bien qu'il supporte maintenant l'[interface webserver rack](http://rack.rubyforge.org/) 
ce qui le rend utilisable avec n'importe quel serveur web supportant Rack (Mongrel, Thin, Ebb, etc...).

Merb has obvious roots and inspiration in the 
[Ruby on Rails](http://www.rubyonrails.com) web framework.  If you know Ruby and
have used Rails you're likely to get the hang of Merb quite easily. 

TRANSLATION
Si vous connaissez Ruby et que vous avez utilisé Rails vous devriez facilement prendre en mail Merb. 
Tant que Rails est obstiné, Merb est agnostique - avec respect pour l'ORM, la librairie de javascipt et le language de template. La philosophie de merb ne croit pas avoir un framework monolitique. A la place, cela consiste à avoir plusieurs gems : `merb-core`, `merb-more` et `merb-plugins`. Cela signifie qu'il est possible de prendre et choisir la fonctionnalité dont vous avez besoin, au lieu de s'encombrer avec d'un framework avec des fonctionnalités non essentiel. Le gem `merb` installe les deux `merb-core` et `merb-more`. C'est tout ce dont vous avez besoin pour rapidement démarrer. L'avantage de cette modularité est que le framework reste simple et se spécifie avec l'ajout d'autre gems.

While there are similarities, Merb is not Ruby on Rails.  There are core 
differences in design and philosophy.  In many areas that Rails chooses to be 
opinionated, Merb is agnostic - with respect to the ORM, the JavaScript library 
and template language. The Merb philosophy also disbelieves in having a monolithic 
framework. Instead, it consists of a number of gems: `merb-core`, `merb-more` and 
`merb-plugins`. This means that it is possible to pick and choose the 
functionality you need, instead of cluttering up the framework with non-essential 
features. 



The `merb` gem installs both `merb-core` and `merb-more`; all you need in order to 
get started straight away.  The benefit of this modularity is that the framework 
remains simple and focused with additional functionality provided by gems.

Thanks to Merb's modularity, you are not locked into using any particular 
libraries. For example, Merb ships with plugins for several popular ORMs and 
provides support for both Test::Unit and RSpec.

`merb-core` alone provides a lightweight framework 
(a la [camping](http://code.whytheluckystiff.net/camping/)) that can be used to 
create a simple web app such as an upload server or API provider where the 
functionality of an all-inclusive framework is not necessary.

### [DataMapper](http://datamapper.org/)

DataMapper is an Object-Relational Mapper (ORM) written in Ruby by Sam Smoot. 
We'll be using DataMapper with Merb. As previously mentioned, Merb does not require 
the use of DataMapper.  You can just as easily use the same ORM as Rails 
(ActiveRecord) if you prefer.

TRANSLATION
DataMapper est un Mappeur relationnel aux objets (ORM) écrit en Ruby par Sam Smoot.
 Nous utiliserons DataMapper avec Merb. 
Il est aussi possible d'utiliser le même ORM que Rails (ActiveRecord), mais étant donné la pléthore de tutoriels d'utilisation d'ActiveRecord, nous avons décidé de nous concentrer sur DataMapper.

We have chosen to use DataMapper because of it's feature set and performance. One
of the differences between it and ActiveRecord that I find useful is the way 
database attributes are handled. The schema, migrations and attributes are all 
defined in one place: your model. This means you no longer have to look around in 
your database or other files to see what is defined.  

TRANSLATION
DataMapper est rempli de belles fonctionnalités qui le rendent plus rapide que ActiveRecord dans certain cas. C'est notamment le cas quand on traite les attributs de la base de donnée. Ainsi, le schéma, les migrations et les attributs sont tous définis au même endroit : vos modèles. Vous n'avez donc plus rien dans votre base de donnée ou dans d'autre fichiers à regarder pour voir ce qui est défini.

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
