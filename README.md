# DB UNIVERSITY;

# GIORNO UNO;

## 1. Selezionare tutti gli studenti nati nel 1990 (160);

SELECT 
    *
FROM
    university.students
WHERE YEAR
    (date_of_birth) = 1990;


## 2. Selezionare tutti i corsi che valgono più di 10 crediti (479);

SELECT 
    *
FROM
    university.courses
WHERE
    `cfu` > 10;


## 3. Selezionare tutti gli studenti che hanno più di 30 anni;

SELECT 
    *
FROM
    university.students
    WHERE `date_of_birth` < CURDATE()- INTERVAL 30 YEAR;


## 4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286);

SELECT 
    *
FROM
    university.courses
WHERE
    `period` = 'I semestre' AND `year` = 1;


## 5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21);

SELECT 
    *
FROM
    university.exams
    WHERE
    `date` = '2020/06/20' AND `hour` > '14:00:00';


## 6. Selezionare tutti i corsi di laurea magistrale (38);

SELECT 
    *
FROM
    university.degrees
    WHERE `level` = "magistrale";

## 7. Da quanti dipartimenti è composta l'università? (12);

SELECT 
COUNT(*)
 FROM university.departments;



## 8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50);

SELECT 
    COUNT(*)
FROM
    university.teachers
    WHERE `phone` IS NULL;


# GIORNO DUE;

# GROUP BY;

## 1. Contare quanti iscritti ci sono stati ogni anno;

SELECT 
        COUNT(*), YEAR(enrolment_date) AS enroled_per_year
    FROM
        students
    GROUP BY enroled_per_year;

## 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio;

SELECT 
COUNT(*), `office_address`
FROM university.teachers
GROUP BY `office_address`;

## 3. Calcolare la media dei voti di ogni appello d'esame;

SELECT 
    exam_id, AVG(vote) AS media_voti
FROM
    university.exam_student
GROUP BY exam_id
ORDER BY media_voti DESC;

## 4. Contare quanti corsi di laurea ci sono per ogni dipartimento;

SELECT 
    department_id, 
    COUNT(*) AS numero_corsi
FROM 
    university.degrees
GROUP BY 
    department_id;

# INNER JOIN;