---
title: API Réseau-SAM

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell

toc_footers:
  - <a href='https://www.reseau-sam.be'>Réseau-SAM</a>
  - <a href='https://www.reseau-sam.be/fr/services-sam/webservice'>Services SAM - Webservices</a>

# includes:
#   - errors

search: false

code_clipboard: true

meta:
  - name: description
    content: Documentation API Réseau-SAM
---

# API Réseau-SAM

Bienvenue sur l'API Réseau SAM! Vous pouvez utiliser les différents endpoints de notre API pour récupérer les informations concernant votre réseau de prestataires.

# Identification

> Pour vous authentifier, utilisez ce code :

```shell
# Avec shell, vous pouvez simplement passer le bon en-tête avec chaque requête
curl "api_endpoint_here" \
  -H "Authorization: Bearer samapitoken"
```

> Assurez-vous de remplacer `samapitoken` par votre clé API.

RéseauSAM utilise des tokens pour permettre l'accès à son API. Ces tokens sont essentiels pour assurer une communication sécurisée avec l'API de RéseauSAM.

Pour obtenir un token d'accès à l'API de RéseauSAM, il vous faut contacter directement l'équipe de RéseauSAM. Vous pouvez le faire par email, téléphone.

Une fois que vous avez reçu votre token, celui-ci doit être inclus dans toutes les requêtes API que vous envoyez au serveur.

<aside class="notice">
Vous devez remplacer <code>samapitoken</code> par votre clé API personnelle.
</aside>

# Mon réseau

## Lister les prestataires

```shell
curl -X POST "https://www.reseau-sam.be/api/prestataires/search" \
  -H "Authorization: samapitoken" \
  -H "Content-Type: application/json" \
  -d '{"scopes": [ {"name": "myNetwork" } ]}'
```

> La commande ci-dessus renvoie du JSON structuré de cette manière :

```json
{
  "data": [
    {
    "id": 1234,
    "value": 1234,
    "prestataire_id": 1234,
    "enabled": true,
    "verified": true,
    "complete": false,
    "promoted": false,
    "contact_form": false,
    "visible_sam": true,
    "status": 1,
    "titre": "John Doe - Thérapeute XYZ",
    "videos": "",
    "label": "John Doe - Thérapeute XYZ",
    "slug": "john-doe-therapeute-xyz",
    "email": "jdoe.xyz@gmail.com",
    "societe": "John Doe - Thérapeute XYZ",
    "logo": "",
    "nom": "Doe",
    "cdcs_count": 0,
    "prenom": "John",
    "forme_juridique": null,
    "numero_entreprise": "BE 1234.567.890",
    "numero_inami": "1.23456.78.910",
    "conventionne": null,
    "membre_de": "",
    "public_cible": null,
    "description_activite": "Thérapie XYZ à domicile : \nAccompagnement, évaluation et conseil ...",
    "telephone": "0123 45 67 89",
    "gsm": "0123 45 67 89",
    "fax": "",
    "website": "http://www.johndoe.xyz",
    "specialisation": "",
    "autres_activites": "",
    "horaires": "lundi - mardi - jeudi sur RV: 8h30 à 18h",
    "honoraires": "",
    "conditions_access": "Ouvert à tous, divers",
    "autres_infos": "",
    "video": "",
    "facebook": "",
    "twitter": "",
    "linkedin": "",
    "instagram": "",
    "super_logo": "",
    "super_show_network": false,
    "super_description": "",
    "super_title": "",
    "super_show_annuaire": false,
    "super_show_infos": false,
    "super_show_agenda": false,
    "super_show_annonces": false,
    "site_clef": "",
    "progenda_slug": null,
    "progenda_has_link": 0,
    "progenda_has_iframe": 0,
    "mrab_status": null,
    "mrab_source": null,
    "mrab_id": null,
    "newsletter_tracking": null,
    "distance": null,
    "created_at": "2023-03-21T10:48:47.000000Z",
    "updated_at": "2023-04-17T07:29:13.000000Z",
    "childrens_count": 0,
    "infos": [],
    "sectors": [],
    "besoins": [],
    "cdcs": [],
    "user": {
        "label": "jdoe.xyz@gmail.com",
        "value": 7478,
        "roles": [
            "presta"
        ]
    },
    { ... }
  ],
  "links": {
        "first": "https://www.reseau-sam.be/api/prestataires/search?page=1",
        "last": "https://www.reseau-sam.be/api/prestataires/search?page=4",
        "prev": null,
        "next": "https://www.reseau-sam.be/api/prestataires/search?page=2"
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 4,
        "links": [
            {
                "url": null,
                "label": "pagination.previous",
                "active": false
            },
            {
                "url": "https://www.reseau-sam.be/api/prestataires/search?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": "https://www.reseau-sam.be/api/prestataires/search?page=2",
                "label": "2",
                "active": false
            },
            {
                "url": "https://www.reseau-sam.be/api/prestataires/search?page=3",
                "label": "3",
                "active": false
            },
            {
                "url": "https://www.reseau-sam.be/api/prestataires/search?page=4",
                "label": "4",
                "active": false
            },
            {
                "url": "https://www.reseau-sam.be/api/prestataires/search?page=2",
                "label": "pagination.next",
                "active": false
            }
        ],
        "path": "https://www.reseau-sam.be/api/prestataires/search",
        "per_page": 15,
        "to": 15,
        "total": 50
    }
}
```

Ce point d'accès récupère tous les prestataires de votre réseau.

### Requête HTTP

`POST https://www.reseau-sam.be/api/prestataires/search`

### Corps de la requête

Veillez à bien inclure le JSON suivant dans le corps de la requête afin de limiter les résultats aux prestataires de votre réseau.

<code>
{ "scopes": [{ "name": "myNetwork" }] }
</code>

### Paramètres d'URL

| Paramètre | Description                   |
| --------- | ----------------------------- |
| page      | Numéro de la page à récupérer |

## Récupérer un prestataire individuel

```shell
curl "https://www.reseau-sam.be/api/prestataires/{slug}"
```

> Veillez à remplacer {slug} par le slug du prestataire à récupérer

> La commande ci-dessus renvoie du JSON structuré de cette manière :

```json
{
  "data": {
    "id": 1234,
    "value": 1234,
    "prestataire_id": 1234,
    "enabled": true,
    "verified": true,
    "complete": false,
    "promoted": false,
    "contact_form": false,
    "visible_sam": true,
    "status": 1,
    "titre": "John Doe - Thérapeute XYZ",
    "videos": "",
    "label": "John Doe - Thérapeute XYZ",
    "slug": "john-doe-therapeute-xyz",
    "email": "jdoe.xyz@gmail.com",
    "societe": "John Doe - Thérapeute XYZ",
    "logo": "",
    "nom": "Doe",
    "cdcs_count": 0,
    "prenom": "John",
    "forme_juridique": null,
    "numero_entreprise": "BE 1234.567.890",
    "numero_inami": "1.23456.78.910",
    "conventionne": null,
    "membre_de": "",
    "public_cible": null,
    "description_activite": "Thérapie XYZ à domicile : \nAccompagnement, évaluation et conseil ...",
    "telephone": "0123 45 67 89",
    "gsm": "0123 45 67 89",
    "fax": "",
    "website": "http://www.johndoe.xyz",
    "specialisation": "",
    "autres_activites": "",
    "horaires": "lundi - mardi - jeudi sur RV: 8h30 à 18h",
    "honoraires": "",
    "conditions_access": "Ouvert à tous, divers",
    "autres_infos": "",
    "video": "",
    "facebook": "",
    "twitter": "",
    "linkedin": "",
    "instagram": "",
    "super_logo": "",
    "super_show_network": false,
    "super_description": "",
    "super_title": "",
    "super_show_annuaire": false,
    "super_show_infos": false,
    "super_show_agenda": false,
    "super_show_annonces": false,
    "site_clef": "",
    "progenda_slug": null,
    "progenda_has_link": 0,
    "progenda_has_iframe": 0,
    "mrab_status": null,
    "mrab_source": null,
    "mrab_id": null,
    "newsletter_tracking": null,
    "distance": null,
    "created_at": "2023-03-21T10:48:47.000000Z",
    "updated_at": "2023-04-17T07:29:13.000000Z",
    "childrens_count": 0,
    "infos": [],
    "sectors": [],
    "besoins": [],
    "cdcs": [],
    "user": {
      "label": "jdoe.xyz@gmail.com",
      "value": 7478,
      "roles": ["presta"]
    }
  }
}
```

Ce point d'accès récupère un prestataire individuellement.

### Requête HTTP

`GET https://www.reseau-sam.be/api/prestataires/{slug}`

# Filtres

## Préoccupations

```shell
curl "https://www.reseau-sam.be/api/besoins"
```

> La commande ci-dessus renvoie du JSON structuré de cette manière :

```json
{
    "data": [
        {
            "id": 1,
            "value": 1,
            "slug": "01sinformer-sur-une-maladie-un-handicap-une-pathologie",
            "titre": "S'informer",
            "definition": "<p>Repérer les prémisses d'une pathologie ou d'un handicap, s'informer sur un diagnostic ou encore s'atteler à prendre soin de son proche fragilisé tout en préservant sa propre santé en tant que SAM.</p>",
            "image": "s-informer-maladie-handicap.jpg",
            "label": "S'informer",
            "parent": null,
            "sectors": [],
            "parent_id": null,
            "translations": {
                "titre": {
                    "fr": "S'informer",
                    "nl": "Op de hoogte blijven"
                },
                "slug": {
                    "fr": "01sinformer-sur-une-maladie-un-handicap-une-pathologie",
                    "nl": "op-de-hoogte-blijven"
                },
                "definition": {
                    "fr": "<p>Repérer les prémisses d'une pathologie ou d'un handicap, s'informer sur un diagnostic ou encore s'atteler à prendre soin de son proche fragilisé tout en préservant sa propre santé en tant que SAM.</p>",
                    "nl": "<p>Het begin van een pathologie of een handicap opsporen, een diagnose leren kennen of voor een zwak familielid zorgen met behoud van de eigen gezondheid als verzorger.</p>"
                },
                "image": {
                    "fr": "s-informer-maladie-handicap.jpg"
                }
            }
        },
        { ... }
    ]
}
```

Ce point d'accès récupère les différentes préoccupations utilisées sur Réseau-SAM

### Requête HTTP

`GET https://www.reseau-sam.be/api/besoins`

## Secteurs d'activités

```shell
curl "https://www.reseau-sam.be/api/sectors"
```

> La commande ci-dessus renvoie du JSON structuré de cette manière :

```json
{
    "data": [
        {
            "id": 1,
            "value": 1,
            "slug": "centre-de-jour",
            "titre": "Centre de jour",
            "label": "Centre de jour",
            "type": null,
            "parent": null,
            "translations": {
                "titre": {
                    "fr": "Centre de jour",
                    "nl": "Dagcentrum"
                },
                "slug": {
                    "fr": "centre-de-jour",
                    "nl": "dagcentrum"
                }
            }
        },
        { ... }
    ]
}
```

Ce point d'accès récupère les différents secteurs d'activités utilisés sur Réseau-SAM

### Requête HTTP

`GET https://www.reseau-sam.be/api/sectors`

## Zones de couverture

```shell
curl "https://www.reseau-sam.be/api/places"
```

> La commande ci-dessus renvoie du JSON structuré de cette manière :

```json
{
  "data": [
    {
      "id": 1,
      "type": 1,
      "nom": "Région de Bruxelles-Capitale",
      "label": "Région de Bruxelles-Capitale",
      "value": 1,
      "province": "",
      "arrondissement": "",
      "commune": "",
      "localite": "",
      "geojson": {
        "type": "Feature",
        "properties": {
          "RecId": 301,
          "AdCoKey": "01000",
          "AdPrKey": "04000",
          "AdReKey": "04000",
          "NameDUT": "Brussels Hoofdstedelijk Gewest",
          "NameFRE": "Région de Bruxelles-Capitale",
          "NameGER": "Region Brüssel-Hauptstadt",
          "UpdDate": "2020-03-26",
          "Version": 1,
          "FiscSitId": 5,
          "Stat_Area": 16242,
          "Shape_Area": 162419848.165131,
          "Shape_Leng": 72162.1390417262
        },
        "geometry": {
          "type": "Polygon",
          "coordinates": [[[4.3117983, 50.7975121]]]
        }
      },
      "polygon": "",
      "geoprops": {
        "RecId": 301,
        "AdCoKey": "01000",
        "AdPrKey": "04000",
        "AdReKey": "04000",
        "NameDUT": "Brussels Hoofdstedelijk Gewest",
        "NameFRE": "Région de Bruxelles-Capitale",
        "NameGER": "Region Brüssel-Hauptstadt",
        "UpdDate": "2020-03-26",
        "Version": 1,
        "FiscSitId": 5,
        "Stat_Area": 16242,
        "Shape_Area": 162419848.165131,
        "Shape_Leng": 72162.1390417262
      }
    }
  ],
  "links": {
    "first": "https://www.reseau-sam.be/api/places?page=1",
    "last": "https://www.reseau-sam.be/api/places?page=238",
    "prev": null,
    "next": "https://www.reseau-sam.be/api/places?page=2"
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 238,
    "links": [
      {
        "url": null,
        "label": "pagination.previous",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=1",
        "label": "1",
        "active": true
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=2",
        "label": "2",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=3",
        "label": "3",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=4",
        "label": "4",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=5",
        "label": "5",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=6",
        "label": "6",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=7",
        "label": "7",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=8",
        "label": "8",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=9",
        "label": "9",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=10",
        "label": "10",
        "active": false
      },
      {
        "url": null,
        "label": "...",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=237",
        "label": "237",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=238",
        "label": "238",
        "active": false
      },
      {
        "url": "https://www.reseau-sam.be/api/places?page=2",
        "label": "pagination.next",
        "active": false
      }
    ],
    "path": "https://www.reseau-sam.be/api/places",
    "per_page": 15,
    "to": 15,
    "total": 3560
  }
}
```

Ce point d'accès récupère les différentes zones de couverture utilisées sur Réseau-SAM

### Requête HTTP

`GET https://www.reseau-sam.be/api/places`
