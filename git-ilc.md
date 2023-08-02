---
layout: default
lang: fr
title: Interface de ligne de commande GitHub
permalink: /fr/plan/interface-ligne-commande-github/
homologue: /outline/github-command-line-interface/
parent: Plan
nav_order: 2
---

# Introduction à Git avec le terminal

## Synchroniser et configurer Git

Ouvrez GitBash ou votre terminal et naviguer jusqu’au dossier que vous souhaitez utiliser dans le cadre de l’atelier. Une fois à l’intérieur du dossier, entrez la commande :

Input
{: .label .label-green}
~~~
git config --list
~~~
Si votre système d’exploitation est MacOS et que vous n’avez jamais configuré Git auparavant, vous devriez voir apparaître le texte suivant :

Output
{: .label .label-yellow}
~~~ 
credential.helper=osxkeychain
~~~
Si votre système d’exploitation est Windows et que vous n’avez jamais configuré Git auparavant, vous devriez plutôt voir apparaître le message suivant :

Output
{: .label .label-yellow}
~~~
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager-core
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=main
~~~

Si le texte qui s’affiche à votre écran diffère des messages ci-dessus, c’est probablement que vous avez déjà configuré Git sur votre ordinateur. Passez à la section suivante pendant que nous finalisons la configuration de Git.

Pour poursuivre la configuration de Git, vous aurez besoin d’un nom d’utilisateur et d’une adresse courriel. Notez que cette adresse doit être la même que celle affiliée à votre compte GitHub.

Dans le terminal, entrez la commande suivante :

Input
{: .label .label-green}
~~~
git config --global user.name "Votre nom d’utilisateur GitHub"
git config --global user.email "L’adresse courriel affiliée à votre compte GitHub"
~~~

Normalement, aucun message ne devrait apparaître après que vous ayez entré cete commande.
Pour vérifier si la commande a été correctement effectuée, vous devez entrer la commande

Input
{: .label .label-green}
~~~
git config --list
~~~
encore une fois.

Un texte devrait maintenant apparaître, indiquant votre nom d’utilisateur ainsi que votre adresse courriel.

La dernière chose qu’il reste à faire est établir votre branche principale comme branche par défaut. Pour ce faire, entrez la commande :

Input
{: .label .label-green}
~~~
git config --global init.defaultBranch main
~~~
La commande init.defaultBranch permet d’attribuer à une branche git la valeur de branche par défaut.

Nous survolerons brièvement ces étapes : [https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-personal-access-token-classic](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token#creating-a-personal-access-token-classic) 

## Créer un répertoire

Un dépôt Git est une structure de données utilisée pour suivre les modifications apportées à un fichier au fil du temps. Les dépôts Git sont sauvegardés dans le même répertoire que les fichiers qui y sont associés, dans un répertoire masqué dont le nom porte l’extension « .git ».

Commençons par créer un nouveau répertoire en entrant la commande mkdir (_make directory_) suivie du nom que vous souhaitez attribuer au répertoire.

Input
{: .label .label-green}
~~~
mkdir gitAtelier
~~~
Pour vérifier qu’un répertoire a bel et bien été créé, entrez la commande ls (_list directory_). Un message devrait apparaître avec le nom du répertoire que vous venez de créer.

Input
{: .label .label-green}
~~~
ls
~~~
Vous pouvez passer d’un répertoire à un autre en entrant la commande cd (_change directory_). Allez au répertoire que vous venez de créer en entrant la commande :

Input
{: .label .label-green}
~~~
cd gitAtelier
~~~

### À propos de Git

Le plus gros défi soulevé par l’utilisation de Git et de GitHub est d’apprendre la terminologie des commandes. Si certains noms de commandes permettent d’identifier rapidement leur fonction, d’autres n’ont tout bonnement aucun sens (même en anglais). Par conséquent, la meilleure façon d’apprendre la terminologie des commandes Git est de les utiliser.

En général, le nom d’une commande Git a la forme suivante :

Input
{: .label .label-green}
~~~
git verbe option
~~~
Quand vous entrez une commande Git, commencez toujours par taper « git ». Puis, ajoutez un verbe décrivant ce que vous souhaitez faire (en anglais) : « _add_ », « _push_ », « _pull_ », « _init_ », etc. Les « options » sont des informations additionnelles qui précisent le sens de votre commande, par exemple en indiquant à quel répertoire elle s’applique.

Poursuivez la création de votre nouveau dépôt Git. Entrez la commande :

Input
{: .label .label-green}
~~~
git init
~~~
Le message suivant devrait apparaître :

Output
{: .label .label-yellow}
~~~
Initialized empty Git repository in <your file path>/gitWorkshop/.git/
~~~

## Démonstration de quelques commandes Git

### Afficher l’état d’un projet

La commande

Input
{: .label .label-green}
~~~
git status
~~~
permet d’afficher l’état d’un projet. En entrant cette commande maintenant, vous devriez voir apparaître ce texte : No commits yet and nothing to commit.

### Marquer un fichier et en prendre des instantanés

Nous allons maintenant créer et sauvegarder notre premier fichier de projet. Il s’agit d’un processus en deux étapes : d’abord, nous devons marquer le fichier ; puis, prendre des instantanés des modifications qui y sont apportées et les sauvegarder dans le dépôt Git. Ce procédé accorde un grand contrôle sur ce qui doit ou non figurer dans chaque instantané.

Entrez la commande

Input
{: .label .label-green}
~~~
touch index.md
~~~
pour créer un nouveau fichier nommé « index.md ». En effet, la commande `touch` permet de créer rapidement de nouveaux fichiers vides.

Vous pouvez entrer les commandes `ls` ou `git status` pour consulter le fichier nouvellement créé.

Après avoir entré la commande `git status`, un texte devrait indiquer qu’un nouveau fichier, dont le nom apparaît en rouge, a été ajouté au répertoire, mais que ce fichier n’est pas encore marqué. Pour indiquer à Git que vous souhaitez être en mesure de suivre les modifications apportées au fichier « index.md », entrez la commande

Input
{: .label .label-green}
~~~
git add index.md
~~~
La commande `git add` permet de marquer un fichier. Les modifications qui y sont apportées seront dès lors sauvegardées chaque fois que vous utiliserez la commande `git commit`. Autrement dit, si Git permet de prendre des instantanés des modifications apportées à un fichier, alors `git add` sert à indiquer quel contenu doit figurer dans cet instantané. La commande `git commit`, quant à elle, sert à prendre l’instantané en tant que tel et à le sauvegarder dans le répertoire.

Pour vérifier qu’un fichier a été marqué, entrez la commande

Input
{: .label .label-green}
~~~
git status
~~~
Un texte devrait indiquer que le nouveau fichier, dont le nom apparaît maintenant en vert, est marqué (_Changes to be commited_).

Avant de prendre un instantané de votre fichier, modifiez-le. Ouvrez le fichier dans un logiciel d’édition de texte (par exemple, _Notepad_ sur Windows, _TextEdit_ sur MacOS, etc.). Écrivez « # Bonjour ! ». Le symbole « # » est utilisé pour créer un titre en format Markdown (.md). Sauvegardez les modifications et fermez l’éditeur de texte. Dans Git Bash ou sur votre terminal, entrez la commande

Input
{: .label .label-green}
~~~
git status
~~~
Le texte suivant devrait apparaître :

Output
{: .label .label-yellow}
~~~
On branch main
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
    	new file:   index.md
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
    	modified:   index.md
~~~

Le message indique que des modifications apportées au fichier « index.md » ont été repérées, et que ces modifications n’ont pas été marquées. Entrez la commande

Input
{: .label .label-green}
~~~
git add index.md
~~~
Maintenant, vous allez prendre un instantané des modifications apportées au fichier « index.md » et le sauvegarder dans le répertoire créé précédemment. Prendre un instantané d’un fichier avec Git ressemble à l’action de sauvegarder un fichier. Toutefois, l’instantané d’un fichier contient beaucoup plus d’informations à propos des modifications qui y ont été apportées qu’une copie sauvegardée.

Quand vous prenez un instantané d’un fichier, il est préférable d’utiliser l’option -m. Cette option permet d’annoter un instantané - vous pouvez ainsi décrire, commenter ou résumer les modifications qui y figurent. Si vous lancez la commande git commit sans ajouter l’option -m, Git ouvrira automatiquement un éditeur de texte pour que vous puissiez joindre une plus longue annotation à votre instantané.

Entrez la commande

Input
{: .label .label-green}
~~~
git commit -m "Ajouté à index.md un titre"
~~~
Vous pouvez voir que le fichier, « index.md » a été modifié par l’ajout d’une ligne de texte : « # Bonjour ! ».

Vous disposez maintenant d’une trace permanente des modifications qui ont été apportées au fichier. Votre instantané contient même des métadonnées, comme l’identité de l’auteur des modifications (vous !), ainsi que l’heure et la date de ces changements. Vous avez ainsi gardé une trace de vos activités à l’intérieur du répertoire.

Si vous entrez la commande `git status`, un message devrait indiquer qu’il n’y a rien à prendre en instantané dans le répertoire.

## Utiliser les branches

### Que sont les branches ?

Dans Git, une branche est une nouvelle itération du répertoire principal. Lorsque vous travaillez sur un projet d’envergure, il peut être utile de disposer d’une deuxième branche pour travailler sur d’éventuels développements ou de nouvelles idées. Ainsi, en cas de problème, vous pourrez aisément retourner à votre branche principale.

Les branches permettent aussi de travailler sur différentes partie d’un projet sans impacter la branche principale. En effet, une fois le travail sur une branche secondaire complété, vous pouvez fusionner cette dernière à la branche principale.

La commande

Input
{: .label .label-green}
~~~
git branch
~~~
permet d’afficher les branches dans votre répertoire. À cette étape de l’atelier, entrer cette commande devrait uniquement afficher votre branche principale.

### Créer une nouvelle branche

Pour créer une nouvelle branche, entrez la commande

Input
{: .label .label-green}
~~~
git branch develop
~~~
Puis entrez à nouveau la commande

Input
{: .label .label-green}
~~~
git branch
~~~
pour afficher les branches dans votre répertoire, qui devraient maintenant être au nombre de deux.

### Naviguer entre différentes branches

La commande `git checkout` permet de naviguer entre les branches de votre répertoire. Entrez

Input
{: .label .label-green}
~~~
git checkout develop
~~~
pour naviguer jusqu’à la nouvelle branche que vous avez créée.

Ouvrez « index.md » dans un éditeur de texte et apportez-y un changement. Puis, retournez dans Git Bash ou sur votre terminal et entrez la commande `git status`. Un message devrait indiquer que le fichier « index.md » a été modifié.

Comme vous l’avez fait plus tôt, utilisez les commandes `git add index.md`, puis `git commit` pour prendre un instantané des modifications.

Entrez la commande

Input
{: .label .label-green}
~~~
git checkout main
~~~
pour naviguer jusqu’à la branche principale. Puis, ouvrez le fichier « index.md » dans un éditeur de texte. Normalement, vous ne devriez pas voir les modifications que vous y avez apportées. Celles-ci n’apparaîtront que lorsque vous serez dans la branche secondaire du répertoire.

### Fusionner des branches

Vous êtes maintenant prêt à fusionner les branches de votre répertoire. Une fois les branches fusionnées, vous obtiendrez une seule branche comprenant les modifications ajoutées dans la branche secondaire.

Entrez la commande


Input
{: .label .label-green}
~~~
git merge develop
~~~
Puis, ouvrez le fichier « index.md » dans un éditeur de texte. Vous devriez maintenant voir les modifications qui avaient été apportées à partir de la branche secondaire.

Si vous désirez supprimer la branche secondaire, entrez la commande

Input
{: .label .label-green}
~~~
git branch -d develop
~~~
Maintenant, en entrant la commande `git branch`, vous devriez uniquement voir la branche principale de votre répertoire.

## Partager votre travail

### Synchroniser votre dépôt local à un répertoire GitHub

Vous venez de créer un répertoire local, c’est-à-dire sur votre ordinateur. Plus tôt, nous avions créé un répertoire en ligne sur GitHub. Ces deux répertoires sont, pour l’instant, complètement séparés l’un de l’autre. Vous allez maintenant apprendre à les synchroniser, de façon à pouvoir partager vos projets avec d’autres personnes.

Pour synchroniser un répertoire local à un répertoire GitHub, entrez la commande suivante :

Input
{: .label .label-green}
~~~
git remote add <lien vers votre répertoire GitHub>
~~~
Par exemple :

Input
{: .label .label-green}
~~~
git remote add origin https://github.com/ClaraTurp/BiblioTECH_Git
~~~

### Synchroniser les modifications

Vous disposez maintenant de 2 répertoires interreliés. Néanmoins, le contenu de ces répertoires n’a pas encore été synchronisé. Par conséquent, votre répertoire en ligne devrait normalement être vide.

Pour synchroniser votre répertoire en ligne et votre répertoire local, entrez la commande

Input
{: .label .label-green}
~~~
git push -u origin main
~~~
En effet, « _origin_ » désigne votre répertoire GitHub et « _main_ », la branche principale de votre répertoire local. L’option « -u » indique à Git de se rappeler des paramètres associés à la commande `git push` : ainsi, la prochaine fois que vous entrerez cette commande, Git synchronisera automatiquement vos répertoires local et web.

En anglais, l’action de synchroniser des modifications pour les appliquer à un répertoire GitHub est parfois appelée « _pushing changes upstream_». Car, c’est à l’expression « _-set-uptstream_ » que réfère l’option « -u » employée précédemment.

Il est possible que Git vous demande d’entrer vos identifiants GitHub pour compléter la synchronisation de vos répertoires.

Lorsque vous synchronisez des répertoires, vous verrez Git faire « remonter » les modifications apportées aux fichiers sur votre ordinateur jusqu’au répertoire GitHub. Dans le cas de cet exercice, ce processus ne devrait pas prendre beaucoup de temps : il n’y a qu’un seul fichier à faire remonter jusqu’à votre répertoire en ligne. Notez cependant que la synchronisation peut être longue dans le cas où vous avez beaucoup de modifications à synchroniser. Vous pouvez entrer la commande `git status` pour afficher la progression de la synchronisation.
