---
layout: default
lang: fr
title: Interface utilisateur GitHub
permalink: /fr/plan/interface-utilisateur-github/
homologue: /outline/github-user-interface/
parent: Plan
nav_order: 1
---

# Introduction à l’interface utilisateur de GitHub

## Créer un répertoire

Un **répertoire** Git est une façon d’organiser des données utilisée pour suivre les modifications apportées à des fichiers au fil du temps. Un répertoire est sauvegardé dans un dépôt avec les fichiers du projet auquel il est associé, dans un dépôt masqué dont le nom porte l’extension « .git ». Les informations concernant le répertoire, les modifications apportées aux fichiers dans le dépôt, et les versions précédentes du répertoire sont toutes entreposées dans ce dépôt masqué, de telle sorte qu’elles restent accessibles sans pour autant compliquer la navigation à l’intérieur du répertoire.

Vous pouvez créer un répertoire à partir de l’[interface web GitHub](https://github.com/new), ou sur votre propre ordinateur en utilisant GitBash ou le terminal.

Commencez par créer un nouveau répertoire à partir de l’interface web.

Allez sur votre profil GitHub. Ensuite, cliquez sur « Répertoires », puis sur le bouton vert « Nouveau », en haut à droite de votre écran. Vous pouvez aussi créer un nouveau répertoire en cliquant sur le symbole « + » en haut à droite de l’en-tête du site web.

![Adding a new repository in the GitHub interface]({{ '/screenshots/new_repository.png' | relative_url }})

Au moment de créer un répertoire, vous devrez indiquer certaines informations :

Nom du répertoire : donnez un nom à votre nouveau répertoire.

Description (optionnelle) : si vous le souhaitez, décrivez brièvement le contenu de votre répertoire.

Public ou privé :

*   public : tout le monde peut voir votre répertoire en ligne. Seule les personnes avec votre autorisation peuvent y apporter des modifications.
*   privé : vous seul décidez qui peut voir et apporter des changements au répertoire.

Ajouter au répertoire :
*   un fichier _README_ : un fichier _README_ sert à décrire brièvement votre projet et ses contextes d’application, ainsi qu’à relever son utilité pour la communauté. Bien qu’il ne soit pas obligatoire de joindre un fichier _README_ à un projet, il est fortement suggéré de le faire.
*   des fichiers _.gitignore_ : l’extention « _.gitignore_ » indique à Git quels fichiers sont à ignorer au moment de prendre un instantané de votre projet. On la joint généralement à des fichiers de paramétrage ou contenant des informations personnelles.
*   une licence : bien qu’attribuer une licence d’utilisation à votre projet soit facultatif, il s’agit d’une étape importante dans la diffusion de celui-ci. Pour en connaître plus sur les licences d’utilisation, leurs avantages et leurs inconvénients, consultez [https://choosealicense.com/](https://choosealicense.com/).

Pour cet atelier :
*   créez un répertoire nommé « bonjour ! » ;
*   ajoutez-y une brève description ;
*   rendez le public ;
*   ajoutez-y un fichier _README_
*   attribuez-lui une licence _CreativeCommons_ ;
*   confirmez sa création.

![Create a new repository in the GitHub interface]({{ '/screenshots/create_new_repository.png' | relative_url }})

![HelloWorld repository in the GitHub interface]({{ '/screenshots/hello_world.png' | relative_url }})

Maintenant que vous disposez d’un répertoire, il est important que vous preniez connaissance de deux concepts de l’outil Git :
*   **branche principale (_main branch_)** : un répertoire Git peut être divisé en de multiples branches, lesquelles peuvent être modifiées indépendamment avant d’être fusionnées. Au moment d’être créé, un répertoire contient par défaut une seule branche, dite « principale ». Dans le cadre de cet atelier, vous travaillerez à partir d’une seule branche.
*   **instantané (_commit_)** : prendre un instantané des fichiers dans votre répertoire permet de sauvegarder et de suivre les modifications que vous y apportez, tout en conservant des métadonnées pertinentes comme le nom de l’auteur des modifications. Normalement, vous devriez voir que votre projet contient déjà un instantané de la création du fichier _README_.

## Mettre à jour les fichiers dans un répertoire

Apportez des modifications au fichier _README_ dans votre répertoire.

Cliquez sur le bouton avec une icône de crayon, en haut à droite du fichier. Git et GitHub fonctionnent avec la langue de balisage _Markdown_. Portez attention au caractère « # », placé devant le nom de votre fichier ; il s’agit de la balise utilisée pour identifier un titre : « # » pour les titres 1, « ## » pour les titres 2, et ainsi de suite. Vous pouvez prévisualiser le texte dans l’onglet « _Preview_ » pour vous assurer que la mise en page soit correcte.

![Editing a file in the GitHub interface]({{ '/screenshots/edit_file_1.png' | relative_url }})

En bas de la page se trouve un bouton « _Commit changes_ » (prendre un instantané des modifications). Appuyez sur ce bouton pour enregistrer les changements apportés au fichier. Il est recommandé d’annoter l’instantané, de façon à décire les modifications effectuées ; vous pourrez ainsi retourner à des versions antérieures de vos projets sur la base de ces informations.

Par exemple, annotez votre instantané en écrivant : « Ajout d’une description du projet dans le fichier _README_ ».

GitHub vous demande ensuite de choisir si vous souhaitez enregistrer l’instantané dans la branche principale de votre répertoire ou dans une nouvelle branche, dite « branche secondaire ». Il est recommandé de créer une branche secondaire pour tester les modifications apportées à un fichier avant de les fusionner avec la branche principale d’un projet ; mais aux fins de cet atelier, vous pouvez sauvegarder l’instantané de vos modifications dans la branche principale.

Voici un autre concept important à comprendre en utilisant Git :
*   **demande de tirage (_pull request_)** : une demande de tirage permet au propriétaire d’un projet d’appliquer des modifications apportées à des branches secondaires à la branche principale. Au moment de fusionner les branches d’un répertoire, vous devez faire une demande de tirage pour plus d’informations sur les demandes de tirage, consultez [https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

## Consulter l’historique d’un fichier

Il est possible de consulter l’historique des instantanés pris d’un fichier pour voir l’ensemble des modifications qui y ont été apportées. Cliquez sur le bouton « ... » à droite du nom de l’instantané pour lire son annotation.

![Viewing commit history in the GitHub interface]({{ '/screenshots/file_history.png' | relative_url }})

L’historique d’un fichier vous permet de voir en détails, pour chaque instantané, les modifications qui ont été faites, ce qui a été ajouté ou retiré, etc.

Le bouton « < > », à droite d’un instantané, vous permet de ramener votre fichier à l’état de cet instantané. Un bouton identique existe pour vous permettre de retourner aux états antérieurs d’un répertoire entier.

![Browsing commit history in the GitHub interface]({{ '/screenshots/browse_history.png' | relative_url }})

Ces fonctionnalités montrent le potentiel de Git et de GitHub, mais aussi l’importance de garder des traces de vos activités lorsque vous utilisez ces outils - surtout en contexte de collaboration.

## Ajouter un fichier dans un répertoire

![Adding a file in the GitHub interface]({{ '/screenshots/add_file.png' | relative_url }})

Vous pouvez ajouter un fichier dans un répertoire en cliquant sur le bouton « _Add file_ » en haut à droite de la liste des fichiers compris dans le répertoire. Vous pouvez ajouter un fichier de deux façons :

<ol type="a">
  <li><p>Créer un fichier : créez un nouveau fichier à partir de GitHub, en lui attribuant un nom et une extension de votre choix. Vous pouvez placer le nouveau fichier dans un sous-dossier en ajouter le nom du sous-dossier et « / » avant le nom du fichier.</p><p>Créez un fichier nommé « index.md ». Dans ce document, écrivez un titre 1 « Accueil » et un titre 2 « Bienvenue ».</p><p>Enfin, prenez un instantané de ces changements et annotez-le.</p><img src="{{ '/screenshots/edit_file_2.png' | relative_url }}" alt="Editing a file in the GitHub interface"></li>
  <li><p>Charger un fichier : chargez un fichier à partir de votre ordinateur. Une fois votre fichier chargé dans votre répertoire, prenez un instantané des modifications apportées.</p><img src="{{ '/screenshots/upload_file.png' | relative_url }}" alt="Upload a file in the GitHub interface"></li>
</ol>

Voici deux commandes Git que vous rencontrerez très probablement à mesure que vous utiliserez cet outil :

*   **Dupplication (_fork_)** : la commande de dupplication sert à sauvegarder une copie d’un répertoire GitHub créé par un autre utilisateur sur votre propre compte. Après avoir duppliqué un répertoire dans votre compte, vous en gagnerez le plein contrôle et pourrez le modifier sans entraîner de conséquence sur le répertoire originel.
*   **Clôner** : la commande de clônage sert à sauvegarder une copie d’un répertoire GitHub sur votre ordinateur. Elle permet de modifier vos fichiers à partir d’un outil autre que Git, puis d’appliquer ces modifications dans Git.

![git staging area]({{ '/screenshots/stage.png' | relative_url }})
