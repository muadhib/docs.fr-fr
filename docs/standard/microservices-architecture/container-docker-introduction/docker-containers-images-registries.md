---
title: Registres, des images et des conteneurs docker
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Registres, des images et des conteneurs docker
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 224fed34f06d10760b14aa9ecbae6c0e912915cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="docker-containers-images-and-registries"></a>Registres, des images et des conteneurs docker

Lorsque vous utilisez Docker, un développeur crée une application ou de service, et l'empacte avec ses dépendances dans une image de conteneur. Une image est une représentation statique de l’application ou du service, avec sa configuration et ses dépendances.

Pour exécuter l’application ou le service, l’image de l’application est instanciée pour créer un conteneur, qui est exécuté sur l’hôte Docker. Les conteneurs sont initialement testées dans un environnement de développement ou un PC.

Les développeurs doivent stocker des images dans un Registre, qui agit comme une bibliothèque d’images et est nécessaire lors du déploiement vers les orchestrators de production. Docker conserve un registre public via un [Hub docker](https://hub.docker.com/); les autres éditeurs proposent des registres pour les différentes collections d’images. Également, les entreprises peuvent avoir un Registre privé local pour leurs propres images Docker.

Figure 2-4 indique comment les images et les registres dans Docker se rapportent à d’autres composants. Il montre également les offres de Registre plusieurs provenant de fournisseurs.

![](./media/image5.PNG)

**Figure 2-4**. Taxonomie de Docker termes et concepts

Placer des images dans un Registre vous permet de stocker les bits d’application statique et immuable, y compris toutes leurs dépendances au niveau de l’infrastructure. Ces images peuvent ensuite être créée et déployée dans plusieurs environnements et par conséquent fournissent une unité de déploiement cohérent.

Les registres de l’image privée, soit hébergé localement ou dans le cloud, sont recommandé lorsque :

-   Vos images ne doivent pas être partagés publiquement en raison de la confidentialité.

-   Vous souhaitez avoir une latence réseau minimum entre vos images et votre environnement de déploiement choisi. Par exemple, si votre environnement de production est cloud Azure, vous souhaiterez probablement stocker vos images dans le Registre de conteneur Azure afin que la latence du réseau sera minime. De la même façon, si votre environnement de production sur site, vous souhaiterez ont un local Docker Trusted Registre disponibles dans le même réseau local.

>[!div class="step-by-step"]
[Précédente] (docker-terminology.md) [suivant] (.. /NET-Core-NET-Framework-Containers/index.MD)
