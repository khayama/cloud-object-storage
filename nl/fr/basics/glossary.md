﻿---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-03-19"

keywords: glossary, getting started, terms

subcollection: cloud-object-storage

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:download: .download}

# Termes clés
{: #terminology}

## Clés S3 {{site.data.keyword.cos_short}} ou clé d'API IAM
{: #terminology-auth}

Les instances d'{{site.data.keyword.cos_short}} mises à disposition en tant qu'infrastructure sous forme de services utilisent des paires de clés secrète et d'accès (appelées clés HMAC) au lieu d'une clé d'API IAM {{site.data.keyword.cloud_notm}}. Ces paires de clés permettent de créer des signatures AWS V4 pour l'authentification et l'autorisation au lieu des jetons bearer OAuth2 utilisés par IAM {{site.data.keyword.cloud_notm}}. Bien que les clés d'API IAM permettent un contrôle d'accès à granularité fine beaucoup plus performant, les clés HMAC sont obligatoires pour utiliser les outils et les passerelles compatibles S3 (tels que l'interface CLI AWS ou Cyberduck).

## Données d'identification de service
{: #terminology-service-credential}

Les données d'identification de service sont un ensemble d'informations importantes dont les développeurs se servent pour connecter les applications à une instance d'Object Storage :

```json
{
  "apikey": "<apikey>",
  "endpoints": "https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints",
  "iam_apikey_description": "<auto-generated-apikey-description>",
  "iam_apikey_name": "<auto-generated-apikey-description>",
  "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:<role>",
  "iam_serviceid_crn": "crn:v1:staging:public:iam-identity::a/<account-id>::serviceid:ServiceId-<GUID>",
  "resource_instance_id": "crn:v1:bluemix:public:cloud-object-storage:global:a//<account-id>:<resource-instance-GUID>::"
}
```

## Emplacement de compartiment {{site.data.keyword.cos_short}}
{: #terminology-location}

Tous les compartiments dans {{site.data.keyword.cos_short}} portent sur un emplacement. Il s'agit d'une région (par exemple, `us-south` ou `us-east`) ou d'une zone géographique (par exemple, `eu-geo` ou `us-geo`). Dans cet emplacement, les objets sont découpés en tranches et dispersés dans trois emplacements physiques différents.

## ID d'instance de ressource/ID d'instance de service
{: #terminology-service-instance-id}

Lorsque vous créez ou mettez à disposition une instance d'un service, un identificateur unique lui est affecté sous la forme d'un nom de ressource de cloud (CRN) :

```
crn:v1:bluemix:public:<service-name>:<region>:a/<account-id>:<resource-instance-GUID>:<resource-type>:<resource>
```

Pour une instance d'{{site.data.keyword.cos_short}}, cela peut ressembler à ce qui suit :

```
crn:v1:bluemix:public:cloud-object-storage:global:a/3bf0d9003abfb5d29761c3e97696b71c:d6f04d83-6c4f-4a62-a165-696756d63903::
```

## ID de service
{: #terminology-service-id}

Un ID de service est un utilisateur abstrait destiné à être utilisé par les développeurs pour identifier les applications (ou les composants d'applications) qui accèdent aux ressources de stockage d'objets. Les ID de service peuvent se voir accorder des rôles IAM sur des ressources comme n'importe quel autre utilisateur.

## Instance de ressource/instance de service
{: #terminology-service-instance}

Instance d'un service de cloud. Selon le service, il peut s'agir d'une instance unique ou d'un compte au sein d'un service à service partagé ({{site.data.keyword.cos_short}}).

## Noeud final d'identité
{: #terminology-identity}

Le noeud final IAM (`iam.cloud.ibm.com`) est utilisé pour extraire un jeton d'accès en échange d'une clé d'API. Ce jeton est utilisé dans l'en-tête `Authorization` de toutes les demandes d'API REST envoyées vers un noeud final de service {{site.data.keyword.cos_short}}.

## Noeuds finaux de service
{: #terminology-service-endpoint}
Les [noeuds finaux de service](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints) (par exemple, `s3.us-south.cloud-object-storage.appdomain.cloud`) sont les URL de base vers lesquelles les demandes d'API qui interagissent avec les données sont envoyées.

## Régions
{: #terminology-region}
Les termes région et emplacement sont souvent utilisés de façon interchangeable, mais contrairement à la plupart des services disponibles dans la plateforme {{site.data.keyword.cloud_notm}}, {{site.data.keyword.cos_short}} est un service 'global'. La plateforme {{site.data.keyword.cloud_notm}} existe dans différentes régions (par exemple, `US South` ou `United Kingdom`) et certains services portent sur l'emplacement où ils ont été créés. Bien que chaque instance d'{{site.data.keyword.cos_short}} soit considérée comme 'globale', chaque compartiment individuel possède une combinaison spécifique d'emplacement, de résilience et de classe de stockage.

## Résilience {{site.data.keyword.cos_short}}
{: #terminology-resiliency}

La résilience fait référence à la portée et à la dimension de la zone géographique dans laquelle vos données sont distribuées. La résilience _inter-régionale_ propagera vos données dans plusieurs zones métropolitaines, tandis que la résilience _régionale_ propagera les données dans une seule zone métropolitaine.

## Ressource
{: #terminology-resource}

Tout ce que vous avez créé dans {{site.data.keyword.cloud_notm}}. Une ressource peut être une instance d'un service, un cluster Kubernetes, un compartiment de stockage d'objet, une application Cloud Foundry, ou presque tout autre élément créé dans la plateforme {{site.data.keyword.cloud_notm}}. L'accès aux ressources est contrôlé à l'aide des règles IAM (Identity and Access Management).

## Rôles IAM
{: #terminology-roles}

Les rôles IAM représentent le niveau d'accès qu'un objet donné doit avoir sur une ressource donnée. Il existe deux types de rôles :
  - les rôles de plateforme, qui permettent de gérer la plateforme {{site.data.keyword.cloud_notm}} proprement dite (gérer des comptes, créer des instances, écrire des règles IAM) ;
  - les rôles de service, qui permettent de gérer des ressources propres aux services (compartiments et objets d'accès).

## Service
{: #terminology-service}

Composant unique de la plateforme {{site.data.keyword.cloud}} (par exemple, {{site.data.keyword.cos_full}}, Cloudant, Fonctions, etc.).
