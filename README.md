# ![](images/logo.jpeg)

# Développement d'applications avec IHM

### IUT Montpellier-Sète – Département Informatique

* [**Support de cours**](https://gitlabinfo.iutmontp.univ-montp2.fr/ihm/ressources)
* **Enseignants:**
    * [Sophie Nabitz](mailto:sophie.nabitz@univ-avignon.fr),
      [Cyrille Nadal](mailto:cyrille.nadal@umontpellier.fr),
      [Nathalie Palleja](mailto:nathalie.palleja@umontpellier.fr),
      [Xavier Palleja](mailto:xavier.palleja@umontpellier.fr),
      [Petru Valicov](mailto:petru.valicov@umontpellier.fr)
* Le [forum Piazza](https://piazza.com/class/lfmbartihpv60i) de ce cours pour poser vos questions
* [Email](mailto:petru.valicov@umontpellier.fr) pour une question d'ordre privée concernant le cours.

## TP 3 : gestionnaires d'événement et propriétés

### Exercice 1 - Un peu d'arithmétique (issu du sujet d'examen à l'IUT d'Aix-Marseille Université en 2021)

On s'intéresse à un petit programme qui permet d'afficher des problèmes arithmétiques et qui affiche combien de réponses
sont justes. Voici une présentation de l'application en deux étapes :
Étape 1 :

![Etape 1](images/Etape1.png)


Étape 2 :

![Etape 2](images/Etape2.png)


Le contrôle que vous aurez à utiliser est
un [ComboBox](https://openjfx.io/javadoc/18/javafx.controls/javafx/scene/control/ComboBox.html), qui permet de choisir
le nombre d'exercices à afficher. Veuillez regarder la documentation de cette classe pour savoir comment l'utiliser
avant de poursuivre.

Notamment, notez l'utilisation de la
propriété [valueProperty](https://openjfx.io/javadoc/18/javafx.controls/javafx/scene/control/ComboBoxBase.html#valueProperty())
et [selectedItemProperty](https://openjfx.io/javadoc/18/javafx.controls/javafx/scene/control/SelectionModel.html#selectedItemProperty()),
qui permet de savoir quelle est la valeur actuelle de la ComboBox. Quand un item est sélectionné, la propriété est mise
à jour pour représenter l'item sélectionné.

1. Complétez la méthode `start()` de la classe `AppMaths` et créez une fenêtre rassemblant à celle de l'étape 1 pour que
   la `ComboBox` affiche 6, 9, 12 et 15 comme choix possibles.
2. Complétez la classe `LigneExercice`afin qu'elle modélise chacune des lignes d'exercices (image de l'étape 2). Notez que parmi les attributs de cette classe, il y a un objet de type `Exercice`.
3. Modifiez le code de la classe `AppMaths` afin de prendre en compte le choix de l'utilisateur et mettre à jour la fenêtre de façon à ce qu'elle ressemble à celle de l'étape 2. Pour mettre à jour dynamiquement les exercices affichés en fonction du choix de l'utilisateur, on vous propose de suivre le processus suivant :
    * Ajouter un `ChangeListener` sur `valueProperty` de votre `ComboBox` afin que la méthode `changed()` de cet écouteur fasse le changement nécessaire
    * Dans la méthode `changed()`, vous devrez :
        * créer le nombre nécessaire de lignes d'exercices et les ajouter dans un conteneur `VBox` (pensez à nettoyer au préalable les exercices qui seraient déjà dans la liste...) ;
        * ajouter dans le même conteneur un bouton de validation des résultats qui, pour moment, ne fera rien.

4. La classe `Exercice` vous est partiellement donnée. Elle génère un exercice avec son énoncé et sa solution. Ajoutez à cette classe une propriété `IntegerProperty solution` qui encapsulera la solution à l'énoncé. Ajoutez un _getter_ sur cette propriété.

5. Ajoutez une propriété `BooleanProperty correct` à la classe `LigneExercice`. Cette propriété devra permettre de savoir si la réponse fournie est correcte (c'est-à-dire correspond à la solution de l'exercice).

6. Ajoutez dans la classe principale `AppMaths` un gestionnaire d'événement sur le bouton de validation. Il devra afficher une nouvelle fenêtre indiquant le nombre de réponses correctes. Pour cela, vous utiliserez la classe [Alert](https://openjfx.io/javadoc/18/javafx.controls/javafx/scene/control/Alert.html) de JavaFX. La fonction `showAndWait()` vous permettra de rendre la fenêtre bloquante : tant que l'utilisateur n'a pas validé, il ne pourra pas revenir sur la fenêtre principale.

7. Dans votre version actuelle, lorsqu'un utilisateur choisit un nombre d'exercices, l'intégralité de la liste des exercices est régénérée. Modifiez le code de façon à ce qu'un maximum des exercices incorrectement répondus soit régénéré (si le nombre d'exercices incorrects est supérieur au choix `n` de la `ComboBox`, on affichera les `n` premiers exercices incorrects.