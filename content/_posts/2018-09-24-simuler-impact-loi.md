---
layout: post
title: Simuler l'impact de la loi, c'est possible !
date: 2018-09-24
authors:
  - sandra.chakroun
  - anna-livia.gomart
  - hela.ghariani
categories: dinsic
tags: openfisca mes-aides
image: /img/posts/2018-09-24-simuler-impact-loi.jpg
excerpt: "Vos revenus actuels décideront-ils de vos aides sociales dans deux ans ? Ou, est-il possible de simuler l'impact d'une loi pour que les prestations sociales interviennent au moment où vous en avez besoin ?"
---

## Contexte

Le Groupe de Travail (GT) [Accès aux droits et aux services, lutte contre le non-recours](https://fncp-france.fr/wp-content/uploads/2018/03/rapp-4.pdf) s’applique à proposer des solutions pour permettre à tou·te·s, et surtout aux plus vulnérables, de connaître les moyens d'accompagnement mis à leur disposition.

Dans ce cadre, il a été proposé d’utiliser le logiciel [OpenFisca](https://fr.openfisca.org) en atelier avec une hypothèse : simplifier l'accès au droit passerait par la réduction de la complexité des règles de calcul des prestations sociales.

<!--more-->

Porté par la [Délégation interministérielle à la prévention et à la lutte contre la pauvreté des enfants et des jeunes](https://twitter.com/delegpauvrete) ce GT a été l'opportunité de réunir des experts des prestations sociales, les équipes du simulateur [Mes Aides](https://mes-aides.gouv.fr) et du moteur de calcul [OpenFisca](https://fr.openfisca.org).

> [OpenFisca](https://fr.openfisca.org) est un modèle informatique du système socio-fiscal qui permet de simuler aussi bien la législation actuelle que l‘impact de réformes en discussion au Parlement sur des individus ou des foyers.

> [Mes Aides](https://mes-aides.gouv.fr) se base lui-même sur [OpenFisca-France](https://fr.openfisca.org) pour la simulation du droit aux prestations sociales des particuliers et de ceux qui les accompagnent.

Nous démarrons donc ces ateliers avec un groupe réduit de personnes et l'objectif de simplifier des règles de calcul des prestations sociales.

Les prestations dépendant pour beaucoup des revenus, la première question que nous nous posons est : comment évalue-t-on combien gagne une famille lorsque l’on calcule son éligibilité à une prestation sociale ?

Aujourd’hui, il y a une dizaine de méthodes de calcul des revenus d’un foyer. Ceux-ci peuvent être calculés sur des périodes de temps différentes. Certaines prestations sociales prennent en compte les revenus des 3 derniers mois, d’autres se basent sur le revenu fiscal de référence, calculé sur les revenus N-2 (année - 2). Or, avec le passage au prélèvement à la source de l'impôt sur le revenu, le calcul des prestations sociales pourrait se rapprocher de la situation actuelle des personnes.

Nous avons alors pris le parti d'étudier cela sur des foyers recevant le [RSA](https://fr.openfisca.org/legislation/rsa), la [PPA](https://fr.openfisca.org/legislation/ppa) ou les aides au logement.

Notre hypothèse était qu’en collant plus aux variations de situations des personnes, les aides s’appliqueraient au plus près de leur besoin, et cela simplifierait la compréhension de la façon dont elles sont calculées.

En tant que contributeurs à [OpenFisca](https://fr.openfisca.org), nous voulions aussi savoir :
* dans quelle mesure pouvions-nous utiliser [OpenFisca](https://fr.openfisca.org) pour accompagner la conception d’une réforme ?
* quelle était l'expérience des utilisateurs d'[OpenFisca](https://fr.openfisca.org) qui voulaient simuler l'impact d'une reforme ?

Notre intention était de simuler concrètement une simplification des bases de calcul des prestations sociales, et de définir son impact sur différents types de ménages. Le sujet était encore large et les angles de traitement envisageables variés.
> Exemples illustrant l'ampleur du sujet :
> * multiplicité des [allocations logement](https://www.service-public.fr/particuliers/vosdroits/N20360),
> * règle de calcul de la [base de ressources des aides aux logement](https://fr.openfisca.org/legislation/aide_logement_base_ressources).

Nous nous sommes lancé·e·s dans l'exercice sans vision claire ni du périmètre exact du résultat attendu ni du chemin pour y arriver.

## La rencontre des experts de la loi et des experts du code

Nous avons déterminé 7 scenarios de réformes avec les experts métiers. Nous avons lancé cette initiative sans filet, en nous laissant la possibilité d’adapter notre travail à ce que nous allions découvrir au fur et à mesure. Ceci nous a appris comment faire dialoguer ces deux domaines que sont l'expertise de la loi et le développement informatique : la maïeutique pour partir d'une idée et aller à une réforme calculable.

En bref : temps réduit, environnements techniques très variables, compétences diversifiées.

Nous nous sommes vite rendu compte que pour accompagner au mieux les travaux du GT, nous devions en priorité créer des outils de communication et de visualisation. Nous avons donc réduit au fur et à mesure le périmètre des réformes pour retenir 2 scénarios.

### Simplifier, c'est d'abord comprendre la complexité du droit.

Avant d'écrire une réforme en code informatique, voire même en définir les contours, le premier apprentissage est de comprendre l'esprit de la loi.

Les raisons de chaque subtilité (par exemple, l’effet figé qui consiste à verser un montant identique entre les deux dates d’évaluation d’une aide) doivent être considérées pour savoir quelle typologie de situation sera affectée par la réforme.

Il est facile de se perdre dans la nébuleuse du droit social, même accompagné par des experts.

On se rend compte en discutant avec les participants aux ateliers que la loi a cette mission particulière de considérer toutes les situations de personnes. Et, déterminer combien une personne (ou une famille) gagne aujourd’hui est loin d'être évident :
* Que se passe-t-il si la personne a des revenus qui fluctuent tous les mois ?
* Que se passe-t-il si elle n'est pas salariée ?
* Que se passe-t-il si la personne vient de partir à la retraite ?

### Simplifier les formules ou masquer la complexité ?

Devant la complexité législative inhérente à la diversité des situations familiales, nous nous sommes demandés si l’enjeu de facilitation d'accès au droit ne serait pas dans le masquage de la complexité à l'usager en travaillant l'expérience utilisateur.

C’est le pari du service [Mes Aides](https://mes-aides.gouv.fr), une interface qui structure et simplifie la demande d’information à l’utilisateur, puis qui utilise [OpenFisca](https://fr.openfisca.org) pour calculer les droits sociaux auxquels cet utilisateur peut prétendre.
Une partie de la solution peut se trouver dans l’ordonnancement des informations et la pédagogie.

Les micro-simulateurs comme [OpenFisca](https://fr.openfisca.org) dont la précision de calcul va jusqu'à l'individu ont un rôle à jouer car ils permettent de «Mieux comprendre comment fonctionne le droit adapté à ma situation.».

## Comment les réformes affectent les foyers : un exercice de communication politique

En parallèle des scénarios de réformes, nous avons créé un jeu de situations familiales. Celui-ci permet de tester les réformes sur des cas concrets et de voir comment des changements dans la loi impactent les foyers.
Ces situations (célibataire avec enfants/sans enfant, sénior touchant une retraite…), issues du [livret du pouvoir d'achat du Ministère du Budget](https://www.economie.gouv.fr/files/files/PLF2018/bro-pouvoir-achat-bat-web-10h.pdf), ont été étendues par des situations de personnes aux revenus plus fluctuants.

Nous nous sommes finalement concentrés sur une réforme qui considère les revenus des 12 derniers mois comme base de ressources. Cela nous a en particulier permis de générer les graphiques suivants sur l'aide au logement :

![Graphes de comparaison de différentes bases ressources par cas types](/img/posts/2018-09-24-simuler-impact-loi/comparaison_bases_ressources.png)  
**Comparaison par cas type de différentes bases ressources pour l'aide au logement.**

> Où :  
`Base` est le mode de calcul actuel des aides au logement sur les revenus N-2 récupérés auprès des impôts.  
`AL_MM01` correspond au calcul des aides au logement basé sur les revenus d’activité du mois M-1.  
`AL_MM03` correspond au calcul des aides au logement basé sur les revenus d’activité du dernier trimestre.  
`AL_MM12` correspond au calcul des aides au logement basé sur les revenus d’activité des 12 derniers mois.  


Pour communiquer nos résultats, nous avons voulu générer des graphiques sur la rapidité de prise en compte d’un changement de situation (chômage, augmentation, retraite…) en fonction de la base de ressource prise en compte :  

![Graphes des modes de calcul des aides au logement selon la période des revenus d’activité](/img/posts/2018-09-24-simuler-impact-loi/3_modes.png)  
**3 modes de calcul des aides au logement selon la période des revenus d’activité.**

![Graphes sur la temporalité de l’augmentation de l’aide au logement en cas de baisse de ressources (12 mois)](/img/posts/2018-09-24-simuler-impact-loi/temporalite_al.png)  
**Temporalité de l’augmentation de l’aide au logement en cas de baisse de ressources (12 mois).**

![Graphes de prise en compte des données fiscales, hors revenus d’activité](/img/posts/2018-09-24-simuler-impact-loi/donnees_fiscales.png)  
**Prise en compte des données fiscales, hors revenus d’activité.**


La création de ces graphiques a été chronophage, car nous n’avions pas assez prévu la communication des résultats au début des ateliers. Nous avions dédié plus de temps aux calculs qu'à rendre les résultats lisibles aux yeux des lecteurs, chose qui constitue pourtant la fin de l’exercice.

Cela aussi alors qu'il y avait un enjeu politique fort dans nos travaux. Nous savions que le délégué n'aurait pas pu les annexer au rapport du groupe de travail s’il était dit des choses trop loin de la vision du gouvernement. Le fait que 100% des acteurs présents aient été de l'administration (CAF) a donné une caution à ce qui était produit.

Au final, notre apprentissage principal est qu’[OpenFisca](https://fr.openfisca.org) permet d’ouvrir un espace de dialogue entre les experts de la loi en outillant le calcul et en le rendant plus aisément communicable à d'autres personnes. À la rédaction des réformes, le calculateur a permis d'objectiver les échanges autour de cas concrets. Il a permis d'améliorer la communication sur les réformes mêmes sans en enlever la complexité.

## Si nous refaisions l'exercice, que ferions-nous différemment ?

Cette expérience était complètement nouvelle et ancrée dans le besoin bien réel d’un groupe de travail. Nous en sommes sortis avec une analyse intéressante de ce qu'un tel travail implique.
Tout ne s’est pas passé exactement comme nous l’aurions souhaité et c’est là que se trouvent généralement les meilleurs apprentissages.

Si les situations se représentaient, voici ce que nous ferions différemment :
* Réduire le périmètre législatif : les modifications de la législation sont complexes ; elles demandent de connaître le métier et [OpenFisca-France](https://fr.openfisca.org/legislation) pour bien comprendre les implications des changements. Chaque modification est très chronophage, il faut donc expliciter le périmètre de la réforme très en amont.
* Prioriser une version simplifiée de bout en bout : de la réforme à la visualisation d’impact, avant d’ajouter des cas tests supplémentaires. Ceci pour tester le plus vite possible la réforme sur une situation.
* Identifier les visualisations qui mettront en valeur les résultats.
* Faire des workshops plutôt que des réunions : écrire les réformes et les cas test en séance en binômant métier/tech.

En sortant de cet exercice, nous avons enrichi notre outillage pour accompagner un nouveau type d'utilisateurs :
* des [cas de tests](https://www.data.gouv.fr/fr/datasets/livret-du-pouvoir-dachat/) réutilisables ;
* un [logiciel simplifié](https://repl.it/@openfisca/framework-openfisca-france) qui permet d’automatiser les calculs sur les réformes et extraire les résultats dans un tableur.

## Conclusion

Le logiciel [OpenFisca](https://fr.openfisca.org) peut être utilisé pour créer des simulations de réformes dans le cadre de la création de nouvelles lois.
Son code source ouvert à tous et la forme mathématique des formules permet aux experts métiers et techniques d’échanger sur les méthodes de calcul.
Par ailleurs, la possibilité de simuler l’impact de réformes au niveau des individus et des familles donne des clefs pour mitiger les effets de bords potentiels.
Enfin, la mise à disposition de [cas types](https://www.data.gouv.fr/fr/datasets/livret-du-pouvoir-dachat/) et d’exemples de visualisation permet de donner une base de travail qui peut aussi bien parler aux experts qu’au grand public.

Tout ceci met en oeuvre des compétences variées qui dépassent le champ des prestations sociales pour traiter de l'ensemble du modèle socio-fiscal et faire de ce commun contributif un espace de transparence et de dialogue.

L'aventure vous intéresse ? N'hésitez pas à contacter la [communauté](http://openfisca.org/doc/community.html#contact) pour en savoir plus.

## Pour aller plus loin

* [Rapport final](https://www.caissedesdepotsdesterritoires.fr/cs/BlobServer?blobkey=id&blobnocache=true&blobwhere=1250171076233&blobheader=application%2Fpdf&blobcol=urldata&blobtable=MungoBlobs)
* [Code source des travaux](https://github.com/openfisca/openfisca-events/tree/043a8ea93d48cb7516e188a068d59f80e9c59784/2018-03-gt-non-recours)
* Tester le simulateur [Mes Aides](https://mes-aides.gouv.fr)
* Pour contribuer à OpenFisca, le [code source OpenFisca-France](https://github.com/openfisca/openfisca-france)
* [Explorateur de la législation française](https://fr.openfisca.org/legislation) modélisée
* [Documentation officielle OpenFisca](https://openfisca.org/doc/)
