# Exo Gaulois

Pour les requêtes SQL que tu auras besoin de faire

Sur sql.sh il faudra regarder :

-- SELECT FROM

-- WHERE

-- ORDER BY

-- GROUP BY

-- COUNT

-- SUM

-- DATE_FORMAT

-- INNER JOIN

-- INSERT

-- UPDATE 

-- DELETE

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

### exo3
```
SELECT nom_personnage, sp.nom_specialite, adresse_personnage, l.nom_lieu
FROM personnage p
INNER JOIN specialite sp ON sp.id_specialite = p.id_specialite
INNER JOIN lieu l ON l.id_lieu = p.id_lieu 
ORDER BY l.nom_lieu, p.nom_personnage
```

### exo4
```
SELECT nom_specialite, COUNT(p.id_personnage) AS nbrPersonnages
FROM specialite sp
INNER JOIN personnage p ON sp.id_specialite = p.id_specialite
GROUP BY p.id_specialite
ORDER BY nbrPersonnages DESC
```

### exo5
```
SELECT nom_bataille, DATE_FORMAT(date_bataille, "%d/%m/%Y"), l.nom_lieu
FROM bataille b
INNER JOIN lieu l ON b.id_lieu = l.id_lieu
ORDER BY date_bataille DESC
```

### exo6
```
SELECT nom_potion, SUM(c.qte * i.cout_ingredient) AS prixPotion
FROM potion p
INNER JOIN composer c ON p.id_potion = c.id_potion
INNER JOIN ingredient i ON c.id_ingredient = i.id_ingredient
GROUP BY p.id_potion
ORDER BY prixPotion DESC
```

### exo7
```
SELECT p.nom_potion, i.nom_ingredient, i.cout_ingredient, c.qte
FROM potion p
INNER JOIN composer c ON p.id_potion = c.id_potion
INNER JOIN ingredient i ON c.id_ingredient = i.id_ingredient
WHERE nom_potion = 'Santé'
```

### exo8
```

```

### exo9
```
SELECT p.nom_personnage, b.dose_boire
FROM personnage p
INNER JOIN boire b ON p.id_personnage = b.id_personnage
ORDER BY dose_boire DESC  
```

### exo10
```

```

### exo11
```
SELECT tc.nom_type_casque, COUNT(c.id_type_casque) AS nbrTypeCasques, SUM(c.cout_casque) AS prixTotal
FROM type_casque tc 
INNER JOIN casque c ON tc.id_type_casque = c.id_type_casque
GROUP BY tc.id_type_casque
ORDER BY prixTotal DESC
```

### exo12
```
SELECT nom_potion
FROM potion p
INNER JOIN composer c ON p.id_potion = c.id_potion
INNER JOIN ingredient i ON c.id_ingredient = i.id_ingredient
WHERE nom_ingredient = 'Poisson frais'
```

### exo13
```

```

### exo14
```
SELECT nom_personnage
FROM personnage p
INNER JOIN boire b ON p.id_personnage = b.id_personnage
WHERE NOT EXISTS 

```

### exo15
```

```

Suite 

```
INSERT INTO personnage (nom_personnage, id_specialite, adresse_personnage, id_lieu)
VALUES ('Champdeblix', '12', 'Ferme Hantassion', '6')
```

