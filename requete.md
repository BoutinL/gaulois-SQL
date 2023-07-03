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
SELECT nom_personnage, SUM(qte) AS totalCasque
FROM personnage p
INNER JOIN prendre_casque pc ON p.id_personnage = pc.id_personnage
INNER JOIN bataille b ON pc.id_bataille = b.id_bataille
WHERE b.id_bataille = '1'
GROUP BY p.id_personnage 
HAVING totalCasque >= ALL (
	SELECT SUM(qte) AS totalCasque
	FROM personnage p
	INNER JOIN prendre_casque pc ON p.id_personnage = pc.id_personnage
	INNER JOIN bataille b ON pc.id_bataille = b.id_bataille
	WHERE b.id_bataille = '1'
	GROUP BY p.id_personnage 
)
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
SELECT nom_bataille, SUM(qte) AS totalCasque
FROM bataille b
INNER JOIN prendre_casque pc ON b.id_bataille = pc.id_bataille
GROUP BY b.id_bataille 
HAVING totalCasque >= ALL (
	SELECT SUM(qte) AS totalCasque
	FROM bataille b
	INNER JOIN prendre_casque pc ON b.id_bataille = pc.id_bataille
	GROUP BY b.id_bataille 
)
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
SELECT nom_lieu, COUNT(p.id_personnage) AS nbrPerso
FROM lieu l
INNER JOIN personnage p ON l.id_lieu = p.id_lieu
WHERE l.id_lieu != '1'
GROUP BY l.id_lieu
HAVING nbrPerso >= ALL (
SELECT COUNT(p.id_personnage) AS nbrPerso
FROM lieu l
INNER JOIN personnage p ON l.id_lieu = p.id_lieu
WHERE l.id_lieu != '1'
GROUP BY l.id_lieu
)
```

### exo14
```
SELECT nom_personnage
FROM personnage p
WHERE p.id_personnage NOT IN (
SELECT id_personnage
FROM boire b
)
```

### exo15
```
SELECT nom_personnage 
FROM personnage p
WHERE p.id_personnage IN (
SELECT id_personnage
FROM autoriser_boire ab
WHERE ab.id_potion != '1'
)
```

Suite 

### A
```
INSERT INTO personnage (nom_personnage, id_specialite, adresse_personnage, id_lieu)
VALUES ('Champdeblix', '12', 'Ferme Hantassion', '6')
```

### B
```
INSERT INTO autoriser_boire (id_potion, id_personnage)
VALUES ('1','12')
```

### C
```
DELETE 
FROM casque c 
WHERE c.id_casque NOT IN (
SELECT id_casque 
FROM prendre_casque pc 
)
```

### D
```
UPDATE personnage 
SET adresse_personnage = 'Condate'
WHERE personnage.id_personnage = '23'
```

### E 
```
DELETE 
FROM composer
WHERE id_potion = '9' AND id_ingredient = '19'
```

### F
```
UPDATE prendre_casque
SET qte = '42', id_casque = '10'
WHERE prendre_casque.id_bataille = '9'
```