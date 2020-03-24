![](https://github.com/thierryseegers/DevCommeLesPros-2020-Projet/workflows/Test%20master/badge.svg)

# DevCommeLesPros-2020-Projet

Modèle de départ pour le projet de programmation à effectuer en groupe de deux ou trois étudiants. Vous n'êtes pas dans l'obligation de garder exactment les mêmes binômes que pour les exercices précédents.

# Objectif

Le site [LinkedIn](https://linkedin.com) est un réseau social servant de rapprochement et de moyen de contact entre des entreprises, des demandeurs d'emploi et d'anciens collègues travail.
Vous avez à créer un programme qui simule cette plateforme.

# Spécifications fonctionelles

Sur cette platforme, on distingue trois profils d'utilisateur avec des besoins propres. Les entreprises, les chercheurs d'emploi et les employés.

## Fonctionalités pour une entreprise

- [ ] Créer un profil
    - [ ] Nom
    - [ ] Code postal
    - [ ] Adresse mail
- [ ] Supprimer un profil
- [ ] Créer le profil d'un poste à pourvoir
    - [ ] Titre
    - [ ] Compétences
- [ ] Supprimer le profil d'un poste pourvu
- [ ] Rechercher parmi les chercheurs d'emploi pour des profils qui correspondent à un poste à pourvoir
    - [ ] Recherche par compétences
    - [ ] Recherche par compétences et code postal

## Fonctionalités pour un chercheur d'emploi

Pour un chercheur d'emploi, un bon moyen d'entrer en contact avec une entreprise qui nous intéresse est grâce à une personne que l'on connaît déjà (un(e) ancien(ne) collègue de travail) qui travaille présentement pour cette entreprise.

Lorsqu'un checheur d'emploi est embauché, son profil transitionne vers «employé».

- [ ] Créer un profil
    - [ ] Nom
    - [ ] Prénom
    - [ ] Adresse mail
    - [ ] Code postal
    - [ ] Compétences
    - [ ] Ancien(ne)s collègues de travail parmi les personne employés
- [ ] Modifier un profil
    - [ ] Ajouter des compétences
    - [ ] Ajouter un(e) ancien(ne) collègue de travail
    - [ ] Modifier le code postal
- [ ] Transitionner le profil de «chercheur d'emploi» à un profil «employé»
- [ ] Supprimer un profil
- [ ] Rechercher parmi les les postes à pourvoir qui correspondent au profil du chercheur d'emploi
    - [ ] Recherche par compétences
    - [ ] Recherche par compétences et code postal
    - [ ] Résultats
        - [ ] Titre du poste
        - [ ] Nom de l'entreprise
        - [ ] Adresse mail de l'entreprise
        - [ ] Code postal de l'entreprise
- [ ] Rechercher parmi les anciens collègues
    - [ ] Recherche par entreprise
    - [ ] Recherche par compétence et entreprise
    - [ ] Résultats
        - [ ] Nom du (de la) collègue
        - [ ] Adresse mail du (de la) collègue

## Fonctionalité pour un employé

C'est bien d'être à l'emploi mais pour diverses raisons il peut arriver qu'on veuille quand même s'informer sur les postes à pourvoir pour trouver un travail plus rémunérateur, plus près de chez soi, etc.

Lorsqu'un un employé quitte ou perd son emploi et est en recherche d'emploi, son prfil transitionne vers «checheur d'emploi».

- [ ] Créer un profil
    - [ ] Nom
    - [ ] Prénom
    - [ ] Adresse mail
    - [ ] Code postal
    - [ ] Compétences
    - [ ] Ancien(ne)s collègues de travail parmi les personne employés
    - [ ] Entreprise
- [ ] Modifier un profil
    - [ ] Ajouter des compétences
    - [ ] Ajouter un(e) ancien(ne) collègue de travail
    - [ ] Modifier le code postal
    - [ ] Modifier l'entreprise
- [ ] Transitionner le profil «employé» vers «chercheur d'emploi»
    - [ ] Les employé(e)s de l'entreprise quittée s'ajoute automatiquement à liste des ancien(ne)s collègues de travail
- [ ] Supprimer le profil
- [ ] Rechercher parmi les les postes à pourvoir qui correspondent au profil de l'employé
    - [ ] Recherche par compétences
    - [ ] Recherche par compétences et code postal
    - [ ] Résultats
        - [ ] Titre du poste
        - [ ] Nom de l'entreprise
        - [ ] Adresse mail de l'entreprise
        - [ ] Code postal de l'entreprise
- [ ] Rechercher parmi les anciens collègues
    - [ ] Recherche par entreprise
    - [ ] Recherche par compétence et entreprise
    - [ ] Résultats
        - [ ] Nom du (de la) collègue
        - [ ] Adresse mail du (de la) collègue

# Spécifications de conception

## Interface

Ce programme sera lancé à l'invite de commandes.
L'utilisateur naviguera les divers fonctionalités grâce à une arborescence de menu affichée à l'écran. Quelques exemples :

```
*** Bienvenu sur LuminIn, le site des pros ***

* Menu principal *

Vous êtes :
1. Une entreprise
2. Un employé
3. À la recherche d'un emploi

Votre choix ('q' pour quitter) : 1
```

```
*** Bienvenu sur LuminIn, le site des pros ***

* Menu entreprise *

Vous voulez :
1. Créer le profil de votre entreprise
2. Créer le profil d'un poste à pourvoir
3. Supprimer une annoce d'un poste maintenant pourvu
4. Faire une recherche parmi les chercheurs d'emploi

Votre choix ('q' pour quitter, 'p' pour menu précédent) : 
```

## Format de la base de données

Les tables de la base de données suivent le même format que la table utilisée dans l'exercice 4 (`groupe.csv`) où les champs sont séparés par des virgules. Si un champ contient plusieurs valeurs, celles-ci sont séparées par des points-virgules. 

À chaque tuple dans une table est assigné une clé primaire avec un numéro unique dans cette table. Aussi, certains attributs peuvent être des clés étrangères.

Quelques exemples :

### Table d'entreprise

```
id,nom,code postal,mail
1,Disney,77700,walt@disney.com
2,Google,75009,emplois@google.com
```

### Table de postes

L'attribut `entreprise` est une clé `id` de la table des entreprises.

```
id,titre,competences,entreprise
1,acteur,comedie;gag;1
2,developpeur,C;SQL;Python,2
```

### Table de chercheur d'emploi

L'attribut `collegues` est une liste de clé `id` de la table des employés.

```
id,nom,prenom,mail,code postal,competences,collegues
1,Duck,Donald,donal.duck@canardville.gov,77700,comedie;gag,2
2,Pignon,Francois,pignouf@gmail.com,75020,C;SQL;Python,
```

### Table des employés

L'attribut `collegues` est une liste de clé `id` de la table des employés.
L'attribut `entreprise` est une clé `id` de la table des entreprises.

```
id,nom,prenom,mail,code postal,competences,collegues,entreprise
1,Untel,Michel,m_untel@google.com,13010,C++;Python;,,2
2,Mouse,Mickey,mickey@mickeyville.gov,77700,comedie,3,1
3,Mouse,Minnie,minnie@mickeyville.gov,77700,comedie;chant,2,1
```

# Instructions de travail

Suivez les instructions de départ et les instructions de travail de l'exercice 4 avec deux exceptions :
1. Vous pouvez travailler en groupe de deux ou trois.
1. La personne qui approuve et fusionne un «Pull Request» ne doit pas être la personne qui a ouvert le «Pull Request». C'est-à-dire que si Alice pousse sa branche vers GitHub et ouvre un «Pull Request» pour demander de la fusionner à la branche `master`, ce doit être Bob ou Charlie qui approuvera et fusionnera.

## Étapes de développement

tag pre-alpha, alpha, beta, 1.0, 

release 1.0

## Modules/Bibliothèques

Vous serez tentés d'essayer d'écrire ce programme de façon monolithique avec un gros fichier `main.c` qui fait tout.
Résistez à cette tentation !
La collaboration entre vous serait très difficile.

Travaillez ensemble pour déterminez de quels modules vous aurez besoin ainsi que leurs responsabilités (manipulation des DBs, fonctionalités entreprise/employé/chercheur, interface/menus, documentation, etc.), Déterminez aussi quels sont les dépendances entre les modules et quelles sont les fonctions requises des modules. Ensuite, vous pourez travaillez plus individuellement aux tâches que vous vous serez assignées sachant qui a besoin de quoi.

> Mais si mon module doit appeller une fonction d'une autre module qui n'existe pas encore ?

Rappellez-vous des exercices précédents où vous aviez à implémenter des fonctions «vides». Ces fonctions ou méthodes s'appellent des [bouchons](https://fr.wikipedia.org/wiki/Bouchon_(informatique)) (ou [stub](Method_stub) en anglais). Ces bouchons servent justement à deux choses :

1. Faire en sorte qu'un module A qui dépend de la fonction d'un module B puisse être développé et compilé _comme si_ la fonction était implémentée. Bien sûr, au début la fonction retourne une fausse valeur mais on peut continuer le développement du module A quand même en faisant semblant.
2. On peut écrire des tests avant même que la fonction soit implémentée. Connaissant la signature d'une fonction et ses responsabilités, on peut écrire des tests qui en vérifient le bon fonctionnement. Écrire des tests à l'avance est d'ailleurs une très bonne aide pour comprendre à quoi l'implémentation d'une fonction doit répondre : cas généraux, cas spéciaux, cas d'erreurs, etc.


## Tests

Sans tests, vous n'aurez pas confiance ni en votre code ni en votre programme.

En plus du programme qui sera votre application, écrivez en parallèle un autre programme. Un programme de tests qui rassemblera tout les tests que vous écrirez pour confirmer que vos modules opèrent correctement.

> Mais si mon module dépend d'une fonction d'une autre module qui n'est pas encore implémentée ?

Écrivez quand même vos tests quitte à les laisser commentés temporairement ! N'attendez pas que vos coéquipiers aient tout terminé pour commencer à travailler sur votre module. Vous perdriez un temps précieux.

### Tests unitaires et tests d'intégration

Durant la première phase de développement, les tests que vous écrirez seront plutôt des test unitaires. C'est-à-dire des tests qui testent les divers modules en isolation.

Une fois que votre programme commence à se tenir debout vous pourrez commencer à le tester dans son ensemble, à le lancer à l'invite de commandes et l'utiliser comme un utilisateur lambda le ferait.

### Intégration continue

Tout comme pour les exercices 3 et 4, ce projet est configuré [1] de telle sorte qu'en ouvrant un «Pull Request», GitHub lance une machine virtuelle Ubuntu qui clone votre dépôt et exécute la commande `make check` à l'invite de commande. De ce fait, assurez-vous que la cible `check` de votre `makefile` dépende de votre programme de test et le lance.

Si la vérification du service d'intégration continu venait à échouer, il vous incombe d'apporter les modifications nécéssaires à votre branch (toujours en faisant `add`, `commit` et `push`) pour rectifier la situation.

Essentiellement, je vous demande de travailler comme pour les exercices 3 et 4 en suivant leurs [instructions de travail](https://github.com/thierryseegers/DevCommeLesPros-2020-Ex3#instructions-de-travail). Seulement, cette fois-ci, c'est vous qui écrirez les tests.


[1] Curieux de savoir comment ? Ouvrez le fichier `.github/workflows/test-pull-request.yml`. Pour en savoir plus, cliquez [ici](https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow).

## Documentation


### Documentation pour les ingénieurs


### Documentation pour les utilisateurs

Modifiez ce `README` que vous lisez présentement et écrivez le manuel d'instructions de votre programme. Décrivez-y les fonctionalités implémentés ainsi que, peut-être, les erreurs de manipulation à ne pas commettre. Ce sera le «[tuto](https://fr.wikipedia.org/wiki/Tutoriel)» de votre programme.

Ici, vous pouvez laisser parler votre créativité. Comment aimeriez-_vous_ qu'on vous apprenne à utiliser ce programme ? Par exemple, si vous vous sentez l'âmes de comédiens, faites un tuto vidéo.

# Évaluation

- 
- Bonne utilisation du service d'intégration continu.
    - La cibe `check` dans le `makefile` lance le programme de test.
    - Les «Pull Request» reçoivent la confirmation du service d'intégration continu que tout s'est bien passé.

Vous avez tout bon ? Ça vaut 17 sur 20. Comment gagner d'autres points ? Continuez de lire...

# Les extras

Chacun de ces extras vaut 1 point sur 20. Il vous permettront donc d'atteindre 18, 19 ou 20 sur 20.

*Ne tentez ces extras que si vous avez atteint l'objectif principal ! Ils ne valent aucuns points si votre programme ne répond pas aux exigences de base de votre «client».*

À chaque extra correctement implémenté, incrémentez la version mineure de votre programme (par ex. «1.1» pour le premier extra, «1.2» pour le deuxième extra, etc.) comme décrit dans la section [Étapes de développement](#étapes-de-développement).

Voici une liste d'extras à envisager. Je les ai mis dans un ordre qui, selon moi, est du plus facile au plus difficile.

1. Le programme produit un [journal](https://www.dropbox.com/scl/fi/12l29vxc1v4z74wum6ay3/D-velopper-comme-les-pros.paper?dl=0&rlkey=gbd3b2ajnlo93wz6xvsph5bcu#:uid=877002050135560344832464&h2=D%C3%A9boguer-par-journal) de toute les opérations exécutées et les informations dans le journal persiste entre les utilisations du programme (c'est-à-dire que le fichier servant de journal n'est pas remis à zéro quand vous lancez le programme).
1. Un utilisateur, que ce soit une entreprise ou une personne, s'authentifie avec un mot de passe (ne convervez pas le mot de passe en clair dans la table, utilisez une [fonction de hachage](https://fr.wikipedia.org/wiki/Fonction_de_hachage_cryptographique)).
1. Gardez une historique d'emploi pour chaque personne et utilisez cette historique lors des recherche parmi les anciens collègues, c'est-à-dire «qui travaille *ou a déjà travaillé* à telle ou telle entreprise.
1. Compressez toute la base de données par un codage de Huffman. Les fichiers sur le disque sont compressés. Ils sont décompressés en mémoire, modifiés au file des opérations et au moment de quitter le programme ils sont recompressés et écrit sur le disque. Les fichiers décompressés n'apparaîssent jamais sur le disque.
1. Écrivez un programme de test qui lance votre programme d'application, exécute certaines commandes et vérifie que tout s'est bien déroulé et que la base de données contient les bonnes informations.
1. Utilisez une [véritable base de données SQL](https://sqlite.org/cintro.html) plutôt que des fichers `.csv` (cet extra n'est pas compatible avec l'extra 3).

Vous avez une autre idée d'extra ? Faites-la approuver par votre «client» au préalable.