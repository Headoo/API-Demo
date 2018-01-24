# Documentation widget visual commerce.

Si vous n'avez pas d'uuid, merci de demander à support@headoo.com

## Intégration

Ajouter un div avec un id "widget-container" dans la page là ou le widget doit apparaître ainsi que le code suivant:

```
<script src="https://dab0b4kce2l36.cloudfront.net/js/widget-visualcommerce-0.0.2.js"></script>
<!-- use widget-visualcommerce-raw-0.0.2.js instead of widget-visualcommerce-0.0.2.js if you already use jQuery -->
<script>
    jQueryHeadoo(document).ready(function() {
        jQueryHeadoo.fn.visualCommerce({
            container: '#widget-container',
            uuid: ‘VOTRE_IDENTIFIANT’,
            locale: 'fr'
        });
    });
</script>
```

Lorsque vous ne pouvez pas modifier le template, un autres mode d'intégration est possible, en ciblant un élément dans la page et en se positionnant au choix avant ou après comme dans l'éxemple suivant avec le paramètre "placement". Le paramètre "selector" est un selecteur jQuery et "order" accepte les valeurs 'before' et 'after'.

```
<script src="https://dab0b4kce2l36.cloudfront.net/js/widget-visualcommerce-0.0.2.js"></script>
<script>
jQueryHeadoo(document).ready(function() {
    jQueryHeadoo.fn.visualCommerce({
        placement : {selector: '.selector:last', order: 'before|after'}
	uuid: ‘VOTRE_IDENTIFIANT’,
	locale: 'fr'
    });
});
</script>
```

Si des contenus sont enrichis d'au moins un tag et modérés positivement, le widget les affichera. Le cas échéant le widget disparaît de la page. Pour modifier ce comportement, en environnement de recette par exemple, vous pouvez ajouter ce paramètre "filters: {}", le widget affichera alors tous les derniers contenus aspirés directement.

Voici un exemple de ce mode:

`http://headoo.com/static/html/testvc.html`

Pour afficher le widget en mode galerie, il vous suffit d'ajouter le paramètre mode: "gallery". Voici un exemple:

```
<script src="https://dab0b4kce2l36.cloudfront.net/js/widget-visualcommerce-0.0.2.js"></script>
<script>
    jQueryHeadoo(document).ready(function() {
        jQueryHeadoo.fn.visualCommerce({
            container: '#widget-container',
            uuid: ‘VOTRE_IDENTIFIANT’,
            locale: 'fr',
	    mode: 'gallery'
        });
    });
</script>
```


Voici un exemple de ce mode:

`http://headoo.com/static/html/testvc-gallery.html`

## Options avancées

Les options avancées sont les suivantes, avec les valeurs par défaut : 


    settings: {
                container: null,
                placement: null, // Dynamically inject container on DOM exemple value: {selector: '.selector:last', order: 'before|after'}
                visualcommerce_id: null,
                uuid: null,
                tag_shortname: null, // Specific tag shortname to filter UGC
                widget_mode: 'widget', // ['widget'||'gallery']
                locale: 'en',
                width: '100%',
                itemWidth: 200, // Only for 'gallery' mode
                arrow_size: 'normal', // Only for 'widget' mode other value: 'small'
                gutter: 20, // Space between items
                height: 200, // Only for 'widget' mode
                limit: 15, // Pagination limit
                speed: 500, // Widget scroll easing speed
                resize_breakpoint: 546, // The container width until the items are resized to fill the widget space (only for widget mode)
                sort: '{"created_at":"desc"}', // API sort options (Attention aux quotes : il s'agit d'un string et pas un objet javascript)
                filters: '{"moderated":"1","tagged":"1"}', // API filter ((Attention aux quotes : il s'agit d'un string et pas un objet javascript)
                scheme: 'https', // Scheme for API call
                domain: 'headoo.com', // Domain for API call
                domain_assets: 'headoo.com', // Domain for assets loading
                assets_cache: true, // Cache or not assets
                hideTags: false, // Flag to hide the tags
                debug: false // Call API in app_dev mode
    }



## Filtrer les contenus affichés

Si vous souhaitez filtrer les contenus affichés dans le widget en fonction d'un tag existant, il vous suffit d'ajouter un paramètre "tag_shortname: '123456789a'".

```
<script src="https://dab0b4kce2l36.cloudfront.net/js/widget-visualcommerce-0.0.2.js"></script>
<script>
    jQueryHeadoo(document).ready(function() {
        jQueryHeadoo.fn.visualCommerce({
            container: '#widget-container',
            uuid: ‘VOTRE_IDENTIFIANT’,
            locale: 'fr',
	      tag_shortname: '123456789a'
        });
    });
</script>
```


Précision : Si à la place de '123456789a' vous mettez 'sac 123456789a' , tous les produits dont un tag id contient Sac '123456789a' vont apparaître. C'est pourquoi nous déconseillons les tag id contenant des espaces. En revanche, nous vous invitons à mettre plusieurs tags par produit, reprenant notamment l’id produit et ses catégories.


## Masquer les tags dans la popin

Pour masquer les tags dans la popin, partie droite, il suffit d’ajouter le paramètre hide_tags.

```
<script src="https://dab0b4kce2l36.cloudfront.net/js/widget-visualcommerce-0.0.2.js"></script>
<script>
    jQueryHeadoo(document).ready(function() {
        jQueryHeadoo.fn.visualCommerce({
            container: '#widget-container',
            uuid: ‘VOTRE_IDENTIFIANT’,
            locale: 'fr',
            hide_tags: true
        });
    });
</script>
```


## Autres mode d’intégration

Passer par l’API REST : 
[exemple d’API](https://api.headoo.com/api/v1/photos/get.json?uuid=7332ba4b-6cac-480d-9466-f2acfa91&limit=15&sorts={%22created_at%22:%22desc%22}&filters={%22moderated%22:%221%22,%22tagged%22:%221%22}&limit=15)

Là aussi il faudra remplacer la valeur de uuid avec la valeur que l’on aura fourni

Cette API ne requiert PAS d'authentification

[Référence de l'API](https://admin.headoo.com/doc/api)

Utiliser systématiquement https://api.headoo.com au lieu de https://headoo.com (https://headoo.com sera déprécié courant 2018 pour les appels API)


## Showcase
### ishop.galery
Notre produit ishop.gallery utilise notre API

Par exemple, sur https://ishop.gallery/soniarykiel/, voici l'API utilisée : `https://ishop.gallery/api/v1/photos/get.json?uuid=e70359e0-6ef9-4c1a-81b5-a6bbbcea&sorts={%22sort%22:%22asc%22,%22instagram_created_at%22:%22desc%22}&limit=20&page=1&_=1510157242205`

### Foir'fouille
* [Home](https://www.lafoirfouille.fr/) widget headoo avec personnalisation de la taille des images via configuration itemWidth : . On peut voir dans les sources (onglet network dans Chrome) que le widget utilise l'API, en l'occurence : `https://headoo.com/api/v1/photos/get.json?uuid=1dcd47d8-695c-4134-b5ec-3108ed15066f&limit=15&sorts={%22created_at%22:%22desc%22}&filters=[object%20Object]&limit=15` avec des paramètres de tri, de limit et de filtre.

* [Page gallerie dédiée](https://www.lafoirfouille.fr/galerie-photo-communaute.html) avec un mode d'affichage gallerie et une limite du nombre d'objets retournés

        widget_mode: 'gallery',
        limit: 18,

    Ici aussi, l'API appelée par le widget est visible dans l'onglet network : `https://headoo.com/api/v1/photos/get.json?uuid=1dcd47d8-695c-4134-b5ec-3108ed15066f&limit=18&sorts={%22created_at%22:%22desc%22}&filters=[object%20Object]&limit=18`


### Monnier Frères
* [Page produit](http://www.monnierfreres.fr/hui-sac-seau-m-86926a-lan005039-fr.html#fparent) Dans ce cas, le widget est appelé dans un iframe (source : `http://www.monnierfreres.fr/headoo.php?sku=LAN005039`). L'appel API est visible dans la console de debug avec un filtre sur la référence produit : `https://headoo.com/api/v1/photos/get.json?uuid=db559230-db1b-4ec6-bd7e-7eca8f094608&limit=15&sorts={%22created_at%22:%22desc%22}&filters={%22moderated%22:%221%22,%22tagged%22:%221%22}&limit=15&tag_shortname=LAN005039`


## Détail des champs de l'API

### Request
```
https://headoo.com/api/v1/photos/get.json?uuid=3e87b615-02a1-4915-a41f-0aa7510c&limit=15&sorts={%22created_at%22:%22desc%22}&filters={%22moderated%22:%221%22,%22tagged%22:%221%22}&limit=15&tag_shortname=648612902
```
### Response
```
{  
   "page":1,
   "results":1,
   "lastpage":true,
   "nb_pages":1,
   "data":[  
      {  
         "id":1418830,
         "thumbnail":"https:\/\/dzn64v9qd7vq9.cloudfront.net\/photo_square\/59f\/59fc2ef598cfc.jpg",
         "media":"https:\/\/headoo-media.s3.amazonaws.com\/shooting\/59f\/59fc2ef598cfc.jpg",
         "created_at":"2017-11-03T08:55:17+00:00",
         "opted_at":"2017-11-03T08:55:16+00:00",
         "optin":1,
         "content":"\u041f\u0435\u0440\u0432\u044b\u0435 \u043f\u043e\u0437\u0434\u0440\u0430\u0432\u043b\u0435\u043d\u0438\u044f ??\n.\n.\n.\n#bday #zebra #Etam #jagger_schnauzer #morning #lifeissobeautiful #happy #sweetnovember #november2017",
         "username":"marinamatsiuk",
         "moderation":0,
         "moderation_elastica":1,
         "page_url":"https:\/\/headoo.com\/photo\/1418830?access_token=445142edeee1b636ce35a26281d6d0f1",
         "instagram_link":"https:\/\/www.instagram.com\/p\/Ba8n_XcAn3L\/",
         "instagram_likes":80,
         "instagram_comments":32,
         "instagram_filter":"Normal",
         "instagram_type":"image",
         "instagram":"marina_horbunova",
         "profil_picture":"https:\/\/scontent.cdninstagram.com\/t51.2885-19\/s150x150\/14269009_1680189662308745_2048434738_a.jpg",
         "instagram_user_followed":246,
         "instagram_user_followers":191,
         "social_media":"https:\/\/scontent.cdninstagram.com\/t51.2885-15\/e35\/p320x320\/22860589_1957011234562641_3400318538727030784_n.jpg",
         "instagram_content":"\u041f\u0435\u0440\u0432\u044b\u0435 \u043f\u043e\u0437\u0434\u0440\u0430\u0432\u043b\u0435\u043d\u0438\u044f \ud83d\ude0b\ud83d\udc15\n.\n.\n.\n#bday #zebra #Etam #jagger_schnauzer #morning #lifeissobeautiful #happy #sweetnovember #november2017",
         "tags":[  
            {  
               "id":9889,
               "establishment_id":2145,
               "shortname":"648612902",
               "logo":"https:\/\/headoo.com\/media\/cache\/resolve\/establishment_logo_hd\/tags\/9889\/logo-5990071aab817.jpg%3Fsw=500%26sh=591",
               "default_locale":"fr",
               "created_at":"2017-08-13T08:00:26+00:00",
               "updated_at":"2017-08-13T08:00:26+00:00",
               "visualcommerce_id":47,
               "translations":{  
                  "fr":{  
                     "name":"Combinaison z\u00e8bre",
                     "url":"http:\/\/www.etam.com\/nuit\/modeles\/combinaisons\/combinaison-zebre-648612902.html",
                     "url_utm":"http:\/\/www.etam.com\/nuit\/modeles\/combinaisons\/combinaison-zebre-648612902.html?utm_source=headoo&utm_medium=ishop&utm_campaign=shoppable-instagram-",
                     "logo":""
                  }
               },
		"position":"{\"position\":{\"x\":0.36,\"y\":0.28},\"text\":\"\",\"buttonAttributes\":{},\"popupAttributes\":{}}"

            }
         ],
         "has_demand":true,
         "has_response":true,
         "is_tagged":true,
         "instagram_deleted":false
      }
   ]
}
```

#### Info about response

* data.0.media is the media (image). It is a copy of the source, not necessarily square
* data.0.thumbnail is the media (image) squared. Use it when you want a square image
* data.0.tags.0.position : il s'agit d'un string et pas un objet javascript.
Voici les correspondances : 

| Position | 0      | 1       |
|:--------:|:-------|:--------|
| x        | gauche | droite  |
| y        | haut   | bas     |

Exemple d'API contenant des positions : `https://api.headoo.com/api/v1/photos/get.json?establishment_id=1789&sorts=%7B%22sort%22:%22asc%22,%22instagram_created_at%22:%22desc%22%7D&limit=20&page=1&_=1510759199172`

## Remarques

dab0b4kce2l36.cloudfront.net est le CDN de headoo.com

Dans le cas, ou il est impossible de modifier le site où le widget va être intégré, il est possible de l'intégrer dans un élément existant de la page. Pour ce faire il suffit de remplacer le paramètre "container"par "placement: {selector: '.cross-sell h2', order: 'before'}". 
"selector" doit pointer vers un élément existant dans la page et la valeur de "order" doit être 'before' ou 'after'. 


Concernant les medias dans la section "meilleurs publications", si ce ne sont pas des publications à l'intérieur de la période d'absorption, elles ne seront pas absorbées.

En fonction de votre contrat, il y a une limite d'absorption par heure, paramétrable, donc certains medias peuvent ne pas être absorbés, notamment si le flux créé sur instagram pour l'ensemble de vos hashtags est supérieur à ce chiffre.

Pour répondre au sujet des "meilleurs publications", nous avons dans notre roadmap une fonctionnalité qui consiste à permettre d'absorber un media instagram donné. On pourrait envisager par exemple un bouton [absorber les "meilleurs publications"] et/ou un bouton : [absorber un post précis].

C'est un développement que nous envisageons de mettre en place fin 2017/début 2018.
