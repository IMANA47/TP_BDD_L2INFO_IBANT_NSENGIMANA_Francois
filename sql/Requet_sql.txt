-- ============================================================================
-- TP BASE DE DONNEES - L2 INFORMATIQUE IBANT
-- Année académique: 2025-2026
-- ============================================================================

-- ============================================================================
-- 1. CREATION DE LA BASE DE DONNEES
-- ============================================================================
CREATE DATABASE ecole;

USE ecole;

-- ============================================================================
-- 2. CREATION DES TABLES
-- ============================================================================
CREATE TABLE
    Classe (
        code_class VARCHAR(8) PRIMARY KEY,
        libelle_class VARCHAR(40) NOT NULL
    );

CREATE TABLE
    Matiere (
        code_mat VARCHAR(8) PRIMARY KEY,
        libelle_mat VARCHAR(40) NOT NULL
    );

CREATE TABLE
    Etudiant (
        id INT PRIMARY KEY AUTO_INCREMENT,
        Matri_et VARCHAR(16) UNIQUE NOT NULL,
        nom_et VARCHAR(40) NOT NULL,
        prenom_et VARCHAR(30) DEFAULT 'Prenom indefini',
        datenais_et DATE NOT NULL DEFAULT CURDATE(),
        sexe_et VARCHAR(40) NOT NULL,
        nationalite_et VARCHAR(40) NOT NULL,
        contact_et VARCHAR(40) NOT NULL,
        code_class VARCHAR(8),
        FOREIGN KEY (code_class) REFERENCES Classe (code_class)
    );

CREATE TABLE
    Dispenser (
        code_class VARCHAR(8),
        code_mat VARCHAR(8),
        coeff NUMERIC DEFAULT 0,
        PRIMARY KEY (code_class, code_mat),
        FOREIGN KEY (code_class) REFERENCES Classe (code_class),
        FOREIGN KEY (code_mat) REFERENCES Matiere (code_mat)
    );

CREATE TABLE
    Noter (
        id INT,
        code_mat VARCHAR(8),
        note_et NUMERIC DEFAULT 0,
        PRIMARY KEY (id, code_mat),
        FOREIGN KEY (id) REFERENCES Etudiant (id),
        FOREIGN KEY (code_mat) REFERENCES Matiere (code_mat)
    );

-- ============================================================================
-- 3. INSERTIONS DE DONNEES
-- ============================================================================
-- Insertion des classes
INSERT INTO
    Classe (code_class, libelle_class)
VALUES
    (
        '1AIGN',
        'Première année Informatique Génie Numérique'
    ),
    (
        '2AIGT',
        'Deuxième année Informatique Génie Technologique'
    ),
    (
        '3AIGI',
        'Troisième année Informatique Génie Informatique'
    );

-- Insertion des Matieres (15+)
INSERT INTO
    Matiere (code_mat, libelle_mat)
VALUES
    ('MATBD001', 'Base de Données'),
    ('MATPPY00', 'Programmation en Python'),
    ('MATSE003', 'Système d''exploitation'),
    ('MATAO004', 'Architecture des ordinateurs'),
    ('MATALGO0', 'Algorithmes Avancés'),
    ('MATDW006', 'Développement Web'),
    ('MATRI007', 'Réseau Informatique'),
    ('MATSI008', 'Sécurité Informatique'),
    ('MATGN009', 'Génie Logiciel'),
    ('MATAI010', 'Intelligence Artificielle'),
    ('MATBD201', 'Bases de Données Avancées'),
    ('MATDBA01', 'Administration de Bases de Données'),
    ('MATCC013', 'Cloud Computing'),
    ('MATPM014', 'Programmation Mobile'),
    ('MATQL015', 'Qualité de Logiciel');

-- Insertion des étudiants (30 étudiants)
INSERT INTO
    Etudiant (Matri_et,nom_et,prenom_et,datenais_et,sexe_et,nationalite_et,contact_et,code_class)
VALUES ('EAD20250001','Oko','Jean','2005-03-15','M','Congolais','0601234567','1AIGN'),
    ('EAD20250002','Ngala','Marie','2005-05-22','F','Congolais','0601234568','1AIGN'),
    ('EAD20250003','Oyombi','Pierre','2005-07-10','M','Beninois','0601234569','1AIGN'),
    ('EAD20250004','Ngakoso','Sophie','2005-02-14','F','Tchad','0601234570','1AIGN'),
    ('EAD20250005','Mbemba','Luc','2005-09-08','M','Belgique','0601234571','1AIGN'),
    ('EAD20250006','Mafouta','Anne','2005-11-20','F','Congolais','0601234572','1AIGN'),
    ('EAD20250007','Boboko','Marc','2005-04-16','M','Beninois','0601234573','1AIGN'),
    ('EAD20250008','Ngatsie','Isabelle','2005-08-25','F','RDC','0601234574','1AIGN'),
    ('EAD20250009','Pemba','François','2005-06-12','M','Congolais','0601234575','1AIGN'),
    ('EAD20250010','Morel','Claire','2005-01-30','F','Beninois','0601234576','1AIGN'),
    ('EAD20250011','Mougala','Thierry','2005-10-05','M','Cameroun','0601234577','1AIGN'),
    ('EAD20250012','Yoyo','Nathalie','2005-12-18','F','Côte d''Ivoire','0601234578','1AIGN'),
    ('EAD20250013','Koulman','Olivier','2005-03-09','M','Sénégal','0601234579','1AIGN'),
    ('EAD20250014','Guie','Valérie','2005-07-21','F','Mali','0601234580','1AIGN'),
    ('EAD20250015','Tsotsolo','Christophe','2005-05-11','M','Congolais','0601234581','1AIGN'),
    ('EAD20250016','Saraka','Sylvie','2004-09-27','F','Beninois','0601234582','2AIGT'),
    ('EAD20250017','Boumie','Alain','2004-11-14','M','Congolais','0601234583','2AIGT'),
    ('EAD20250018','Mampassi','Muriel','2004-02-03','F','Burkina Faso','0601234584','2AIGT'),
    ('EAD20250019','Nguesso','Denis','2004-06-19','M','Togo','0601234585','2AIGT'),
    ('EAD20250020','Dongo','Émilie','2004-08-08','F','Congolais','0601234586','2AIGT'),
    ('EAD20250021','Popo','Bernard','2004-12-25','M','Beninois','0601234587','2AIGT'),
    ('EAD20250022','Oyamba','Valentine','2004-04-30','F','Rwanda','0601234588','2AIGT'),
    ('EAD20250023','Danzo','Fabrice','2004-10-17','M','Congolais','0601234589','2AIGT'),
    ('EAD20250024','Kokoli','Lucie','2004-01-26','F','RDC','0601234590','2AIGT'),
    ('EAD20250025','Lefort','Maxime','2004-07-13','M','Beninois','0601234591','2AIGT'),
    ('EAD20250026','Massolo','Céline','2004-03-06','F','Congolais','0601234592','2AIGT'),
    ('EAD20250027','Sosoli','Yves','2004-09-22','M','Cameroun','0601234593','2AIGT'),
    ('EAD20250028','Bembele','Sandrine','2003-05-31','F','Gabon','0601234594','3AIGI'),
    ('EAD20250029','Rokoga','Julien','2003-11-15','M','Congolais','0601234595','3AIGI'),
    ('EAD20250030','Deniga','Francine','2003-02-28','F','Beninois','0601234596','3AIGI');

-- Insertion des dispenses (18 insertions)
INSERT INTO
    Dispenser (code_class, code_mat, coeff)
VALUES
    ('1AIGN', 'MATBD001', 4),
    ('1AIGN', 'MATPPY00', 3),
    ('1AIGN', 'MATSE003', 3),
    ('1AIGN', 'MATAO004', 3),
    ('1AIGN', 'MATALGO0', 2),
    ('1AIGN', 'MATDW006', 2),
    ('2AIGT', 'MATBD001', 3),
    ('2AIGT', 'MATPPY00', 2),
    ('2AIGT', 'MATSE003', 2),
    ('2AIGT', 'MATDW006', 4),
    ('2AIGT', 'MATRI007', 3),
    ('2AIGT', 'MATSI008', 2),
    ('2AIGT', 'MATGN009', 3),
    ('3AIGI', 'MATBD001', 2),
    ('3AIGI', 'MATAI010', 4),
    ('3AIGI', 'MATBD201', 3),
    ('3AIGI', 'MATDBA01', 3),
    ('3AIGI', 'MATCC013', 2);

-- Insertion des notes (30 insertions)
INSERT INTO
    Noter (id, code_mat, note_et)
VALUES
    (1, 'MATBD001', 15),
    (1, 'MATPPY00', 14),
    (2, 'MATBD001', 16),
    (2, 'MATSE003', 13),
    (3, 'MATBD001', 12),
    (3, 'MATAO004', 14),
    (4, 'MATBD001', 18),
    (4, 'MATPPY00', 17),
    (5, 'MATBD001', 11),
    (5, 'MATALGO0', 12),
    (6, 'MATBD001', 19),
    (6, 'MATSE003', 15),
    (7, 'MATBD001', 13),
    (7, 'MATDW006', 14),
    (8, 'MATBD001', 17),
    (8, 'MATPPY00', 16),
    (9, 'MATBD001', 14),
    (9, 'MATAO004', 15),
    (10, 'MATBD001', 16),
    (10, 'MATSE003', 13),
    (16, 'MATBD001', 6),
    (16, 'MATDW006', 8),
    (17, 'MATBD001', 8),
    (17, 'MATPPY00', 7),
    (18, 'MATDW006', 9),
    (18, 'MATBD001', 5),
    (19, 'MATBD001', 7),
    (19, 'MATRI007', 6),
    (20, 'MATDW006', 14),
    (20, 'MATBD001', 16),
    (20, 'MATSE003', 13),
    (26, 'MATBD001', 6),
    (26, 'MATDW006', 8),
    (27, 'MATBD001', 8),
    (27, 'MATPPY00', 7),
    (28, 'MATDW006', 9),
    (28, 'MATBD001', 5),
    (29, 'MATBD001', 7),
    (29, 'MATRI007', 6),
    (30, 'MATBD001', 15),
    (30, 'MATDW006', 14);

-- ============================================================================
-- 4. REQUETES SQL (Questions a à o)
-- ============================================================================
-- a) Lister les étudiants de chaque classe
-- (code_class, matri_et, prenom_et, sexe_et, nationalite_et) 
-- en ordre croissant de nom et prénom
SELECT
    c.code_class,
    e.Matri_et,
    e.prenom_et,
    e.sexe_et,
    e.nationalite_et
FROM
    Etudiant e
    JOIN Classe c ON e.code_class = c.code_class
ORDER BY
    e.nom_et ASC,
    e.prenom_et ASC;

-- b) Afficher les classes qui ont au moins 10 étudiants
-- (code_class, nombre d'étudiants)
SELECT
    c.code_class,
    COUNT(e.id) AS nombre_etudiants
FROM
    Classe c
    JOIN Etudiant e ON c.code_class = e.code_class
GROUP BY
    c.code_class
HAVING
    COUNT(e.id) >= 10;

-- c) Trouver la Matiere qui a le plus gros coefficient
-- (libelle_mat, coeff)
SELECT
    m.libelle_mat,
    MAX(d.coeff) AS coeff
FROM
    Matiere m
    JOIN Dispenser d ON m.code_mat = d.code_mat
GROUP BY
    m.libelle_mat
ORDER BY
    coeff DESC
LIMIT
    1;

-- d) Déterminer dans chaque classe quelle est la Matiere qui a le plus gros coefficient
-- (code_class, code_mat, coeff)
SELECT
    d.code_class,
    d.code_mat,
    d.coeff
FROM
    Dispenser d
WHERE
    d.coeff = (
        SELECT
            MAX(d2.coeff)
        FROM
            Dispenser d2
        WHERE
            d2.code_class = d.code_class
    )
ORDER BY
    d.code_class;

-- e) Lister par pays et par classe, les étudiants de ce pays 
-- en ordre décroissant des noms et prénoms
-- (nationalité, code classe, nom et prénom, sexe)
SELECT
    e.nationalite_et,
    c.code_class,
    e.nom_et,
    e.prenom_et,
    e.sexe_et
FROM
    Etudiant e
    JOIN Classe c ON e.code_class = c.code_class
ORDER BY
    e.nationalite_et ASC,
    c.code_class ASC,
    e.nom_et DESC,
    e.prenom_et DESC;

-- f) Trouver la Matiere (ou les Matieres) qui n'est enseigné dans aucune classe
-- (libelle_mat)
SELECT
    m.libelle_mat
FROM
    Matiere m
WHERE
    m.code_mat NOT IN(
        SELECT DISTINCT
            d.code_mat
        FROM
            Dispenser d
    );

-- g) Lister les Matieres qui ne sont pas enseignées en '1AIGN'
-- (code_mat, libelle_mat)
SELECT
    d.code_mat,
    m.libelle_mat
FROM
    Matiere m
    LEFT JOIN Dispenser d ON m.code_mat = d.code_mat
    AND d.code_class = '1AIGN'
WHERE
    d.code_mat IS NULL;

-- h) Lister quel est le pays qui a le plus d'étudiants
-- (nationalité, nombre d'étudiant)
SELECT
    e.nationalite_et,
    COUNT(e.id) AS nombre_etudiants
FROM
    Etudiant e
GROUP BY
    e.nationalite_et
ORDER BY
    nombre_etudiants DESC
LIMIT
    1;

-- i) Donner la classe (ou les classes) où il y a plus de filles
-- (libelle_class, nombre de filles)
SELECT
    c.libelle_class,
    COUNT(e.id) AS nombre_filles
FROM
    Classe c
    JOIN Etudiant e ON c.code_class = e.code_class
WHERE
    e.sexe_et = 'F'
GROUP BY
    c.code_class,
    c.libelle_class
HAVING
    COUNT(e.id) = (
        SELECT
            MAX(cnt)
        FROM
            (
                SELECT
                    COUNT(e2.id) AS cnt
                FROM
                    Etudiant e2
                WHERE
                    e2.sexe_et = 'F'
                GROUP BY
                    e2.code_class
            ) AS sub
    );

-- j) Donner la classe (ou les classes) où il y a plus de filles que les garçons
-- (libelle_class, nombre de filles, nombre de garçons)
SELECT
    c.libelle_class,
    SUM(
        CASE
            WHEN e.sexe_et = 'F' THEN 1
            ELSE 0
        END
    ) AS nombre_filles,
    SUM(
        CASE
            WHEN e.sexe_et = 'M' THEN 1
            ELSE 0
        END
    ) AS nombre_garcons
FROM
    Classe c
    JOIN Etudiant e ON c.code_class = e.code_class
GROUP BY
    c.code_class,
    c.libelle_class
HAVING
    SUM(
        CASE
            WHEN e.sexe_et = 'F' THEN 1
            ELSE 0
        END
    ) > SUM(
        CASE
            WHEN e.sexe_et = 'M' THEN 1
            ELSE 0
        END
    );

-- k) Les étudiants Beninoisois ne fréquentent plus l'EAD
-- Note: Il faut d'abord supprimer les notes associées à ces étudiants avant de supprimer les étudiants eux-mêmes
-- Étape 1 : supprimer toutes les notes de l’étudiant béninois
DELETE FROM Noter
WHERE id IN (
    SELECT id FROM Etudiant WHERE nationalite_et = 'Beninois'
);

-- Étape 2 : supprimer l’étudiant béninois
DELETE FROM Etudiant
WHERE nationalite_et = 'Beninois';

-- l) Augmenter d'un demi-point la note de Base de données 
-- à tous les étudiants de la '2AIGT' qui ont une note en dessous de 7
UPDATE Noter
SET
    note_et = note_et + 0.5
WHERE
    code_mat = 'MATBD001'
    AND id IN (
        SELECT
            e.id
        FROM
            Etudiant e
        WHERE
            e.code_class = '2AIGT'
    )
    AND note_et < 7;

-- m) Augmenter d'un point la note de Base de données 
-- à tous les étudiants de la '2AIGT' qui ont une note supérieure à 7
UPDATE Noter
SET
    note_et = note_et + 1
WHERE
    code_mat = 'MATBD001'
    AND id IN (
        SELECT
            e.id
        FROM
            Etudiant e
        WHERE
            e.code_class = '2AIGT'
    )
    AND note_et > 7;

-- n) Quelle est la classe qui contient le plus d'étudiants ?
-- (code_class, libelle_class, nombre d'étudiants)
SELECT
    c.code_class,
    c.libelle_class,
    COUNT(e.id) AS nombre_etudiants
FROM
    Classe c
    JOIN Etudiant e ON c.code_class = e.code_class
GROUP BY
    c.code_class,
    c.libelle_class
ORDER BY
    nombre_etudiants DESC
LIMIT
    1;

-- o) Calculer pour chaque étudiant sa moyenne tenant compte des notes obtenues et des coefficients des Matieres
-- (matri_et, nom_et, moyenne calculée)
SELECT
    e.Matri_et,
    e.nom_et,
    ROUND(SUM(n.note_et * d.coeff) / SUM(d.coeff), 2) AS moyenne_calculee
FROM
    Etudiant e
    JOIN Noter n ON e.id = n.id
    JOIN Dispenser d ON n.code_mat = d.code_mat
    AND e.code_class = d.code_class
GROUP BY
    e.id,
    e.Matri_et,
    e.nom_et
ORDER BY
    e.nom_et ASC;

-- ============================================================================
-- FIN DES REQUETES
-- ============================================================================