# symfony4

## PHP Storm
File / Settings / Plugins / Browse remote

## Plugin :
Symfony plugin : https://plugins.jetbrains.com/plugin/7219-symfony-plugin

PHP Annotations : https://plugins.jetbrains.com/plugin/7320-php-annotations 

PHP Toolbox : https://plugins.jetbrains.com/plugin/8133-php-toolbox 

## Video :
Grafikart : [YouTube](https://www.youtube.com/playlist?list=PLjwdMgw5TTLX7wmorGgfrqI9TcA8nMb29) 

Les teachers du net : [YouTube](https://www.youtube.com/watch?v=2iUJvxkJydM)

https://symfonycasts.com/screencast/symfony 

https://symfonycasts.com/screencast/symfony/setup

## Note :
https://github.com/eewee/Symfony4

## Doc API :
https://api.symfony.com/4.1/Symfony/Component/Routing/Generator/UrlGenerator.html 

https://api.symfony.com/4.1/Symfony/Component/Serializer/Encoder/CsvEncoder.html 

## Vrac :
Liste bundle : [flex.symfony.com](https://flex.symfony.com/) (=https://symfony.sh/)

Demo/source Symfony 4 : [demo](https://github.com/symfony/demo)

[Subscriber](https://www.doctrine-project.org/projects/doctrine-orm/en/2.6/reference/events.html#lifecycle-events) : permet d'écouter les events de l'ORM preUpdate, postUpdate, preRemove, postRemove, ...

## Setup
__Projet web :__

```composer create-project symfony/website-skeleton my-project```


__Serveur web (option) :__

```composer require symfony/web-server-bundle --dev```


__Run serveur local sur http://127.0.0.1:8000/ :__

```php bin/console server:run```


__Checking for Security Vulnerabilities :__

```composer require sensiolabs/security-checker --dev```

__Apache - htaccess - Rewrite Rules ([source](https://symfony.com/doc/current/setup/web_server_configuration.html)) :__

```composer require symfony/apache-pack```


__Annotation :__

```composer require annotations```


__Check route :__

```php bin/console debug:router```


__SwiftMailer ([source](https://symfony.com/doc/current/email.html)) :__

```composer require symfony/swiftmailer-bundle```


__Form ([source](https://symfony.com/doc/current/components/form.html) / [type](https://symfony.com/doc/current/reference/forms/types/text.html)) :__

https://symfony.com/doc/current/forms.html 

```
composer require symfony/form

composer require symfony/validator

// Disable : HTML5 validator (required) :

{{ form_start(form, {'attr': {'novalidate': 'novalidate'}}) }}
```


## DOCTRINE :
__Voir la req qui sera utilisée lors de la création du schéma de la db__

```php bin/console doctrine:schema:create --dump-sql```

__Créer le schéma de la db :__

```php bin/console doctrine:schema:create```

__Maj le schéma de la db :__

```php bin/console doctrine:schema:update```

__Autre :__

```php bin/console doctrine:migrations:status --show-versions```

```php bin/console doctrine:migrations:version YYYYMMDDHHMMSS --delete```


__ADD :__

```php bin/console doctrine:migrations:execute YYYYMMDDHHMMSS --up```


__DROP :__

```php bin/console doctrine:migrations:execute YYYYMMDDHHMMSS --down```


__CREATE MIGRATION :__

```php bin/console make:migration```


__EXEC MIGRATIONS :__

```php bin/console doctrine:migrations:migrate```


__Si on ajoute manuellement une valeur dans entity :__

```php bin/console make:entity --regenerate```


__Status :__

```php bin/console doctrine:migrations:status```

__Faire une requête :__

```php bin/console doctrine:query:sql "SELECT * FROM user"```

```
Result : 
array(1) {
  [0]=>
  array(3) {
    ["id"]=>
    string(1) "1"
    ["username"]=>
    string(6) "Thomas"
    ["password"]=>
    string(60) "$2y$12$7kID8aQ/DOsY1Ue28SJV0OJwHXolrIsNce.Dhf/7dEt16gRH17ep6"
  }
}
```

```php bin/console doctrine:query:dql "SELECT u FROM App\Entity\User u"```

```Result : 
array(1) {
  [0]=>
  object(stdClass)#597 (5) {
    ["__CLASS__"]=>
    string(15) "App\Entity\User"
    ["id:App\Entity\User:private"]=>
    int(1)
    ["username:App\Entity\User:private"]=>
    string(6) "Thomas"
    ["password:App\Entity\User:private"]=>
    string(60) "$2y$12$7kID8aQ/DOsY1Ue28SJV0OJwHXolrIsNce.Dhf/7dEt16gRH17ep6"
    ["text:App\Entity\User:private"]=>
    array(0) {
    }
  }
```

__Comprendre le OneToOne, OneToMany, ManyToOne et ManyToMany + Repository :__

[OpenClassRoom](https://openclassrooms.com/fr/courses/5489656-construisez-un-site-web-a-l-aide-du-framework-symfony-4/5517031-gerez-vos-donnees-avec-doctrine-orm)

L'annotation ManyToOne a un attribut inversedBy.

L'annotation OneToMany a un attribut mappedBy.

## FRONT
Installer "Encore" pour la gestion des scss, css et js.

Lancer la commande “yarn encore dev --watch” durant le dev pour la compilation du scss.


__Encore (assets > scss, css, js, …) :__

https://symfony.com/doc/4.0/frontend/encore/installation.html 

https://symfony.com/doc/current/frontend/encore/simple-example.html 


__Compile assets once :  yarn encore dev__

Or, recompile assets automatically when files change : yarn encore dev --watch 

On deploy, create a production build : yarn encore production


__Bootstrap CSS/JS :__

https://symfony.com/doc/current/frontend/encore/bootstrap.html 

https://symfony.com/doc/current/form/bootstrap4.html


__Generate url (absolute / relative) :__

https://symfony.com/doc/current/routing.html#routing-requirements (generateUrl)

https://symfony.com/doc/current/controller.html (redirectToRoute / redirect)


__Template erreur 404, 500, etc … :__

https://symfony.com/doc/current/controller/error_pages.html 


__Log :__

https://symfony.com/doc/current/logging.html 

https://github.com/Seldaek/monolog/blob/master/doc/02-handlers-formatters-processors.md 


## Déploiement :
https://symfony.com/doc/current/deployment.html 


__Tuto pour déployer avec Git :__

https://fr.tuto.com/compte/achats/video/101881/player/#190751-preparation-du-depot-distant 

OVH > https://geekco.fr/blog/deployer-un-site-symfony3-sur-ovh

https://thatelo.fr/blog/deployer-symfony-git-serveur 


### SUR SERVEUR DISTANT :
__1/ git init :__

cd /kunden/homepages/xx/dxxxxxxxxx/htdocs/var/git

mkdir sf4.git

cd sf4.git

git init --bare


__2/ se placer dans le dossier hooks :__

cd  hooks

vi post-receive


__3/ Edit post-receive ET coller ceci :__

#!/bin/sh

git --work-tree=/kunden/homepages/xx/dxxxxxxxxx/htdocs/sf4_test/ --git-dir=/kunden/homepages/xx/dxxxxxxxxx/htdocs/var/git/sf4_test.git checkout -f


__4/ Droit execution :__

chmod +x post-receive


### SUR SERVEUR LOCAL (dans le dossier du projet symfony en local) :
git init

git remote add live ssh://uxxxxxxxx@homexxxxxxxxx.1and1-data.host/kunden/homepages/xx/dxxxxxxxxx/htdocs/var/git/sf4_test.git


git add .

git commit -m "Premier déploiement avec git"

git push live master


php composer.phar self-update

php composer.phar update

php composer.phar install --no-dev --optimize-autoloader

php bin/console cache:clear --env=prod --no-debug

php bin/console assets:install


### DIVERS :
__// install composer__

curl -sS https://getcomposer.org/installer | /usr/bin/php7.1-cli


__// update composer__

/usr/bin/php7.1-cli composer.phar self-update


__// Heroku deploy :__

https://afsy.fr/avent/2017/03-deployer-un-projet-symfony-flex-sur-heroku


__SSH 1and1 :__

Source : 
https://www.1and1.fr/digitalguide/serveur/securite/generer-des-cles-ssh-pour-votre-connexion-reseau/ 

http://thisisnotcnn.blogspot.com/2015/07/setup-remote-git-repository-on-1-server.html 

http://flosy.info/2012/07/utilisation-de-git-avec-un-hebergement-de-1and1/ 


__1/ Générer key :__

cd .ssh

ssh-keygen -t rsa -C “contact@tld.com” -b 4096

/Users/xxx/.ssh/1and1_rsa

mdp (optionnel)


__2/ Copier contenu 1and1_rsa.pub (local) dans ~/.ssh/authorized_keys (distant à la racine).__

on peut le faire en uploadant 1and1_rsa.pub sur le serveur.

cat id_rsa.pub >> ~\.ssh\authorized_keys


__3/ En local :__

cd ~/.ssh

ssh-add 1and1_rsa


__4/ En distant :__

On copie la key public dans .ssh/authorized_keys (à la racine du FTP 1and1) :

cat ~/id_rsa_1and1.pub >> ~/.ssh/authorized_keys


__5/ test en indiquant :__

ssh uxxxxxxxx@homexxxxxxxxx.1and1-data.host ls

On doit avoir le rendu sans devoir indiquer le mot de passe ssh.


#### clone :
git clone ssh://uxxxxxxxx@homexxxxxxxxx.1and1-data.host/kunden/homepages/xx/dxxxxxxxxx/htdocs/var/git/sf4_test.git

#### pull :
git pull ssh://uxxxxxxxx@homexxxxxxxxx.1and1-data.host/kunden/homepages/xx/dxxxxxxxxx/htdocs/var/git/sf4_test.git master
