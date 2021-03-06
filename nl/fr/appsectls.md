---

copyright:

  years: 1994, 2018

lastupdated: "2018-05-22"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Retrait de la prise en charge de TLS 1.0 et 1.1
{: #tlssupportwithdraw}

IBM a retiré la prise en charge de TLS 1.0 et TLS 1.1 sur plusieurs produits et services de cloud à compter du 1 mars 2018. TLS 1.2 est pris en charge pour n'importe quel produit ou service {{site.data.keyword.Bluemix_notm}} sur lequel la prise en charge de TLS 1.0 et 1.1 été retirée.
{:shortdesc}

## Pourquoi la prise en charge de version TLS a-t-elle été modifiée ?
{: #why}

La modification de la version TLS prise en charge permet un environnement de cloud sécurisé et conforme aux pratiques recommandées du secteur pour la sécurité et la confidentialité de données.

## Qu'est-ce que TLS ?
{: #what}

Le [protocole TLS  ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://en.wikipedia.org/wiki/Transport_Layer_Security){: new_window} est utilisé pour chiffrer les communications sur un réseau, afin de garantir que les données transmises restent privées. TLS a publié les versions suivantes : 1.0, 1.1 et 1.2. Toutes les connexions HTTPS se servent de TLS. HTTPS est la méthode principale utilisée pour s'assurer que vos connexions vers les produits et services {{site.data.keyword.Bluemix_notm}} sont fiables et sécurisées. Certains produits et services {{site.data.keyword.Bluemix_notm}} permettent des connexions sécurisées via le protocole WSS (WebSocket Secure), lequel utilise également TLS. Le retrait de la prise en charge pour TLS 1.0 et 1.1 concerne aussi bien les connexions HTTPS que WSS.

## Quelles actions dois-je entreprendre pour m'assurer que je ne serai pas impacté ?
{: #impact}

La plupart des connexions vers les produits et services {{site.data.keyword.Bluemix_notm}} utilisent déjà TLS 1.2. Si vos connexions ne requièrent pas TLS 1.0 ou 1.1,  vous n'êtes pas impacté.

Si vous utilisez l'un des produits ou services sur lequel la prise en charge de TLS 1.0 ou 1.1 a été retirée, vous devez vérifier que vos connexions ne requièrent pas la version TLS 1.0 ou 1.1.

### Cloud Foundry sur {{site.data.keyword.Bluemix_notm}}

Pour les applications Cloud Foundry, vous devez vérifier que les connexions de l'extérieur de {{site.data.keyword.Bluemix_notm}} vers votre application ne sont pas impactées. Vérifiez également que les connexions depuis votre application vers une autre application Cloud Foundry sur {{site.data.keyword.Bluemix_notm}} ne sont pas impactées.

Toutes les connexions à Cloud Foundry qui utilisent TLS sont potentiellement impactées, incluant les connexions effectuées depuis des navigateurs Web. Tous les navigateurs récents prennent en charge TLS 1.2, notamment ceux figurant dans les [Prérequis](https://console.bluemix.net/docs/overview/prereqs.html#browsers) pour {{site.data.keyword.Bluemix_notm}}.
{: tip}

#### Connexion à votre application Cloud Foundry

Tous les noeuds finaux d'application Cloud Foundry sur le domaine `*.mybluemix.net` sont accessibles via un noeud final alternatif ne prenant en charge que TLS 1.2.

Pour utiliser le noeud final alternatif, ajoutez `alt.` après le sous-domaine de votre application. Par exemple, si votre application est hébergée à l'adresse `https://myapplication.mybluemix.net`, utilisez `https://myapplication.alt.mybluemix.net`. ou pour `https://myapplication.eu-gb.mybluemix.net`, utilisez `https://myapplication.alt.eu-gb.mybluemix.net`.

Si vous parvenez à vous connecter au noeud final alternatif, vous ne serez pas impacté.

Si vous ne parvenez pas à vous connecter, vous devrez modifier votre client, les bibliothèques client ou la configuration client en activant TLS 1.2.

#### Connexion entre applications Cloud Foundry

Utilisez la commande suivante afin de configurer votre application Cloud Foundry pour redirection automatique vers les noeuds finaux alternatifs disponibles sur le domaine `*.mybluemix.net` lorsque vous vous connectez à d'autres applications :
```
cf set-env <application_name> BLUEMIX_TLS10_DISABLED true
```

Après avoir défini `BLUEMIX_TLS10_DISABLED` à `true`, vous devez utiliser la commande suivante pour reconstituer votre application pour que ce changement prenne effet :
```
cf restage <nom_application>
```

Une fois que vous avez effectué ces changements, toute demande sortante en provenance de votre application est redirigée vers les noeuds finaux alternatifs TLS 1.2 uniquement.

Pour utiliser les noeuds finaux alternatifs, votre client doit prendre en charge l'extension TLS SNI (Server Name Indication). Si ce n'est pas le cas, le certificat retourné risque d'être considéré comme non valide par votre client et vous pourriez supposer à tort que vous êtes impacté par le retrait de TLS 1.0 et 1.1.
{: tip}

### Produits et services Watson

Pour les produits et services Watson, effectuez les remplacements suivants pour vos connexions :
  * Remplacez `gateway.watsonplatform.net` par `gateway-tls12.watsonplatform.net`
  * Remplacez `stream.wastonplatform.net` par `stream-tls12.watsonplatform.net`

Ces noeuds finaux alternatifs ne prennent en charge que TLS 1.2. Si vous parvenez à vous connecter à ces noeuds finaux alternatifs, vous ne serez pas impacté. Si vous ne parvenez pas à vous connecter, vous devrez modifier votre client, les bibliothèques client ou la configuration client en activant TLS 1.2.

Aucun noeud final alternatif pour les produits et services Watson dans des régions autres que Sud des Etats-Unis n'est fourni car elles prennent déjà en charge TLS 1.2.

`gatway-tls12.watsonplatform.net` et `stream-tls12.watsonplatform.net` sont fournis à des fins de test uniquement et ne seront plus disponibles après le retrait de TLS 1.0 et 1.1.
{: tip}

### Autres produits ou services

Pour les produits ou services qui ne disposent pas de noeuds finaux alternatifs accessibles uniquement via TLS 1.2, reportez-vous à la documentation disponible pour votre client ou vos bibliothèques client pour plus d'informations sur l'identification des TLS prises en charge et de la version que vous utilisez.

## Quels sont les produits et services qui retirent leur prise en charge pour TLS 1.0 et 1.1 ?
{: #prodsandservs}

Les produits et services ci-après retirent leur prise en charge pour TLS 1.0 et 1.1.

Certains produits ou services, comme Cloud Foundry on {{site.data.keyword.Bluemix_notm}} et les services du catalogue {{site.data.keyword.Bluemix_notm}} peuvent être proposés dans plusieurs régions différentes. TLS 1.0 et 1.1 seront retirés dans toutes les régions dans lesquelles ils sont actuellement pris en charge.

**Remarque importante :** les déploiements de système {{site.data.keyword.Bluemix_notm}} privé ou {{site.data.keyword.Bluemix_notm}} local ou tous les services {{site.data.keyword.Bluemix_notm}} hébergés dans ces déploiements ne sont pas inclus. Si votre déploiement prend toujours en charge TLS 1.0 ou 1.1, voyez avec votre responsable client ou support quand effectuer le retrait .

### Produits ou services disponibles depuis le catalogue {{site.data.keyword.Bluemix_notm}}

#### Plateforme cloud

* Cloud Foundry sur {{site.data.keyword.Bluemix_notm}}
* Infrastructure {{site.data.keyword.Bluemix_notm}} (`api.softlayer.com` et `api.service.softlayer.com`)

#### API

* API Connect

#### Services d'application

* Business Rules
* Message Hub
* Voice Agent with Watson\*
* Watson Content Knowledge Kits\*

#### Données et analyse

* Compose Enterprise
* Compose for Elasticsearch
* Compose for etcd
* Compose for JanusGraph
* Compose for MongoDB
* Compose for MySQL
* Compose for PostgreSQL
* Compose for RabbitMQ
* Compose for Redis
* Compose for RethinkDB
* Compose for ScyllaDB
* Data Catalog
* Data Connect
* Data Refinery
* Decision Optimization
* Graph
* Informix
* Lift
* Weather Company Data
* Managed MS-SQL Database Server\*

#### DevOps

* Auto-Scaling
* Alert Notification
* Availability Monitoring
* Continuous Delivery
* Continuous Release
* DevOps Insights
* Event Management
* Globalization Pipeline
* Automated Accessibility Tester\*
* Digital Content Checker\*
* Runbook Automation\*

#### Finance

* Historical Instrument Analytics\*
* Instrument Analytics\*
* Investment Portfolio\*
* Portfolio Optimization\*
* Predictive Market Scenarios\*
* Simulated Historical Instrument Analytics\*
* Simulated Instrument Analytics\*

#### Fonctions

* Fonctions

#### Intégration

* App Connect
* Product Insights
* Secure Gateway
* API Harmony\*

#### Internet of Things

* IoT for Electronics

#### Mobile

* App ID†
* Mobile Analytics
* Mobile Foundation
* Push Notifications
* App Launch\*

#### Sécurité

* App ID†
* SSL Certificates†

#### Watson

* Conversation
* Discovery
* Language Translator
* Natural Language Classifier
* Natural Language Understanding
* Personality Insights
* Speech to Text
* Text to Speech
* Tone Analyzer
* Visual Recognition
* Knowledge Studio\*
* Document Conversion‡
* Retrieve & Rank‡
* Tradeoff Analytics‡

\* Disponible dans la catégorie services expérimentaux du catalogue {{site.data.keyword.Bluemix_notm}}.  
† TLS 1.0 a déjà été retiré; seul TLS 1.1 est concerné par le retrait actuel.  
‡ Déprécié, disponible uniquement pour les clients existants.

### Produits ou services disponibles depuis IBM Marketplace

* Forms Experience Builder on Cloud
* IoT for Insurance
* Watson Customer Insight for Insurance
* Watson Marketing Insights
* Watson Knowledge Studio
* Watson Virtual Agent
* Weather Company Energy Trader

### Autres produits ou services
{: #prodservices}

* Teacher Advisor with Watson

## Que faire si mon produit ou service n'est pas répertorié ?
{: #tlsprodnotlisted}

Il se peut que votre produit ou service prenne déjà en charge TLS 1.2 ou que la prise en charge de TLS 1.0 et 1.1 n'ait pas encore été retirée. Vous pouvez utiliser plusieurs clients et outils en ligne pour vérifier si TLS 1.0 et 1.1 sont pris en charge par les noeuds finaux d'un produit ou service.

## Y a-t-il moyen de continuer à utiliser TLS 1.0 ou 1.1 après que sa prise en charge a été retirée ?
{: #tlskeepusing}

Certains produits et services mettent à disposition des noeuds finaux alternatifs qui continuent à prendre en charge TLS 1.0 et 1.1 une fois que ces derniers ont été retirés des noeuds finaux principaux.

### Infrastructure {{site.data.keyword.Bluemix_notm}}

Lors du retrait de la prise en charge de TLS 1.0 et 1.1 de `api.softlayer.com` et de `api.service.softlayer.com`, des noeuds finaux alternatifs seront annoncés et disponibles pendant 30 jours.

### Produits et services Watson
{: #watsonprodservices}

Pour continuer à utiliser TLS 1.0 ou 1.1 pour se connecter aux produits et services Watson après le retrait de la prise en charge de ces protocoles, vous pouvez effectuer l'un des remplacements suivants :
  * Remplacez `gateway.watsonplatform.net` par `gateway-tls10.wastonplatform.net`
  * Remplacez `stream.watsonplatform.net` par `stream-tls10.watsonplatform.net`

Vous pouvez continuer à utiliser `gateway-tls10.watsonplatform.net` et `stream-tls10.watsonplatform.net` pour prendre en charge TLS 1.0, 1.1 et 1.2 après que ces versions TLS ont été retirées de `gateway.watsonplatform.net` et `stream.watsonplatform.net`.

## Contactez-nous
{: #tlssupport}

Si vous avez des questions, des doutes ou des problèmes, [Contactez le support ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/support){: new_window}
