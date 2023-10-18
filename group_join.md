

Group by:

## Contare quanti iscritti ci sono stati ogni anno

SELECT YEAR(`students`.`enrolment_date`) AS `current_year`, 
COUNT(*) AS `total_subscriptions` FROM `students` 
GROUP BY `current_year`
ORDER BY `current_year` DESC;


## Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT `teachers`.`office_address` AS `address_name`,
COUNT(*) AS `teacher_with_same_office` FROM `teachers`
GROUP BY `address_name`
ORDER BY `address_name` ASC;

## Calcolare la media dei voti di ogni appello d'esame

SELECT AVG(`exam_student`.`vote`) AS `average_vote`, `exam_id` FROM `exam_student`
GROUP BY `exam_id`
ORDER BY `average_vote` DESC;

## Contare quanti corsi di laurea ci sono per ogni dipartimento


Joins:


## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.