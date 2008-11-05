## Le Framework

La structure des dossiers du projet créer doit ressembler à ce qu'il suit. 
Nous allons faire une brêve vue d'ensemble du framework ici et aller plus en profondeur 
sur chaque composant dans les chapitres suivants.

	test
	  |--> app
	  |--> autotest
	  |--> config
	  |--> log
	  |--> public
	  `--> spec

Le répertoire `app` contiens vos models, vues (incluant les pages d'exceptions et les layouts), les controllers et les helpers. Il y a aussi 
les Parts, ils héritent de `AbstractController` et sont similaire aux anciens composant Rails, i
mais ils sont léger et très pratique pour les sidebars widgets etc... 

`Mailers` qui héritent aussi de `AbstractController` ont leur propre 
dossier où les contrôlleurs et vues vivent.

	app
	  |--> controllers
	  |--> models (generated with a model)
	  |--> helpers
	  |--> mailers (generated with a mailer)
	  |--> helpers
	  |--> parts (generated with a parts controller)
	  `--> views


Le dossier `config` possédent tous les fichiers de configurations et d'environnement. Il est 
important d'éditer les fichier `init.rb` et `database.yml` avant 
de démarrer Merb. 

Le routeur de Merb, qui maps toutes les requêtes entrante vers les contrôlleurs et aussi 
ici. Le fichier `rack.rb` est le gestionnaire de rack et vous pouvez utiliser l'option 
`merb -a` pour changer d'adapter rack.

	config
	  `--> environments

RSpec, les specs peuvent être trouvé dans le dossier spec.

	spec
	
En complément de ces dossier, vous pouvez avoir un répertoire `gem`, qui conserve 
les gems gelé (voir le gel des gems pour plus d'information) et un dossier `lib` pour enregistrer 
d'autre fichier ruby.
