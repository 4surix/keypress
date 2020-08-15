Simple module permettant de récupérer les touches de clavier pressées.  

### Pourquoi ce module ?

J'ai créée un langage de programmation, [`Callect`](https://github.com/4surix/callect), et j'avais besoin de récupérer les touches de clavier pressées pour mon [event keypress](https://github.com/4surix/callect/wiki/Event-keys).  
  
J'ai trouvée des solutions, mais soit elle été trop complexe, soit trop volumineuse (`Tkinter`, `Pygame`, `pynput`, `curses`, ...).  
  
Je suis tombée sur [ce poste](http://code.activestate.com/recipes/134892), qui permettait de faire ce que je voulais, mais le code n'est pas optimisé et assez désordonné.  
  
J'ai du coup, à partir du code présent dans le poste, fait un module simple, léger, propre, pour juste capturer les touches pressées.  

### Documentation

Les fonctions ci-dessous sont bloquantes.  
  
**Attention**, si vous utilisez plusieurs `thread` dans votre programme, et que dans l'un vous utilisez ces fonctions et dans l'autre vous utilisez `input` (ou `sys.stdin`) en même temps, cela peut ne pas fonctionner correctement.  

#### getKey() -> str

Renvoie la touche pressée brute.  
Cela ne gère pas les touches faite en plusieurs caractères.  

```python
import keypress

if keypress.getKey() == '\t':
    print('Vous avez pressée la touche de tabulation !')

if keypress.getKey() == '\xe0':
    if keypress.getKey() == 'H':
        print('Vous avez pressée la touche flèche du haut !')
```

#### getName() -> str

Renvoie le nom de la touche pressée.

```python
import keypress

if keypress.getName() == 'Tab':
    print('Vous avez pressée la touche de tabulation !')

if keypress.getName() == 'Up':
    print('Vous avez pressée la touche flèche du haut !')
```

### Touches disponibles : 
| Touche  | Description |
| ------- | ----------- |
|  `a-z`  | Toute les touches de `a` à `z` minuscule. |
|  `A-Z`  | Toute les touches de `A` à `Z` majuscule. |
|  `0-9`  | Tout les chiffres de `0` à `9` |
|  `\w`   | Toute les touche basique (`é`, `{`, `-`, `@`, ...)|
|  `Ctrl+[a-z]`  | Toute les combinaisons `Ctrl` + `a` à `z`. |
|  `AltGr+[a-z]`  | Toute les combinaisons `Alt Gr` + `a` à `z`. |
|`F1-F12` | Toutes les touches fonction de `F1` à `F12` |
|`Escape` | Touche échappe |
|`Return` | Touche entrée |
|`Up`     | Touche flèche du haut |
|`Down`   | Touche flèche du bas |
|`Left`   | Touche flèche de gauche |
|`Right`  | Touche flèche de droite |
|`Tab`    | Touche tabulation |
|`Delete` | Touche Suppr |
|`Insert` | Touche Inser |
|`Begin`  | Touche Début |
|`End`    | Touche Fin |
|`PageUp` | Remonte d'une page |
|`PageDown`  | Descend d'une page |
|`BackSpace`  | Touche supprimer (flèche vers la gauche) |