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
- <code>requirements.txt</code>: Fichier contenant les libairies nécéssaires à l'exécution du projet
- src:
  - <code>answers(2).json</code>: Fichier source contenant des textes annotés au format Squad ( Contexte, Question, Réponse), nécéssaire pour l'évaluation des modèles
  - <code>question.csv</code>: Fichier source contenant les questions à poser, le mot clé à rechercher, ainsi que l'indicateur associés.
  - <code>bornes.csv</code>: Fichier csv contenant les bornes spécifiques aux indicateurs de SISPEA.
  - <code>results.csv</code>: Fichier csv contenant les résultats des rapports testés.
  - <code>indic_metric.csv</code>: Fichier csv contenant les résultats des rapports testés mais triés par indicateurs.
  - <code>collect_2023.csv</code>: Ficier csv contenant les liens vers les RPQS récupérés en ligne, ainsi que la ville, l'année et la compétence associée.
  - <code>ville_df.csv</code>: Ficier csv contenant les noms et codes INSEE des communes de France. On l'utilise pour la collecte de RPQS.
  - <code>data_sispea.7z</code>: Zip contenant toutes les extraction depus sispea sur les données entre 2016 et 2021, sur l'ensemble du territoire. Nécessaires pour l'exécution des codes "data_sispea" et "scrap_test". 
- evaluations_modeles:
  - <code>eval_etalab_rpqs.ipynb</code>: Jupyter Notebook permettant d'évaluer le modèle d'etalab, à partir d'un fichier de données étiquetées
  - <code>flan-t5-base.ipynb</code>: Jupyter Notebook permettant d'évaluer le modèle flan-t5-base, à partir d'un fichier de données étiquetées
  - <code>flan-t5-large.ipynb</code>: Jupyter Notebook permettant d'évaluer le modèle flan-t5-large, à partir d'un fichier de données étiquetées
  - <code>flan-t5-xl.ipynb</code>: Jupyter Notebook permettant d'évaluer le modèle flan-t5-xl, à partir d'un fichier de données étiquetées
  - <code>flan-t5-xxl.ipynb</code>: Jupyter Notebook permettant d'évaluer le modèle flan-t5-xxl, à partir d'un fichier de données étiquetées
- fonctions_generales:   
  - <code>Fonction_finale.ipynb</code>: Jupyter Notebook permettant l'éxécution du code (usage, test du programme) *(point de vue: utilisateur du programme)*
  - <code>Fonction_finale_génerique.ipynb</code>: Code identique à celui ci-dessus, mais des indications en plus pour généraliser à d'autres cas d'usages *(point de vue: développeur pour un autre cas d'usage)*
  - <code>data_sispea.ipynb</code>: Jupyter Notebook permettant d'éxecuter le code, puis de comparer les réponses prédites avec les valeurs présentes dans sispea, pour obtenir des métriques de performance   *(point de vue: développeur sur ce cas d'usage)*
  - <code>data_indic.ipynb</code>: Idem que le fichier précedent, mais calcule des métriques par indicateur et non par PDF.
  - <code>scrap_test.ipynb</code>: Fonction_finale, mais qui va collecter les RPQS en ligne automatiquement.
  - <code>collect_RPQS.ipynb</code>: Méthode de web scraping et crawling permet de collecter en masse les RPQS en logne et renvoie un fichier excel avec le nom de la collectivité, l'année et la compétence(AC ou EP)
- rf :
   - <code>rf.7z</code>: fichier zip contenant otu les csv des résultats finaux des 50 pdf testés 
- scrib :
  - <code>collect_scrib.pdf</code>: Tuto pour l'éxecution du notebook collect_RPQS.ipynb
  - <code>sspgit.pdf</code>: Tuto pour créer un service de jupyter sur le sspcloud lié à un dépôt git
  







