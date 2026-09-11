# preflight-turb-data

Grille de turbulence et de vent en altitude, publiée pour
[Preflight Lens](https://notam.feyndev.com).

Ce dépôt ne contient **que des données générées**. Il n'y a pas de code ici :
le calcul vit dans le dépôt applicatif, privé.

## Ce qu'il y a dedans

La branche **`turb-data`** — et non `main` — porte la grille. Elle est
orpheline et réécrite en force à chaque cycle : un seul commit, jamais
d'historique qui grossit.

```
index.json          le cycle, les échéances, la grille, le pavage, l'encodage
hNNN/rRcC.png       indice de turbulence, un octet par point (EDR x 100)
WIND/hNNN/rRcC.png  vent et écart ISA, trois plans (u, v, dT)
```

Adresse de lecture, avec CORS ouvert :

```
https://raw.githubusercontent.com/MDG64/preflight-turb-data/turb-data/index.json
```

## Rythme

Quatre fois par jour, à HH+4 h 20 des cycles GFS 00/06/12/18 Z. Le cycle
effectivement publié est écrit dans `index.json` — c'est lui qui fait foi, pas
l'horodatage du commit.

## Source et licence

Les champs bruts viennent du **Global Forecast System de la NOAA**
(NCEP, GFS 0,25°), production du gouvernement des États-Unis : domaine public,
libre de réutilisation. La transformation appliquée (indice de type Ellrod
calibré, réduction à un octet, pavage) est publiée ici sous la même liberté
d'usage — reprenez-la si elle vous sert.

Ce qui n'est **pas** couvert par cette phrase : l'application Preflight Lens,
son code et ses autres bases de données, qui restent
« tous droits réservés ».

## Avertissement

Prévision automatique, non vérifiée par un prévisionniste, sans garantie de
disponibilité ni d'exactitude. Aide à la décision avant le vol, jamais un
substitut au dossier météorologique officiel.
