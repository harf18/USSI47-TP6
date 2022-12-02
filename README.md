# TP6 : Exceptions & Fichiers

### Objectifs
Utiliser les Exceptions, créer, ouvrir, lire et écrire dans des fichiers

### Prérequis
- Cloner le projet sur votre poste dans le repertoire de votre choix
- Ouvrir le projet :
	- Sur l'écran d'accueil d'IntelliJ, cliquer sur **Open**
	- Sélectionner le dossier **tpX-xxx** qui a été copié depuis github puis cliqué sur **OK**.
	- Le projet s'ouvre
	- Allez vérifier que le SDK est bien sélectionné dans **File > Project Structure** onglet **Project**

### Utilisation de GIT

- Créer une nouvelle branche **prenomNom**
- Faire **1 commit** par exercice (sauf exercice 0)
- Ouvrir **une seule** *pull request* sur github et **ne pas** la fermer/merger !!


> Si vous ne l'avez pas encore fait, pensez a créer une nouvelle branche **prenomNom**

### Exercice 1

- Créer une classe **Division**
- Ecrire une méthode ``` public double division1(int a, int b)``` qui retourne la division de a par b **sans gérer d'exception** 
- Dans **Execute** compléter la méthode **exercice1()** pour appeler division1() et afficher le résultat avec a=10 et b=0
- Executer la méthode main() (qui execute la méthode exercice1()), noter dans un coin ce qui se passe...

> Pensez a faire votre 1er commit !!  

### Exercice 2
- Dans la méthode main(), commenter l'appel de exercice1()
- Dans la classe **Division**, écrire une méthode avec la signature ``` public double division2(int a, int b)``` qui calcule la division de a par b et qui capture l'exception **exacte** levée à l'exercice 1 et qui la traite en affichant un message d'erreur directement dans la méthode division2().
- Dans **Execute**, compléter la méthode **exercice2()** pour appeler division2() et afficher le résultat avec a=10 et b=0
- Executer la méthode main() (qui execute la méthode exercice2())

> Pensez a faire un commit !!

### Exercice 3

On vous demande maintenant de forcer les développeurs qui vont utiliser votre méthode de division à gérer les divisions par zéro. 
Or, l'ArithmeticException est *Unchecked*, c'est pour ça que vous avez pu écrire division1 sans être forcé de capturer d'exception. 
Il faut donc qu'en cas de division par zéro, une exception *checked* soit levée comme, par exemple, **IOException** (on ne créé pas encore sa propre classe d'exception) : 

- Dans la classe **Division**, écrire une méthode ``` public double division3(int a, int b)``` qui calcule la division de a par b et qui capture l'exception **exacte** levée à l'exercice 1 et qui leve une exception de type **IOException** 
- Dans **Execute**, compléter la méthode **exercice3()** pour appeler division3() et afficher le résultat avec : avec a = 10 et b = 0;
- Executer la méthode **exercice3()** dans le main()

Laquelle des 3 solutions vous parait la plus pertinente ? Mettre en commentaire au-dessus de la méthode division1(), division2() ou division3() pour expliquer.

> Pensez a faire un commit !!

### Exercice 4

Le but est d'écrire un fichier texte *etudiants.csv* contenant une liste d'étudiants du type : "INE","Nom","Prenom"

- Créer une classe **Etudiants** avec 3 attributs : ine, nom, prenom 
  - Ajouter le/les constructeurs et accesseurs que vous jugez pertinent. 
  - Surcharger également la méthode *toString()* pour qu'elle retourne la chaine "INE","Nom","Prenom"  + retour à ligne. Respecter les guillemets et virgule. Ine, Nom, Prenom représentent les VRAIS valeurs des attributs de l'étudiant (Pour afficher un guillement dans une chaine, il faut le préfixer... cours 1). Pensez au retour à la ligne en fin de ligne.
- Créer un classe **EtudiantService**
  - Ajouter une méthode avec la signature ```public void sauve(Etudiant[] etudiants, String cheminCompletFichier) throws IOException``` et écrivez le code pour écrire le fichier à l'aide des classes du package java.nio.file. Si le fichier existe déjà, détruiser le avant de le recréer. Vous pouvez écrire le fichier ligne par ligne, en utilisant la méthode toString() ci dessus.
- Dans **Execute**, completer la méthode **exercice5()** pour créer quelques étudiants et générer le fichier. 
- Executer la méthode **exercice5()** dans le main()

> Pensez a faire un commit !!

### Exercice 5
- Dans la classe **EtudiantService**
	- Ajouter une méthode avec la signature ```public Etudiant[] charge(String cheminCompletFichier)  throws IOException```  et écrivez le code pour lire le fichier créer a l'exercice 6 à l'aide des classes du package java.nio.file. Cette méthode doit convertir chaque ligne et créer un objet Etudiant à partir des données extraitent et retourner un tableau d'Etudiant. Vous pouvez utiliser des méthodes de découpage et modification de chaine pour découper chaque chaine et supprimer les caractères inutiles.
	- Ajouter une méthode *main()* quand laquelle vous lirez le fichier et afficherez le nom de chaque client importé.
- Dans **Execute**, completer la méthode **exercice6()** lire le fichier et afficher le nom des étudiant importés. 
- Executer la méthode **exercice6()** dans le main()

> Pensez a faire un commit !!

### Exercice 6

- Créer une nouvelle classe **FactorialNegativeArgumentException** qui hérite de Exception avec un constructeur avec la signature ```public FactorialNegativeArgumentException(long val)```  et qui appelle le constructeur Exception(String s) de sa classe mère pour afficher le message "Le nombre *val* est négatif"
- Créer une nouvelle classe **FactorialTooLargeArguementException** qui hérite de Exception avec un constructeur avec la signature ```public FactorialTooLargeArguementException(long val)```  et qui appelle le constructeur Exception(String s) de sa classe mère pour afficher le message "Le nombre *val* est trop grand"
- Créer une nouvelle classe **Factorielle**
- Créer une méthode avec la signature ```public long calcul(String val)``` qui doit calculer la factorielle en gérant les problèmes suivants et pour chacun lever une exception qui doit être capturée par le code appelant
	- val est null, lever alors l'exception **IOException** en passant le message "le paramètre *val* est null"
	- val doit être converti en long (Aller voir la documentation de Long.parseLong(String s)). Si val n'est pas un long, forcer la capture d'une exception en  levant l'exception **IOException** en passant le message "Le paramètre *val* n'est pas un nombre" (Comme  pour l'exercice 3, on est obligé de faire ça car NumberFormatException est unchecked)
	- val est négatif, lever l'exception **FactorialNegativeArgumentException**
	- val est supérieur à 20, lever l'exception **FactorialTooLargeArguementException**

> **Pensez a factoriser votre code !** Par exemple créez 4 méthodes *private* qui sont appelées par *calcul()* et qui font les tests et la conversion String en long et qui levent des exceptions. calcul() sera très compact et plus lisible et chaque "logique" sera séparée dans sa méthode

- Dans **Execute**, completer la méthode **exercice4()** avec les valeurs suivantes et gérer les exceptions pour chaque tests (un try/catch par test) et afficher le message retourné par l'exception.
	- null
	- "Hello"
	- "-1"
	- "21"
	- "10"
- Executer la méthode **exercice4()** dans le main()

> Pensez a faire un commit !!
