1. Selezionare tutti gli studenti nati nel 1990 (160)

- SELECT * FROM `students` WHERE `date_of_birth` LIKE '1990-%' ORDER BY `date_of_birth` DESC;
<hr>
<br>

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

- SELECT * FROM `courses` WHERE `cfu` > 10;
<hr>
<br>

3. Selezionare tutti gli studenti che hanno più di 30 anni

- SELECT * FROM `students` WHERE TIMESTAMPDIFF(YEAR,`date_of_birth`, CURDATE()) > 30;

<hr>
<br>

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)

- SELECT * FROM `courses` WHERE `period` LIKE 'I semestre' AND `year` LIKE '1';
<hr>
<br>

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)

- SELECT * FROM `exams` WHERE `date` = '2020-06-20' AND `hour` > '14:00';
<hr>
<br>

6. Selezionare tutti i corsi di laurea magistrale (38)

- SELECT * FROM `degrees` WHERE `level` LIKE 'magistrale';
<hr>
<br>

7. Da quanti dipartimenti è composta l'università? (12)

- SELECT COUNT(*) AS 'Total_department' FROM `departments`;
<hr>
<br>

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

- SELECT SUM(`phone` IS NULL) as 'Total_teachers'FROM `teachers`;
<hr>
<br>