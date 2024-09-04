# FirstCrudG2

## Installation
Installation de la dernière version LTS avec les dépendances courantes pour un site web

    symfony new FirstCrudG2 --version=lts --webapp
    cd FirstCrudG2

### Mise à jours de composer

    composer update

### Lancement du serveur

    symfony serve -d

### Création d'un contrôleur

    php bin/console make:controller HomeController

2 fichiers sont créés, le contrôleur et sa vue.

    created: src/Controller/HomeController.php
    created: templates/home/index.html.twig

Pour voir le chemin généré pour le contrôleur

    symfony console debug:route

Pour le fichier

```php
# src\Controller\HomeController.php
# ...
    #[Route('/home', name: 'app_home')]
    public function index(): Response
    {
        return $this->render('home/index.html.twig', [
            'controller_name' => 'HomeController',
        ]);
    }
# ...
```

On souhaites avoir cette page comme accueil réel de notre site

```php
# src\Controller\HomeController.php
# ...
    #[Route('/', name: 'homepage')]
    public function index(): Response
    {
        return $this->render('home/index.html.twig', [
            'controller_name' => 'HomeController',
        ]);
    }
# ...
```

Et le template

```twig
{% extends 'base.html.twig' %}

{% block title %}{{ title }}{% endblock %}

{% block body %}
    <h1>{{ title }}</h1>
{% endblock %}
```

### Création d'une entité

    symfony console make:entity Article

    created: src/Entity/Article.php
    created: src/Repository/ArticleRepository.php

Le premier fichier sera le "mapping/DTO" d'une donnée et le deuxième sera un Manager

