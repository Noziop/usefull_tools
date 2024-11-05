# H2G2PT - Le Guide du Voyageur Pythonique des Type Hints 🌌

## Message de Dernière Minute sur l'Hypernet 📡
DON'T PANIC ! 
Si vous lisez ceci, c'est que vous avez survécu à la destruction de la Terre pour faire place à une voie express hyperspatiale.
Voici votre kit de survie pour coder en Python :

- str, int, bool : Votre serviette numérique de base ✅
- List[str], Dict[str, int] : Votre Guide du Voyageur 📦
- Optional[str] : Pour quand votre serviette est au pressing 🤔
- Union[str, int] : Votre poisson Babel des types 🐠

## N'oubliez pas votre serviette !

Dans les profondeurs infinies du code Python, une question persiste : comment éviter le chaos typographique qui menace tout projet d'envergure ? La réponse, comme l'a découvert une certaine équipe de développement (dont le nom commence par T... 😏), réside dans les type hints.

Comme tout bon auto-stoppeur galactique le sait, la clé n'est pas de paniquer devant un code non typé, mais de s'armer de sa serviette et de son Guide. Ce guide, justement, vous apprendra à naviguer dans l'espace-temps du typage Python avec autant d'aisance qu'un certain builder naviguait dans les méta-données... mais ça, c'est une autre histoire !

### Les Types Fondamentaux - Votre Kit de Survie 🌱

```
# Les bases pour ne pas paniquer
name: str = "Arthur Dent"
answer: int = 42
has_towel: bool = True
```

### Les Collections - Votre Sac de Voyage Typé 🎒

```
from typing import List, Dict, Tuple

# Votre liste de provisions pour le voyage
provisions: List[str] = ["serviette", "Guide", "cacahuètes"]

# Votre guide des planètes visitées
planet_guide: Dict[str, bool] = {
    "Terre": False,  # Détruite pour une voie express
    "Magrathea": True,  # À visiter absolument
    "Vogsphere": False  # À éviter à tout prix
}

# Coordonnées dans l'espace-temps
coordinates: Tuple[int, int, int, str] = (42, 42, 42, "Jeudi")
```

### Optional - Pour les Choses Qui Peuvent Disparaître 🌌

Dans la galaxie Python, certaines choses peuvent être présentes... ou pas. Un peu comme certains projets web qui nous ont appris l'importance des types... 😏

```
from typing import Optional

def find_my_towel(location: str) -> Optional[str]:
    """
    Cherche votre serviette. Comme la Terre, 
    elle n'est pas toujours là où on l'attend.
    """
    towel_locations = {"sac": "serviette propre", "vaisseau": "serviette usée"}
    return towel_locations.get(location)
```

### Union Types - Le Restaurant au Bout de l'Univers des Types 🍽️

Dans la galaxie Python, comme dans tout bon restaurant intergalactique, il faut parfois être flexible !

```
from typing import Union

# Le Menu du Restaurant au Bout de l'Univers
Menu = Union[str, int, float, List[str]]

def order_pangalactic_gargle_blaster(menu_item: Menu) -> str:
    """
    Commande la boisson la plus dangereuse de l'univers.
    Accepte le nom, le numéro du menu, le prix ou la liste d'ingrédients.
    """
    match menu_item:
        case str():
            return f"Une boisson nommée {menu_item}, parfait pour oublier vos soucis !"
        case int():
            return f"Le cocktail numéro {menu_item}, excellent choix !"
        case float():
            return f"Pour {menu_item} crédits galactiques ? Un peu cher, mais ça vaut le coup !"
        case _:
            return "Une liste d'ingrédients ? Vous êtes plus courageux qu'un Vogon poète !"
```

### Literal Types - Les Destinations Sûres de l'Auto-Stoppeur 🚗

Parfois, dans la vaste galaxie du typage, vous voulez être VRAIMENT précis sur les valeurs acceptables.

```
from typing import Literal

# Les seuls endroits vraiment sûrs dans la galaxie
SafeLocation = Literal[
    "Magrathea",  # Si vous aimez les planètes custom
    "Milliways",  # Pour un bon repas
    "Ursa Minor Beta"  # Pour les vacances
]

def travel_safely(destination: SafeLocation) -> str:
    match destination:
        case "Magrathea":
            return "Attention aux missiles nucléaires !"
        case "Milliways":
            return "Réservation confirmée pour la fin de l'univers"
        case _:
            return f"En route pour {destination} !"
```

### Types Avancés - Pour les Hoopy Froods Qui N'Ont Pas Peur de Plonger 🎓

#### TypeVar - Le Générateur d'Improbabilité Infinie des Types

Imaginez un type qui peut se transformer comme le Coeur en Or peut voyager n'importe où... 
(Un peu comme certains builders dans une galaxie pas si lointaine... 😉)

```
from typing import TypeVar, List

# T est comme un auto-stoppeur : il peut prendre différentes formes !
T = TypeVar('T')

def first_item(container: List[T]) -> T:
    """
    Retourne le premier élément, peu importe son type.
    Comme le Guide : il s'adapte à toutes les situations !
    """
    if not container:
        raise ValueError("Empty container? DON'T PANIC!")
    return container[0]

# Usage
numbers = [42, 123, 256]
names = ["Arthur", "Ford", "Zaphod"]

answer = first_item(numbers)  # T devient int
pilot = first_item(names)    # T devient str
```

#### Generic - Le Restaurant au Bout de l'Univers des Classes 🍽️

Dans la galaxie Python, Generic est comme le Restaurant au Bout de l'Univers : 
il peut accueillir TOUS les types de clients !

```
from typing import Generic, TypeVar

T = TypeVar('T')

class GalacticContainer(Generic[T]):
    """
    Plus fiable qu'un ordinateur de bord dépressif,
    et plus flexible qu'un Babel Fish !
    """
    def __init__(self, value: T):
        self.value = value

    def get_value(self) -> T:
        return self.value

# Usage
answer_container = GalacticContainer[int](42)
name_container = GalacticContainer[str]("Marvin")
```

#### TypeVar avec Contraintes - Pour Éviter les Accidents Cosmiques 🚀

TypeVar, c'est comme le Coeur en Or avec son générateur d'improbabilité infinie, mais avec des règles ! 
(Parce que parfois, il faut savoir mettre des limites, même aux meilleures choses... 😉)

```
from typing import TypeVar, Optional

# Limiter les types possibles, comme les destinations sûres dans la galaxie
ContentType = TypeVar('ContentType', str, bytes)

def format_content(
    content: ContentType,
    subtitle: Optional[str] = None
) -> ContentType:
    """
    Formate le contenu de manière sûre et typée.
    Comme le Guide : toujours fiable, jamais approximatif !
    """
    if subtitle:
        return f"{content} - {subtitle}"  # type: ignore
    return content

# Usage
title = format_content("Le Guide du Voyageur Galactique")
full_title = format_content(
    "Le Guide", 
    "Ne paniquez pas !"
)
```

### Conclusion - Le Guide du Parfait Auto-Stoppeur des Types 🚀

Félicitations ! Vous avez maintenant toutes les bases pour survivre dans la galaxie Python avec vos type hints. Rappelez-vous :

- Gardez toujours votre serviette (et vos types) à portée de main
- Ne paniquez pas quand mypy vous envoie des erreurs
- Évitez la poésie Vogon et le typage Any
- Et surtout, n'oubliez pas : parfois les solutions les plus simples sont les meilleures !

Note secrète pour les voyageurs expérimentés :
Certains disent qu'il existe, quelque part dans la galaxie, des builders légendaires qui ont ouvert la voie aux type hints modernes. Mais ça, c'est une autre histoire... 😏

```
# Une dernière fonction pour la route
def thanks_for_all_the_types() -> str:
    return "So long, and thanks for all the type hints!"
```

N'oubliez pas : 42 n'est pas qu'un nombre, c'est aussi un type parfaitement valide ! 🎀

## Authors :

Made with love and passions by :
 - Fassih
 - Zoé