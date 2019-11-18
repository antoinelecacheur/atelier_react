## State

 

Les composants peuvent être dotés d'un **state**, un état dans lequel on peut stocker toutes sortes de propriétés du composant, en particulier des propriétés qui sont amenées à être modifiées. Par exemple pour une boîte de dialogue on aura dans le state un attribut **isOpen** qui vaudra soit **true** soit **false**, qu'on voudra changer pour préciser si on doit afficher ou pas cette boîte de dialogue.

 

Un composant n'a pas nécessairement de **state**, ceux-ci sont appelés **stateless components**, et sont déclarés en tant que fonction. En effet, il n'est possible de définir un **state** que dans les composants déclarés en tant que class.

 

Pour déclarer le **state** dans une classe, il existe 2 manières.

 

- Avec un constructeur :

```javascript

class ComposantAvecState extends React.Component {

    constructor(props) {

        super(props)

        this.state = {

            texte: "Texte à afficher"

        }

    }

 

    render() {

        return (

            <div>

                {this.state.texte}

            </div>

        )

    }

}

```

 

- Sans constructeur :

```javascript

class ComposantAvecState extends React.Component {

    state = {

        texte: "Texte à afficher"

    }

 

    render() {

        return (

            <div>

                {this.state.texte}

            </div>

        )

    }

}

```

 

Les deux syntaxes donnent le même résultat et je n'ai pas trouvé de différence de comportement entre les deux en cherchant sur internet.

 

Pour modifier cet état, on doit impérativement utiliser la méthode **setState** propre à React :

```javascript

class ComposantAvecState extends React.Component {

    state = {

        texte: "Texte à afficher"

    }

 

    render() {

        return (

            <div>

                <h1>{this.state.texte}</h1>

                <button onClick={() => this.setState({texte: "Le state a été modifié"})}>Mon premier setState</button>

            </div>

        )

    }

}

```

 

On passe en paramètre de setState un objet qui contient l'attribut à modifier, ou à rajouter avec les modifications souhaitées.

 

## Utiliser des méthodes

 

Pour gérer le clic bouton précédent, on peut définir une méthode qui va se charger d'effectuer l'ensemble d'actions souhaitées. En effet, dans le cas précédent la modification était simple, mais si on commence à vouloir inclure plusieurs vérifications et modifications au moment du clic, il vaut mieux définir tout ça dans une méthode associée à notre classe.

 

Là aussi, il y a deux manières de faire :

 

- La première nécessite l'utilisation du constructeur dans la classe.

 

```javascript

class ComposantAvecState extends React.Component {

    constructor(props) {

        super(props)

        this.state = {

            texte: "Texte à afficher"

        }

        // Nécessaire de bind pour pouvoir utiliser l'instance this de la classe au sein de la méthode handleClick

        this.handleClick = this.handleClick.bind(this)

    }

 

    // On peut nommer par convention la gestion des événements handleClick, handleChange, etc.

    handleClick() {

        this.setState(

            {

                texte: "Le state a été modifié"

            }

        )

    }

 

    render() {

        return (

            <div>

                <h1>{this.state.texte}</h1>

                <button onClick={this.handleClick /* Pas de parenthèses ici ! */}>Mon premier setState</button>

            </div>

        )

    }

}

```

 

- La seconde ne nécessite pas de bind **this** et donc est indifférente de disposer d'un constructeur ou non, elle repose sur l'utilisation des *arrow functions* :

```javascript

class ComposantAvecState extends React.Component {

    state = {

        texte: "Texte à afficher"

    }

 

    // Cette fois, this est accessible directement, car on a utilisé une fonction fléchée.

    handleClick = () => {

        this.setState(

            {

                texte: "Le state a été modifié"

            }

        )

    }

 

    render() {

        return (

            <div>

                <h1>{this.state.texte}</h1>

                <button onClick={this.handleClick /* Pas de parenthèses ici ! */}>Mon premier setState</button>

            </div>

        )

    }

}

```

 

L'utilisation de fonctions fléchées peut être controversée, il y a quelques désavantages :

 

- La méthode n'est pas identifiée en cas d'héritage pour la transmettre à une classe enfant. Mais en React, on ne fait pas d'héritage avec les classes.

 

- Une nouvelle fonction est créée à chaque re-render du composant, on pourrait donc se dire que leur utilisation dégrade la performance de l'appli... Toutefois, après avoir lu plusieurs articles sur le sujet, la différence est tellement minime qu'il faudrait des centaines ou des milliers de fonctions fléchées définies pchaque seconde pour que ce soit réellement perceptible.

 

En résumé, il ne faut pas se priver d'utiliser les fonctions fléchées, elles simplifient l'écriture du code, et permettent d'éviter de bind **this** pour chaque méthode définie...

 

 

## Cycle de vie

 

Un composant React (i.e : une class qui étend React.Component) dispose de méthodes qui vont lui permettre de mieux gérer son cycle de vie. C'est-à-dire, effectuer certaines actions lors de la création du composant pour l'afficher la première fois, puis gérer les mises à jour de ce composant (sans recharger toute la page) ou encore ce qu'il convient de faire lorsqu'on *démonte* le composant lors d'un changement ou une fermeture de page. Un récapitulatif de toutes les méthodes [ici](https://blog.bitsrc.io/react-16-lifecycle-methods-how-and-when-to-use-them-f4ad31fb2282). Les plus importantes sont :

 

- `componentDidMount()` : cette méthode est appelée juste après le premier rendu du composant. C'est donc le moment idéal pour charger des données provenant d'un web-service. On est sûr que notre composant existe bien et qu'on peut lui envoyer les données à afficher.

 

```javascript

class ComposantAvecFetch extends React.Component {

    state = {

        data: []

    }

 

    componentDidMount() {

        // fetch est une méthode utilitaire javascript qui permet de gérer les requête HTTP, si on ne précise rien on effectue une requete GET, mais on peut donner beaucoup de paramètres pour gérer les headers, les verbes, le body, etc.

        fetch("https://api.imgflip.com/get_memes")

        .then(response => response.json())

        .then(json => this.setState(

            {

                data: json.data.memes

            }

        ))

    }

 

    render() {

        const {data} = this.state

        return (

            <div>

                {data.map(

                    meme => {

                        <span>Id : {meme.id}. Name : {meme.name}</span><br/>

                    }

                )}

            </div>

        )

    }

}

```