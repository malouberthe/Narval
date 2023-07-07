# Narval
Exctraction de données depuis des rapports PDF 
## Contexte et objectif

SISPEA (Systèmes d’Informations des Services Publics d’Eau et d’Assainissement) bancarise des données sur la tarification et la performance des services publics d’eau et d’assainissement. Les données concernent 39 indicateurs codifiés (https://www.services.eaufrance.fr/indicateurs/mise-a-jour).

Théoriquement, les collectivités ont pour obligation de saisir les valeurs de ces indicateurs dans SISPEA (saisie manuelle via formulaire en ligne). Dans les faits, certaines collectivités omettent cette étape. Ainsi, la représentativité des jeux de données publiés est de 50% en termes de services couverts et de 80% en termes de population française couverte.  

Les indicateurs et valeurs associées sont également décrits dans des RPQS (rapports sur les prix et la qualité des services), produits annuellement par chaque collectivité. Les RPQS sont mis en ligne soit sur l’application de SISPEA, soit sur le site des collectivités. Ainsi, les RPQS contiennent l'ensemble des valeurs des 39 indicateurs pour toutes les collectivités. Nous allons donc pouvoir y chercher les données manquantes en base de données. 

L’objectif de ce projet est de mettre en place un outil d’extraction de texte et de reconnaissane textuelle automatisée afin d’alimenter les données de SISPEA à partir des RPQS.

Prise en main du projet
----

Le projet a été réalisé dans un environnement Python 3.10.

  Téléchargement des librairies requises
  <code>pip install requirements.txt</code>

Contenu du repertoire
-----
- <code>requirements.txt</code>: fichier contenant les libairies nécéssaires à l'exécution du projet
- <code>Fonction_finale.ipynb</code>: Jupyter Notebook permettant l'éxécution du code (usage, test du programme) *(point de vue utilisateur du programme)*
- <code>Fonction_finale_génrique.ipynb</code>: Code identique à celui ci-dessus, mais des indications en plus pour généraliser à d'autres cas d'usages *(point de vue: développeur pour un autre cas d'usage)*
- <code>data_sispea.ipynb</code>: Jupyter Notebook permettant d'éxecuter le code puis de comparer les réponses prédites avec les valeurs présentes dans sispea *(point de vue: développeur sur ce cas d'usage)*
- <code>flan-t5-xl.ipynb</code>: Jupyter Notebook permettant d'évaluer un modèle, à partir d'un fichier de données étiquetées.
- <code>question.csv</code>: Fichier source contenant les questions à poser, le mot clé à rechercher, ainsi que l'indicateur associé
- <code>answers(2).json</code>:Fichier source contenant des textes annotés au format Squad ( Contexte, Question, Réponse), nécéssaire pour l'évaluation des modèles.








