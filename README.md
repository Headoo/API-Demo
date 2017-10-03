# Documentation widget visual commerce.

Si vous n'avez pas d'uuid, merci de demander à support@headoo.com

## Intégration

Ajouter un div avec un id "widget-container" dans la page là ou le widget doit apparaître ainsi que le code suivant:

```
<script src="https://headoo.com/js/widget-visualcommerce.js"></script>
<script>
    jQueryHeadoo(document).ready(function() {
        jQueryHeadoo.fn.visualCommerce({
            container: '#widget-container',
            uuid: ‘VOTRE_IDENTIFIANT’,
            locale: 'fr'
        }).init();
    });
</script>
```

Voici un exemple de ce mode:

`https://cdn.rawgit.com/nicolasbonnici/4cd765dfd81bc5770e856452db5f7cd0/raw/c3352dd0eec4e20e852a3a08e00a3bce96d7e109/widget-vc-banner.html`

Si des contenus sont enrichis d'au moins un tag et modérés positivement, le widget les affichera. Le cas échéant le widget disparaît de la page. Pour modifier ce comportement, en environnement de recette par exemple, vous pouvez ajouter ce paramètre "filters: {}", le widget affichera alors tous les derniers contenus aspirés directement.

Pour afficher le widget en mode galerie, il vous suffit d'ajouter le paramètre mode: "gallery". Voici un exemple:

```
<script src="https://headoo.com/js/widget-visualcommerce.js"></script>
<script>
    jQueryHeadoo(document).ready(function() {
        jQueryHeadoo.fn.visualCommerce({
            container: '#widget-container',
            uuid: ‘VOTRE_IDENTIFIANT’,
            locale: 'fr',
      mode: 'gallery'
        }).init();
    });
</script>
```


Voici un exemple de ce mode:

`https://cdn.rawgit.com/nicolasbonnici/e72b35a953407b81190b2fa215449918/raw/fe48e69d188f04d2ac68bd35de19a6576f832019/vc-widget-gallery.html`

## Filtrer les contenus affichés

Si vous souhaitez filtrer les contenus affichés dans le widget en fonction d'un tag existant, il vous suffit d'ajouter un paramètre "tag_shortname: '123456789a'".

```
<script src="https://headoo.com/js/widget-visualcommerce.js"></script>
<script>
    jQueryHeadoo(document).ready(function() {
        jQueryHeadoo.fn.visualCommerce({
            container: '#widget-container',
            uuid: ‘VOTRE_IDENTIFIANT’,
            locale: 'fr',
	      tag_shortname: '123456789a'
        }).init();
    });
</script>
```


Précision : Si à la place de '123456789a' vous mettez 'sac 123456789a' , tous les produits dont un tag id contient Sac '123456789a' vont apparaître. C'est pourquoi nous déconseillons les tag id contenant des espaces. En revanche, nous vous invitons à mettre plusieurs tags par produit, reprenant notamment l’id produit et ses catégories.


## Masquer les tags dans la popin

Pour masquer les tags dans la popin, partie droite, il suffit d’ajouter le paramètre hide_tags.

```
<script src="https://headoo.com/js/widget-visualcommerce.js"></script>
<script>
    jQueryHeadoo(document).ready(function() {
        jQueryHeadoo.fn.visualCommerce({
            container: '#widget-container',
            uuid: ‘VOTRE_IDENTIFIANT’,
            locale: 'fr',
            hide_tags: true
        }).init();
    });
</script>
```


## Autres mode d’intégration

Dans le cas, ou il est impossible de modifier le site où le widget va être intégré, il est possible de l'intégrer dans un élément existant de la page. Pour ce faire il suffit de remplacer le paramètre "container"par "placement: {selector: '.cross-sell h2', order: 'before'}". 
"selector" doit pointer vers un élément existant dans la page et la valeur de "order" doit être 'before' ou 'after'. 


Passer par l’API REST : 
[exemple d’API](https://headoo.com/api/v1/photos/get.json?uuid=7332ba4b-6cac-480d-9466-f2acfa91&limit=15&sorts={%22created_at%22:%22desc%22}&filters={%22moderated%22:%221%22,%22tagged%22:%221%22}&limit=15)

Là aussi il faudra remplacer la valeur de uuid avec la valeur que l’on aura fourni

[Preview ici](http://htmlpreview.github.io/?https://github.com/Headoo/API-Demo/blob/master/api-demo.html)



## Remarques

Concernant les medias dans la section "meilleurs publications", si ce ne sont pas des publications à l'intérieur de la période d'absorption, elles ne seront pas absorbées.

En fonction de votre contrat, il y a une limite d'absorption par heure, paramétrable, donc certains medias peuvent ne pas être absorbés, notamment si le flux créé sur instagram pour l'ensemble de vos hashtags est supérieur à ce chiffre.

Pour répondre au sujet des "meilleurs publications", nous avons dans notre roadmap une fonctionnalité qui consiste à permettre d'absorber un media instagram donné. On pourrait envisager par exemple un bouton [absorber les "meilleurs publications"] et/ou un bouton : [absorber un post précis].

C'est un développement que nous envisageons de mettre en place fin 2017/début 2018.
