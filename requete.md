# Exo Gaulois
### exo1
```
SELECT *
FROM lieu
WHERE nom_lieu
LIKE '%um'
```

### exo2
```
SELECT nom_lieu, COUNT(p.id_lieu) AS nbrPersonnages
FROM lieu l
INNER JOIN personnage p ON l.id_lieu = p.id_lieu
GROUP BY l.id_lieu
ORDER BY nbrPersonnages DESC
```