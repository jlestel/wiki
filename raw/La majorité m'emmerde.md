---
title: "La majorité m'emmerde"
source: "https://richard-dern.fr/interets/informatique/2026/04/14/la-majorite-m-emmerde/"
author:
published: 2026-04-14
created: 2026-04-16
description: "Introduction Je ne fais rien comme tout le monde. C’est très frustrant, parce que j’ai l’intime conviction de faire les choses correctement. Mais c’est aussi très valorisant : j’ai …"
tags:
  - "clippings"
---
## Introduction

Je ne fais rien comme tout le monde. C’est très frustrant, parce que j’ai l’intime conviction de faire les choses correctement. Mais c’est aussi très valorisant: j’ai l’impression d’être le détenteur d’un savoir depuis longtemps oublié.

Avant [ChatGPT](https://chatgpt.com/ "Lien externe"), je devais chercher des informations sur Internet à l’aide d’ [un moteur de recherche](https://duckduckgo.com/ "Lien externe"), je faisais des essais et des erreurs. J’avançais vers mon objectif comme on gravit une montagne. Je conquérais mes solutions comme on conquiert un territoire. J’annexais de nouvelles frontières de la connaissance.

Mon temps était utilisé pour une élévation intellectuelle personnelle.

## Connaissance n’est pas statistique

Avec la démocratisation des [LLMs](https://fr.wikipedia.org/wiki/Grand_mod%c3%a8le_de_langage "Lien externe"), l’accès à la connaissance est différent. Elle n’est plus « brute », elle est « pondérée », moyennée. Le LLM, par exemple ChatGPT, tente de deviner le prochain *token* par des moyens statistiques. Pas par une connaissance brute. C’est la raison pour laquelle tout LLM peut se tromper (et normalement, il l’indique quelque part): le prochain *token* est supposé être le plus approprié, mais il n’est pas forcément le plus juste.

En entraînant le modèle, on peut éventuellement atteindre une corrélation parfaite entre ce qui est « supposé approprié » et ce qui est « juste ». Mais [le problème de l’indéterminisme](https://arxiv.org/abs/2408.04667 "Lien externe") des LLMs nous dit que même là, cela ne serait que le fruit du hasard.

## Le problème de la majorité

On entraîne les modèles sur des données qu’on ne maîtrise pas. En gros, ce ne sont pas des physiciens qui donnent des données de physique à ChatGPT et qui vérifient que le modèle recrache des informations pertinentes. Les données d’entraînement sont elles-mêmes des données de référence, et, à en juger par la façon dont les fameux « bots de LLMs » ratissent le web, il est certain que des données réellement utiles (les articles scientifiques, les blogs techniques, la Wikipédia, etc.) se retrouvent mélangées avec des données beaucoup moins pertinentes.

Imaginez noyer la meilleure boisson possible dans de l’eau. Votre boisson n’aura pas le même goût. C’est très exactement pour cela que j’invite à [ne pas bloquer les LLMs](https://richard-dern.fr/interets/informatique/2025/04/02/laisser-l-ia-apprendre-une-position-ethique/ "Laisser l'IA apprendre : une position éthique (02/04/2025)") (en tout cas, ceux qui se comportent correctement). Sans ça, le rapport entre les données pertinentes et les autres est inégal. La connaissance fournie par les LLMs, aussi approximative soit-elle, serait encore plus biaisée.

Mais le vrai fond du problème n’est pas de bloquer les bots ou de les laisser faire, c’est de s’assurer que les données que l’on met soi-même à disposition sont au moins aussi bonnes que celle des autres. Du coup, on alimente les IA avec du contenu très bon en très petite quantité, et du contenu moins bon en très grande quantité. L’intelligence globale en est affaiblie pour tout le monde.

## Mon problème à moi

Lorsque je demande à mon agent d’accomplir une tâche, il le fait plus ou moins bien, en fonction – parfois – de très longues instructions préliminaires (« fais comme ci », « ne fais pas ça »). Ces instructions ne visent pas à faire que l’agent travaillerait comme moi. Elles servent à le rendre moins stupide que la moyenne. Sans ces instructions, il travaillerait « comme tout le monde », c’est-à-dire qu’il serait fainéant.

Pas dans le sens où il produit le moindre effort; non. Au contraire, il me crame mes *tokens* à vitesse grand *V*. Plutôt dans le sens où il fait du *good-enough*. Parce que c’est avec des exemples de code *good-enough* qu’il est entraîné, parce que ces exemples sont les plus économiques, parce que ce sont les plus faciles à trouver sur Internet.

Sauf que, le *good-enough*, c’est ce que veulent 90% des utilisateurs. Et, comme dans toute statistique de ce type, je me trouve dans les 10% restants, mon rapport avec l’IA est spécial: je deviens parfois *toxique pour mon IA*.

## L’enfer, c’est les autres

Exemple concret: mon architecture réseau est une curiosité pour ChatGPT. *Je* suis une curiosité pour *ChatGPT*. Ça ne devrait pas être l’inverse? Bref.

Mon architecture réseau est celle de n’importe quel *adminsys* des années 90-2000: ultra-robuste, 100% locale, 99% auto-gérée. Un routeur derrière lequel j’ai une batterie de serveurs, avec une certaine appétance pour paraphraser la philosophie UNIX: une machine = une mission. Un serveur Web, un serveur domotique, un serveur DNS, etc.

Ça lui troue le cul à ChatGPT. Surtout quand je lui demande d’installer un service «  *qui ne doit pas être exposé sur Internet*  ». Pour lui, systématiquement, ça veut dire «  *qui écoute exclusivement sur localhost*  ». Bah, oui: 90% de ses utilisateurs sont sans doute des *cloud-natives*, des mecs qui crament des AWS ou des Azure sans même se préoccuper de savoir ce qu’ils ont vraiment. «  *Une ligne de conf à changer et mon serveur bah… je sais pas où il est et je m’en fous*  ». Du coup, son serveur, il est exposé directement à Internet. Et donc, pour ChatGPT, mon serveur aussi.

## Les autres me donnent plus de boulot

À cause « des autres », je dois blinder mes *AGENTS.md*, toutes mes instructions hyper-contextualisées, des documents qui par leur simple existence crament mes précieux *tokens* qui ne sont plus alloués à la résolution de mon problème, mais juste à rétablir la vérité. Parce que les statistiques ne penchent pas dans ma balance. Parce que je ne fais rien comme tout le monde.

C’est à cause des autres que je paye 23 euros par mois, et que je vois que j’en fais moins que si je ne payais pas. C’est de la faute des autres si ChatGPT est de moins en moins attractif sur le rapport qualité/prix, et que je passe des heures à bichonner ses instructions au lieu de *produire* activement quelque chose. Ce n’est *pas* de la faute de l’outil, mais de ceux qui ne mettent pas à disposition du contenu de qualité, diversifié.

Attention: ne vous méprenez pas. Je ne dis pas qu’il n’y a que de la merde sur Internet. Mais la merde sur Internet est sacrément sur-représentée. ChatGPT finit bien par résoudre mes problèmes, mais une fois que mes instructions l’ont passé au semis, et parfois, c’est long, et j’ai cramé mes *tokens* hebdomadaires en deux jours.

Aujourd’hui, mon temps est utilisé pour faire que ChatGPT désapprenne ce qu’il pense statistiquement probable pour moi.

## Obsolescence programmée

Le drame dans tout cela est triple.

D’une part, je ne vais pas pouvoir me battre éternellement contre les 90% de gens qui ne font pas comme moi. Mes méthodes, ma façon de faire, vont finir par disparaitre. Pas par obsolescence ni par manque d’intérêt, mais parce qu’il ne sera plus économiquement intéressant de les conserver dans le modèle, ou qu’elles y auront été si diluées qu’elles en perdront toute existence propre.

D’autre part, je ne peux pas revenir en arrière. Aussi approximatives que soient les connaissances de ChatGPT, j’en ai parfois besoin. Je serais encore en train de [me battre avec IPv6](https://richard-dern.fr/interets/informatique/2026/03/04/free-ipv6-et-opnsense/ "Free, IPv6 et OPNsense (04/03/2026)"), par exemple. Et, quand il lit consciencieusement mes instructions, il me fait gagner un temps monumental. Qu’on le veuille ou non, on sera tous dépendant, demain ou dans dix ans, de près ou de loin, de l’IA.

Enfin, quand le moment arrivera où tout ce que je suis, tout ce que je veux diffuser, partira aux chiottes parce que plus personne ne fait les choses comme ça en informatique, tout le monde aura oublié que sans tout ça, sans Merise, sans UML, sans les méthodes de gestion de projet pré-Agile, sans l’ *adminsys*, on n’aurait pas tout ce que l’on a aujourd’hui.

## Conclusion

Je fais mon réseau à ma sauce. Et si ça fait lever le sourcil de quelqu’un, tant pis pour sa tronche. Mais écoutez un peu ce que font les vieux, au lieu de brandir bêtement l’étendard du progrès et du capitalisme. Vos fondations seraient moins branlantes avec un peu plus de sérieux en amont. On verrait moins de conneries sur Internet.

Oui, vous, les jeunes: apprendre à coder, ça ne veut pas dire suivre une formation de 15 jours sur javascript. Je persiste à croire que c’est un art, désormais en voie d’extinction. Et que ce n’est pas parce qu’on n’écrit plus le code nous-même qu’on ne peut pas apprendre à notre amie l’Intelligence Artificielle à mieux faire.

C’est ce qu’ils font en médecine, en économie: ils apprennent à leurs IA à être meilleure qu’eux. Nous, on leur apprend à scier la branche sur laquelle on est assis.