# Mon suivi football

## Match de la saison
Du 27/06/2026 au 08/08/2026, du plus ancien au plus récent.
```dataview
TABLE date AS "Date", adversaire AS "Adversaire", resultat AS "Resultat", minute AS "Minute"
FROM "Match"
SORT date ASC
```

## Bilan des match
```dataview
TABLE WITHOUT ID key AS "Resultat", length(rows) AS "Nombre de match"
FROM "Match"
GROUP BY resultat
```

## Entrainement par type
```dataview
TABLE WITHOUT ID key AS "Type", sum(rows.duree) AS "Duree", length(rows) AS "Seance"
FROM "entrainement"
GROUP BY type
```

## Competence a travailler
```dataview
TABLE categorie AS "Categorie", niveau AS "Niveau"
FROM "competence"
WHERE !atteint
SORT niveau ASC
```

## Objectif en cours
```dataview
TABLE actuel AS "Actuel", cible AS "Cible", "<progress value='" + actuel + "' max='" + cible + "'></progress>" AS "Progression"
FROM "objectif"
WHERE !atteint
```

## Objectif atteint
```dataview
LIST
FROM "objectif"
WHERE atteint
```

## A faire
```dataview
TASK
WHERE !completed
GROUP BY file.link
```

## Calendrier de la saison
```dataview
CALENDAR date
FROM "Match" OR "entrainement"
```


[[Saison Abidjan 2026]] · [[Objectif pour la saison 2026-2027]] · [[Ideation]]

