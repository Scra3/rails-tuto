# Explication
Si on ajoute dans le fichier `/config/routes` la commande `resources :clients, only: :index`,
le framework Rails comprend qu'il faut relier la route `localhost/clients` à l'action `index`
qui se trouve dans le controller `clients_controller.rb`. Il faut noter que la route `index` répondra uniquement
par la méthode HTTP GET. Toutes les variables d'instances déclarées (les variables débutant par "@") sont accessibles dans le fichier `view/.haml`.
Dans notre cas, la construction de la réponse à la requête se fait dans le fichier `clients/index.haml` car le nom de l'action est `index`.

# Exemple

Requête depuis le navigateur : `HTTP GET localhost/clients`

Définition de la route pour créer l'interface de communication :
```
# config/routes.rb

resources :clients, only: :index
```

Définition de l'action du controller pour accéder aux données :
```
# clients_controller.rb

def index
    @clients = Client.all
end
```

Définition de la view pour générer l'HTML :

```
# index.haml

  %h1 "Il y a #{ @clients.length } clients"
```


