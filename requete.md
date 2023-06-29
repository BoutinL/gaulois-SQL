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
SELECT DISTINCT nom_lieu
FROM lieu 
INNER JOIN personnage ON lieu.id_lieu = personnage.id_lieu;
SELECT COUNT(*)
FROM personnage
GROUP BY nom_lieu
```