# Notice

## Informations générales

Salut l'équipe ! Votre site est disponible sur [github](https://github.com/Erawpalassalg/bali-folio).

### Github

Github est une plateforme web, pour stocker et collaborer sur du code. Ce qui permettra de travailler à distance pour des modifications futures.

Elle servira aussi de CMS pour le site, vous permettantde faire les modification.

Un bénéfice supplémentaire est que Github conserve en mémoire toutes les modifications faites au code et aux images. Il sera donc **toujours** possible pour un développeur de retrouver des états ultérieurs si quelque chose venait à casser.

### Markdown

Tous les articles sur le site sont écrits en [Markdown](https://www.markdownguide.org/basic-syntax/), qui est un superset du HTML. C'est à dire que tout HTML écrit dans une page markdown sera compris par la machine. Il est donc **toujours possible** d'écrire du HTML dans un fichier `.markdown` ou `.md`

La syntaxe du Markdown est beaucoup plus lisible et compacte que celle du HTML. L'écriture d'articles s'en retrouve donc grandement facilitée.

## Utilisation Standard

Ce sont les cas d'utilisation facile du site. Ce pour quoi il est prévu, et qui ne devrait pas vous demander beaucoup de connaissances techniques.

### Ajouter des Images sur le site

#### Réduire la taille des images

TODO

#### Ajouter les images

Les images se trouves dans le dossier [img](https://github.com/Erawpalassalg/bali-folio/tree/master/img), des images peuvent être uploadées dans le dossier simplement en utilisant le bouton en haut à droite.

Je vous conseille une arborescence simple du type :

```
- img
   |
   +- PROJ1
   |   +- img 1
   |   +- img 2
   |
   +- PROJ2
       +- img 1
```

Mais, en soi, il n'y a pas de règle, donc faites ce qui vous convient le mieux !

## Ajouter et modifier des fichiers

### Ajouter une publication

... Parce que vous ne devriez pas avoir besoin d'ajouter d'autres fichiers qu'une publication.

Dans chacun des dossiers de publications (*_projets* et *_nouvelles*), vous pourrez ajouter des fichiers en cliquant sur le bouton **Ajouter un fichier** en haut à droite. Il suffit ensuite de le nommer **nom_de_la_publication.markdown** (ou **.md**, c'est la même chose)

### Modifier un fichier

Lorsque vous accédez à un fichier, **Github** permettra de le modifier en cliquant sur le bouton **Code** en haut de la page

### Valider les changements

Qu'il s'agisse d'un ajout ou d'une modification, il faudra valider (*commit* dans le jargon) les changements pour qu'ils prennent effet. Pour ça, un bouton **Commit changes** est disponible.

## Projets

Les \[publications à propos des\] projets sont situés dans le dossier [\_projets](https://github.com/Erawpalassalg/bali-folio/tree/master/_projets)

#### L'en-tête

Toutes les publications ont un en-tête, qui contiennent ses metadonnées. Le format pour les projets est le suivant :

```
---yaml                                                                    layout: post                                                               title: le_titre_du_projet                                                   description: un_sous_titre_un_peu_plus_long
img: /img/DVL/DVL_photo1.jpg # un exemple                                   
--- 
```

- `layout: post` **doit** être présent et ne change jamais. Ca dit à la machine qu'on va utiliser la mise en page spécifique aux publications
- `title: whatever` est le titre de la publication
- `desciption: whatever` est le sous-titre de la publication (assez mal nommée par le template...)
- `img: /chemin/vers/image` est le chemin (informatique) vers l'image qui sera présente dans la mosaïque
	- Si vous avez, par exemple, opté pour des thumbnails réduites au maximum pour votre mosaïque, que vous avez mises dans le dossier `/img/thumbnails/` et que l'image s'appelle `whatever.png`, le chemin à renseigner est donc `/img/thumbnails/whatever.png`
- le caractère `#` indique un commentaire, tout ce qui suit ce caractère sur la même ligne sera ignoré par la machine (et est donc exclusivement à destination des lecteurs du code, comme une note pour plus tard)
- les trois tirets `---` avant et après les metadatas sont **indispensables**

#### Le texte

C'est du Markdown tout ce qu'il y a de plus classique ! Vous avez un bouton `Preview` qui vous pemettra d'avoir une idée de ce à quoi l'article va ressembler.

#### Les images

Vous avez le choix de mettre des images sur 1, 2 et 3 colonnes. Voici le code (HTML) à utiliser.

##### 3 Colonnes (image pleine page)

```html
<div clas="img_row">
 <img class="col three" src="{{ site.baseurl }}/img/project_folder/img_x.jpg" title="my_image_purpose"/>
</div>
```

- C'est une simple image, avec un style qui dit qu'elle va prendre 3 colonnes :  `class="col three"`
- la partie `{{ site.baseurl }}` de l'attribut `src` doit toujours être présent (**si vous l'oubliez l'image ne s'affichera pas, c'est la première chose à regarder si vous êtes dans ce cas**)
- le chemin de l'image suite le même principe que [précédemment](#L'en-tête)
- `title` est un attribut qui permet à l'image d'être comprise par les robots; Qu'ils soient d'indexation (google & co) ou pour de la lecture de page web pour personne mal-voyante, par exemple.

##### 2 Colonnes (image longue)

Pareil que précédement, mais remplacer `col three` par `col two`

##### 3 Colonnes (petite image, mosaïque)

Pareil que précédement, mais remplacer `col three` par `col one`

##### Justifier à droite

Les images peuvent être justifiées à droite si elles prennent moins de 3 colonnes (le texte allant à gauche de l'image, le cas échéant), en ajoutant la classe `right` :

```html
<img class="col one right" src="{{site.baseurl}}/img/image_right.jpg">
```


---

Globalement, les `col two` et `col one` peuvent être combinés pour faire une ligne d'images :

```html
<div clas="img_row">
 <img class="col one" src="{{ site.baseurl }}/img/project_folder/img_x.jpg" title="my_image_purpose_1"/>
 <img class="col one" src="{{ site.baseurl }}/img/project_folder/img_y.jpg" title="my_image_purpose_2"/>
 <img class="col one" src="{{ site.baseurl }}/img/project_folder/img_z.jpg" title="my_image_purpose_3"/>
</div>

```

## Ajouter une Nouvelle

Comme pour les [projets](#Projets), les nouvelles ont leur dossier [\_nouvelles](https://github.com/Erawpalassalg/bali-folio/tree/master/_nouvelles).

L'en-tete d'une nouvelle est au format 

```yaml
---
layout: post
title: The Emperor of Ice Cream
date: 2015-07-06 07:59:00
---
```

- `layout: post` **doit** être présent et ne change jamais. Ca dit à la machine qu'on va utiliser la mise en page spécifique aux publications.
- `title: whatever` est le titre de la publication
- `date: yyyy-mm-dd hh:mm:ss` est la date de la publication, que le moteur du site utilisera pour trier les publications (les plus récentes en haut)

Le retse des informations est le même que pour un Projet

## Modifier le Profil

La page de profil est le fichier [bali.md](https://github.com/Erawpalassalg/bali-folio/blob/master/bali.md).

Les metadonnées de cette page ne devraient pas être modifiées. Mais à part ça, libre à vous de faire ce que vous souhaitez dans la page !


## Cas d'usage avancés

### Modifier le Footer

TODO

### Modifier le CSS (Sass, Scss)

TODO
