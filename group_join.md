

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

SELECT `courses`.`degree_id`, COUNT(*) AS `numbers_of_courses` FROM `courses`
GROUP BY `courses`.`degree_id`;

<hr>

Joins:


## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.`id` AS `student_id`, `students`.`surname`, `students`.`name`, `students`.`degree_id`, `degrees`.`name` AS `degree_name` 
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia'
ORDER BY `students`.`surname` ASC;


## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT `degrees`.`name`, `degrees`.`level`, `departments`.`name` AS `department_name` , `degrees`.`department_id`
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = 'magistrale'
AND `departments`.`name` = 'Dipartimento di Neuroscienze';

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `course_teacher`.`course_id`, `courses`.`name` AS `name_course`, `teachers`.`name` AS `name_teacher`, `teachers`.`surname` AS `surname_teacher` , `course_teacher`.`teacher_id`  FROM `course_teacher`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `course_teacher`.`teacher_id` = 44;

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT  `students`.`surname`, `students`.`name`, `degrees`.`name` AS `degree_course`, `departments`.`name` AS `department_name`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname` ASC, `students`.`name` ASC;

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.`name` AS `degree_name`, `courses`.`name` AS `course_name`, `teachers`.`surname` AS `teacher_surname`,  `teachers`.`name` AS `teacher_name`
FROM `courses`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
ORDER BY `teacher_surname` ASC, `teacher_name` ASC;


## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT `teachers`.*, `departments`.`name` AS `name_department`
FROM `teachers`
JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica';

## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.