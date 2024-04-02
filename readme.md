# Prompt 1

***1.*** 
SELECT *
FROM `students` WHERE YEAR(date_of_birth) = 1990;

***2.*** 
SELECT *
FROM `courses` WHERE `cfu` > 10;

***3.***
SELECT *
FROM `students`
WHERE (DATEDIFF(NOW() , `date_of_birth`) / 365.25) > 30;

***4.***
SELECT *
FROM `courses`
WHERE `year` = 1 AND `period` = 'I semestre';

***5.***
SELECT *
FROM `exams`
WHERE `date` = '2020-06-20' AND HOUR(hour) >= 14;

***6.***
SELECT *
FROM `degrees`
WHERE `level` = 'magistrale';

***7.***
SELECT COUNT(id)
FROM `departments`;

***8.***
SELECT COUNT(id) AS `n_teacher`
FROM `teachers`
WHERE `phone` IS NULL;


# Prompt 2

### Group By

***1.***
SELECT COUNT(id) AS `n_students` ,
YEAR(enrolment_date) AS `enrolment`
FROM `students`
GROUP BY YEAR(enrolment_date);


***2.***
SELECT COUNT(id) AS `n_teachers`,
`office_address`
FROM `teachers`
GROUP BY `office_address`;

***3.***
SELECT COUNT(exam_id) AS `exam`,
ROUND(AVG(vote) , 0) AS `vote_avg`
FROM `exam_student`
GROUP BY `vote`;

***4.***
SELECT COUNT(id) AS `id_department`,
`name` AS `course`
FROM `degrees`
GROUP BY `name`;

### Joins

***1.*** SELECT *
FROM `students`
INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`id` = 53;


***2.*** SELECT *
FROM `degrees`
INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = 'magistrale' AND `degrees`.`department_id` = 7;


***3.***
SELECT `course_id`
FROM `course_teacher`
INNER JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` WHERE `teachers`.`name`= 'Fulvio' AND `teachers`.`surname` = 'Amato';

***4.*** 
SELECT * 
FROM ((`students` 
INNER JOIN `degrees` ON `students`.`degree_id`= `degrees`.`id`) INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`)
ORDER BY `students`.`surname`, `students`.`name`;

***5***
SELECT
`courses`.`id` AS `ID_course`,
`course_teacher`.`teacher_id` AS `ID_teacher`,
`teachers`.`name` , `teachers`.`surname`
FROM ((`courses`
INNER JOIN `course_teacher`ON `courses`.`id` = `course_teacher`.`course_id` )
INNER JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`);

***6.*** 
SELECT `teachers`.`name`, `teachers`.`surname` , `departments`.`name` 
FROM `teachers`
INNER JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
INNER JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
INNER JOIN `exams` ON `courses`.`id` = `exams`.`course_id`
INNER JOIN `exam_student` ON `exams`.`id` = `exam_student`.`exam_id`
INNER JOIN `students` ON `exam_student`.`student_id` = `students`.`id`
INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica';

***7.*** 
SELECT COUNT(exam_student.student_id) AS `times_id`,
`students`.`name` ,
`students`.`surname`
FROM `exam_student`
INNER JOIN `students` ON `exam_student`.`student_id` = `students`.`id`
WHERE `exam_student`.`vote` >= 18
GROUP BY `exam_student`.`student_id`;

