

## Tuto python

## Useful Fonctions

```python
type(variable)
help("nomfonction ou module")
```

Print

```python
print("a =", a, "et b =", b)
```

```python
dir(mon_object)
#renvoie toutes les méthodes et attributs de l'object
```

```python
map(int, list)
map(lambda(x): return x*x, list) ## apply function to all element of list
```

`filter` creates a list of elements for which a function returns true.

```python
parameters = filter(lambda p: p.requires_grad, net.parameters())
#Optimizer can only take parameters which grad are required

```

```python
#Reduce is a really useful function for performing some computation on a list and returning the result. For example, if you wanted to compute the product of a list of integers.
from functools import reduce
product = reduce((lambda x, y: x * y), [1, 2, 3, 4])
```

## Variables 

*  permutations :

```python
  >>> a,b = b,a # permutation
```


* Global : On ne peut pas modifier des variables qui ne sont pas en paramètre dans un fonction sauf si on ajoute le mot clef global qui donne full access et permet les effet de bord. (ie la variable est modifiée après l'appel de la fonction).



## Boucles  conditionelles 



```python
>>> if a > 0: # Positif
...     print("a est positif.")
... elif a < 0: # Négatif
...     print("a est négatif.")
... else: # Nul
        print("a est nul.")
```



#### Test logique 



| Opérateur | Signification littérale |
| --------- | ----------------------- |
| <         | Strictement inférieur à |
| >         | Strictement supérieur à |
| <=        | Inférieur ou égal à     |
| >=        | Supérieur ou égal à     |
| ==        | Égal à                  |
| !=        | Différent de            |
| True      | vrai                    |
| False     | faux                    |



## Boucle

```python
while condition:
```

```python
for element in sequence:
    if element>5:
        break
    elif element==5
    	continue #return at while or next for
    print(element)
     
```





## Fonctions



```python
def nom_de_la_fonction(parametre1=0, parametre2=8, parametre3='a', parametreN=5):
    return truc
nom_de_la_fonction(5)
nom_de_la_fonction(parametreN=1,parametre1=5) #l'ordre n'influe pas
```

 Les fonctions lambda :

```python
lambda arg1, arg2,… : instruction de retour
f = lambda x: x * x
f(5)
```

Fonction avec une infinité de paramètre non nommé: Tous les paramètres non nommés sont mis dans un tuple.

```python
def fonction_inconnue(nom, prenom, *commentaires):
	return
fonction_inconnue(Groueix, Thibault, 1,2,3,4,5,6...)
#1,2,3,4,5,6 est mis dans le tuple commentaires.
```

Pour transformer un liste en tuple et la passer en argument :

```python
>>> liste_des_parametres = [1, 4, 9, 16, 25, 36]
>>> print(*liste_des_parametres)
1 4 9 16 25 36
```

Fonction avec une infinité de paramètre  nommé: Tous les paramètres  nommés sont mis dans un dictionnaire.

```python
def fonction_inconnue(nom, prenom, **nomme):
	return
fonction_inconnue(Groueix, Thibault, a=1,b=2,c=3,4,5,6...)
#a=1,b=2,c=3 est mis dans le dictionnaire nomme.
```

Pour transformer un dictionnaire en argument de fonction et la passer en argument :

```python
>>> fruits = {"pommes":21, "melons":3, "poires":31}
>>> print(**fruit)
```







## modules

```python
import math as mathematiques
mathematiques.sqrt(25)
import math
math.sqrt(25)
from math import sqrt
sqrt(25)
from math import * #pour avoir tout le monde dans l'espace de fonction prncipal
```

Il peut y avoir un fichier 

```shell
init.py 
```

 Dont le code est exécuté à l'importation du module.



## Fichier



Il faut préciser l'encodage des charactère en haut i.e; !

```python
# -*-coding:Latin-1 -*
import ...
```



Dans un fichier, pour séparer le fichier principal d'un module importé, on peut appeller :

```python
if __name__ == "__main__":
    table(4)
    os.system("pause")
```

```__name__``` est une variable crée automatique lorsqu'on execute un fichier .py en ligne de commande.



## Exception

```python
try:
    annee = numerateur / denominateur
     if annee<=0:
        raise ValueError("l'année saisie est négative ou nulle")
except ValueError:
    print("La valeur saisie est invalide (l'année est peut-être négative).")

except NameError:
    print("La variable numerateur ou denominateur n'a pas été définie.")
except TypeError:
    print("La variable numerateur ou denominateur possède un type incompatible avec la division.")
except type_de_l_exception as exception_retournee:
    print("Voici l'erreur :", exception_retournee)
finally:
    print("Le résultat obtenu est", resultat) ##always executed
```

Et les assertions :

```python
try:
    annee = int(annee) # Conversion de l'année
    assert annee > 0
except ValueError:
    print("Vous n'avez pas saisi un nombre.")
except AssertionError:
    print("L'année saisie est inférieure ou égale à 0.")
```

On peut lever une exception avec le mot-clef : **raise**

On peut définir de nouvelle classes d'exception qui héritent de la classe mère Exception, elles doivent définir __init__ et __str__.

```python
class MonException(Exception):
    """Exception levée dans un certain contexte… qui reste à définir"""
    def __init__(self, message):
        """On se contente de stocker le message d'erreur"""
        self.message = message
    def __str__(self):
        """On renvoie le message"""
        return self.message
```

# LISTE

Creation : on peut mettre plusieurs type différent dans une liste. LEs listes sont mutables.

```python
ma_liste = [1, 3.5, "une chaine", []]
ma_liste = list()
ma_liste.append("toto")
ma_liste+= malist2 # = ma_liste.extend(ma_list2)
ma_list.insert(2,'c')
malist.remove(3) #retire la première occurece de 3 dans la liste
del(maliste[4]) #retire le 5 ième élément de la liste.
```

### Parcours de liste



```python
for elt in ma_liste:
	blabla
for i, elt in enumerate(ma_liste):
	i est l'indice et elm est maliste[i]
```



### Filtrage de liste 

```python
nouvelle_squence = [element for element in ancienne_squence if condition]
```

# Tuple







# String

*Les str sont non mutables. Toutes les méthodes ne modifient pas l'object et en renvoie un nouveau.*

```python
#format :
# formatage d'une adresse
adresse = """
{no_rue}, {nom_rue}
 {code_postal} {nom_ville} ({pays})
""".format(no_rue=5, nom_rue="rue des Postes", code_postal=75003, nom_ville="Paris", pays="France")
print(adresse)
```

```python
chaine = "NE CRIE PAS SI FORT !"
chaine.lower() # Mettre la chaîne en minuscule
chaine.upper() # Mettre la chaîne en majuscule
```

Les chaînes sont des listes de charactères donc :

```python
>>> chaine = "Salut les ZER0S !"
>>> chaine[0] # Première lettre de la chaîne
'S'
>>> chaine[2] # Troisième lettre de la chaîne
'l'
>>> chaine[-1] # Dernière lettre de la chaîne
'!'
>>> len(chaine)
```

Les chaines de charactères ne supportent pas le remplacement d'un élément comme ceci.

```python
#remplacement dans une chaîne de charactère
#chaine[i] = "b" échoue car chaine[i] est un char alors que "b" est un str
chaine[i:i] = "b"
```

récuperer une sous chaîne :

```python
ma_chaine.split(" ") #renvoie une liste
ma_liste = ['Bonjour', 'à', 'tous']
" ".join(ma_liste)
>>>'Bonjour à tous'

```

```python
str.find('test', begin_indice, end_indice) #return indice de la première occurence de test
```

# Les dictionnaires :

### Creation

```python
mondict = {}
mondict = dict()
placard = {"chemise":3, "pantalon":6, "tee-shirt":7}
echiquier['a', 1] = "tour blanche" #la clef est un tuple
echiquier["hello"] = "tour blanche"
echiquier["hello"] #accès
mon_dictionnaire = {'pseudo', 'mot de passe'} #est un set  (ie une liste avec dont les valeurs dont uniques! )

```

On peut utiliser quasiment tous les types comme clef et tous comme valeur. On donner un tuple en clef comme dans l'exemple.

### Suppression d'un élément :

```python
placard = {"chemise":3, "pantalon":6, "tee shirt":7}
del placard["chemise"]
placard.pop("chemise") #idem mais renvoie la valeur

```

On peut aussi y stocker des référence de fonction.

### parcours :

```python
fruits = {"pommes":21, "melons":3, "poires":31}
for cle in fruits.keys():
	print(cle)
for valeur in fruits.values():
for cle, valeur in fruits.items():
```





# Class

```python
class Compteur:
    """Cette classe possède un attribut de classe qui s'incrémente à chaque
    fois que l'on crée un objet de ce type"""

    
    objets_crees = 0 # Le compteur vaut 0 au départ
    def __init__(self):
        """À chaque fois qu'on crée un objet, on incrémente le compteur"""
        Compteur.objets_crees += 1
    def combien(cls):
        """Méthode de classe affichant combien d'objets ont été créés"""
        print("Jusqu'à présent, {} objets ont été créés.".format(
                cls.objets_crees))
    combien = classmethod(combien)
```

* les méthodes de **class** prennent cls en argument, et doivent être passer comme un attribut statique ainsi : ```combien = classmethod(combien)```
* les methodes d'instance prennent **self** en argument, comme __init__
* les méthodes statiques ne prennent pas d'argument.
* les attributs d'instance prennent *self.attribut*
* les attributs statiques ne prennent rien type ```object_crées = 0```



### __ __dict__ __

Est un attribut spécial de toutes les classes qui contient sous forme de dictionnaire clef-valeur les attributs d'un object.

### Les propriétés

En python, tout est public. Mais pour par convention les attributs qui doivent être modifiés par accesseur/mutateur commencent par *_monAttribut*  . On définit ensuite des methode _get_monattribut et _set_monttribut et on définit un autre attribut comme ce dessous.

```python
nom_propriete = property(methode_accesseur, methode_mutateur, methode_suppression, methode_aide).
```

```python
class Personne:

    def __init__(self, nom, prenom):
        """Constructeur de notre classe"""
        self.nom = nom
        self.prenom = prenom
        self.age = 33
        self._lieu_residence = "Paris" # Notez le souligné _ devant le nom
    def _get_lieu_residence(self):
        print("On accède à l'attribut lieu_residence !")
        return self._lieu_residence
    def _set_lieu_residence(self, nouvelle_residence):
        print("{} déménage à{}.".format(self.prenom,nouvelle_residence))
        self._lieu_residence = nouvelle_residence
    # On va dire à Python que notre attribut lieu_residence pointe vers une propriété
    lieu_residence = property(_get_lieu_residence, _set_lieu_residence)
```

## heritage

```python
class Personne:
    """Classe représentant une personne"""
    def __init__(self, nom):
        """Constructeur de notre classe"""
        self.nom = nom
        self.prenom = "Martin"
    def __str__(self):
        """Méthode appelée lors d'une conversion de l'objet en chaîne"""
        return "{0} {1}".format(self.prenom, self.nom)

class AgentSpecial(Personne):
    """Classe définissant un agent spécial.
    Elle hérite de la classe Personne"""
    
    def __init__(self, nom, matricule):
        """Un agent se définit par son nom et son matricule"""
        # On appelle explicitement le constructeur de Personne :
        Personne.__init__(self, nom)
        self.matricule = matricule
    def __str__(self):
        """Méthode appelée lors d'une conversion de l'objet en chaîne"""
        return "Agent {0}, matricule {1}".format(self.nom, self.matricule)
```

Les fonctions utiles ici sont *issubclass* et *isinstance*:

```python
>>> issubclass(AgentSpecial, Personne) # AgentSpecial hérite de Personne
True
>>> isinstance(agent, Personne) # Agent est une instance héritée de Personne
True
```

en cas, d'hériatege multiple, on cherche d'abord les méthodes dans maclasse1 puis dans maclass2 :

```python
class MaClasseHeritee(MaClasseMere1, MaClasseMere2):
```

# Lecture et écriture dans un fichier

Mot clef : "with"

```python
with open('fichier.txt', 'r') as mon_fichier:
	texte = mon_fichier.read()

```

## Pickle

Utiliser pour sauvegarder des variables dans un fichier.

```python
with open('donnees', 'wb') as fichier:
	mon_pickler = pickle.Pickler(fichier)
	mon_pickler.dump(score)
with open('donnees', 'rb') as fichier:
	mon_depickler = pickle.Unpickler(fichier)
	score_recupere = mon_depickler.load()
```


# Tri

```python
sorted(list) #renvoie une nouvelle liste
list.sort() #trie la list inplace
```

On peut aussi trier avec des clef particulières :

```python
sorted(etudiants, key=lambda colonnes: colonnes[2])
[
    ('Thomas', 11, 12), 
    ('Charles', 12, 15), 
    ('Damien', 12, 15), 
    ('Clément', 14, 16),
    ('Oriane', 14, 18)
]
sorted(etudiants, key=lambda etudiant: etudiant.moyenne) #si etudiant est un obj avec un attribut moyenne
```

idem mais en plus efficace :

```python
from operator import itemgetter #pour une liste de tuple
sorted(etudiants, key=itemgetter(2))
from operator import attrgetter #pour une liste d'objet
sorted(etudiants, key=attrgetter("moyenne"))
sorted(etudiants, key=attrgetter("age", "moyenne")) #idem avec plusieurs critères
```

L'option reverse = True pour le tri dans l'ordre décroissant :

```python
inventaire.sort(key=attrgetter("quantite"), reverse=True)
sorted(inventaire, key=attrgetter("prix"))
```

# Les méthodes spéciales

### La destruction d'un object :

* fin d'une fonction ou du champ de l'obj
* del obj
* fin de l'execution du programme

```python
def __del__(self):
        """Méthode appelée quand l'objet est supprimé"""
        print("C'est la fin ! On me supprime !")
```

### Autre

```python
 def __repr__(self): #ce que print(obj) renvoie
 def __str__(self):#ce que str(obj) renvoie
 def __getattr__(self, nom):#ce que obj.nom renvoie quand obj.nom n'existe pas
 def __setattr__(self, nom):#ce que obj.nom fai quand l'attribu est modifié
 def __delattr__(self, nom):#ce que obj.nom fai quand l'attribu est supprimé

```



```python
def __getitem__(self, indice):
	#remplace elmt[indice]
```

# Autres infos intérresssante :

* cx_Freeze permet de créer des fichiers pythons standalone cross-platform assez facilement. Il suffit de compiler ses sources puis de faire cx_Freeze monichier.py ou python setup.py build avec dans setup.py :

  ```python
  """Fichier d'installation de notre script salut.py."""

  from cx_Freeze import setup, Executable

  # On appelle la fonction setup
  setup(
      name = "salut",
      version = "0.1",
      description = "Ce programme vous dit bonjour",
      executables = [Executable("salut.py")],
  )
  ```

* convention :

  ```python
  # Oui
      if objet is None:
          ...

  # Non
      if objet == None:
          ..
          
  # Oui
      if isinstance(variable, str):
          ...

  # Non
      if type(variable) == str:
          ...
  def MaClasse:
     def ma_fonction():
     mon_attribut = 1
  ```

# Debugging

```python
from pdb import set_trace as bp

code
code
pb()
code
code
```

## JSON

Permet de loader et stocker des sequences dans des fichiers facilement.

```python
import json
with open('hello.txt', 'w') as f:
	f.write(json.dumps(mydict()+ '\n'))
	mydict2 = json.loads(f.read())
```



## tdqm

Package pour visualizer l'évolution d'une boucle for dans la console (pratique)

```python
import tdqm
for i in tqdm(test_indexes, total = len(test_indexes)):
    code
```


# argparse

```python
import argparse
parser = argparse.ArgumentParser(description='Denoise options')
parser.add_argument('-l', '--logdir', required=True, help='directory of model used')
parser.add_argument('-g',"--gpu",  default=0)
parser.add_argument('-f', '--file',  default='/home/laurent/dataset3/train/exr/livingroom-back_Cam015_rgb_0005.exr')
parser.add_argument('-e', '--epoch',  default=100, type=int)
cmd_opt = parser.parse_args()
print(cmd_opt)
```

# Multiprocessing

Focusing on simple things, embarrassingly parralel for loops such as :

```python
for i in inputs:
    results[i] = processInput(i)
# now do something with results
```

```python
from joblib import Parallel, delayed
import multiprocessing
    
# what are your inputs, and what operation do you want to 
# perform on each input. For example...
inputs = range(10) 
def processInput(i):
	return i * i

num_cores = multiprocessing.cpu_count()
    
results = Parallel(n_jobs=num_cores)(delayed(processInput)(i) for i in inputs)
```

Note that processInput has to be pickable (i.e can't be define in a class, or a closure). If you can't avoid it, you can do :

```python
def NewprocessInput(dataset, index):
    return dataset.processInput(index
```

[![Analytics](https://ga-beacon.appspot.com/UA-91308638-2/github.com/ThibaultGROUEIX/python_tuto/python_tuto.md?pixel)](https://github.com/ThibaultGROUEIX/python_tuto/)