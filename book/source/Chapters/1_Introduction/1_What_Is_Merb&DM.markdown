## Qu'est ce que Merb, DataMapper et RSpec ?

> Si vous ne voulez pas vivre a bord, vous prenez trop de chambre. - Alice Bartlett

Merb, DataMapper et RSpec sont toutes des projets open source qui sont génial pour construire des applications web de folie. Ils ont tous un développement actif et bien que cela soit dur, nous ferons de notre mieux pour rester à jour.

### [Merb](http://merbivore.com/)

C'est relativement un nouveau framework (un peu comme Ruby on Rails) et a été créé par [Ezra Zygmuntowicz](http://brainspl.at/). Merb représente Mongrel + ERB bien qu'il supporte maintenant l'[interface webserver rack](http://rack.rubyforge.org/) alors il peux être utiliser avec n'importe quel serveur web qui support rack (Mongrel, Thin, Ebb, etc...).

Si vous connaissez Ruby et que vous avez utilisé Rails vous devriez facilement prendre en mail Merb. Les différences constaté entre Merb et Rails sont d'être moins obstiné et avec une approche plus modulaire.
(TODO) - Clarify "opinionated?" doesn't force a particular style?
(TODO) - Add more differences, or change the structure of this sentence to just reflect on one major difference.

Merb comprend un certain nombre de gems: `merb-core`, `merb-more` et `merb-plugins`. Cela signifie qu'il est possible de prendre et choisir la fonctionnalité dont vous avez besoin, au lieu de s'encombrer avec d'un framework avec des fonctionnalités non essentiel. Le gem `merb` installe les deux `merb-core` et `merb-more`. C'est tout ce dont vous avez besoin pour rapidement démarrer. L'avantage de cette modularité est que le framework reste simple et se spécifie avec l'ajout d'autre gems.

Merci à la modularité de Merb, vous n'être pas bloqué sur l'utilisation de librairies en particulier. Par exemple, Merb s'interface avec plusieurs RM populaire et fourni un support pour Test::Unit et RSpec.

`merb-core` seul fournis un framework très léger (à la [camping](http://code.whytheluckystiff.net/camping/)) qui peux être utilisé pour créer une application web simple comme un serveur d'upload ou un fournisseur d'API où les fonctionnalité d'un framework tout-compris ne sont pas nécessaire.

### [DataMapper](http://datamapper.org/)

DataMapper est un Model-Objet Relationnel (ORM) écrit en Ruby par Sam Smoot. Nous allons utiliser DataMapper avec Merb. Il est possible d'utiliser le même ORM que Rails (ActiveRecor), mais comme il y a plein d'exemple d'utilisation d'ActiveRecord, nous avons décidé de nous concentré sur DataMapper.

DataMapper a plein de jolies fonctionnalités qui le rend plus rapide que ActiveRcord dans certain cas. C'est vraiment vrai pour moi quand on traite les attributs de la base de donnée. Le schéma, les migrations et les attributs sont tous défini au même endroit : vos models. Alors vous n'avez rien autour de votre base de donnée ou dans d'autre fichier à regarder pour voir ce qui est défini.

Comme DataMapper a des similitudes avec ActiveRecord nous ne mettrons en lumière que les différences avec ActiveRecord tout au long de ce livre.

### [RSpec](http://rspec.info/)

RSpec is a Behaviour Driven Development framework for Ruby. 
Merb currently supports the Test::Unit and RSpec testing frameworks. As the specs for Merb and Datamapper are written in RSpec, we will be covering some aspects of RSpec but it will not be our main focus.

RSpec is 
(TODO) Beef up this section a little. As this section is entitled "What's Merb, DataMapper & RSpec", we should probably spend a little time describing RSpec
