# Prompt 1

***1.*** SELECT * FROM `students` WHERE YEAR(date_of_birth) = 1990;

***2.*** SELECT * FROM `courses` WHERE `cfu` > 10;

***3.*** SELECT * FROM `students` WHERE (DATEDIFF(NOW() , `date_of_birth`) / 365.25) > 30;

***4.*** SELECT * FROM `courses` WHERE `year` = 1 AND `period` = 'I semestre';

***5.*** SELECT * FROM `exams` WHERE `date` = '2020-06-20' AND HOUR(hour) >= 14;

***6.*** SELECT * FROM `degrees` WHERE `level` = 'magistrale';

***7.*** SELECT COUNT(id) FROM `departments`;

***8.*** SELECT COUNT(id) AS `n_teacher` FROM `teachers` WHERE `phone` IS NULL;


# Prompt 2

### Group By

***1.*** SELECT COUNT(id) AS `n_students` , YEAR(enrolment_date) AS `enrolment` FROM `students` GROUP BY YEAR(enrolment_date);


***2.*** SELECT COUNT(id) AS `n_teachers`, `office_address` FROM `teachers` GROUP BY `office_address`;

***3.*** SELECT COUNT(exam_id) AS `exam`, ROUND(AVG(vote) , 0) AS `vote_avg` FROM `exam_student` GROUP BY `vote`;

***4.*** SELECT COUNT(id) AS `id_department`, `name` AS `course` FROM `degrees` GROUP BY `name`;

### Joins

***1.*** SELECT * FROM `students` INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`id` = 53;


***2.*** 

***3.*** 

***4.*** 

***5*** 

***6.*** 

***7.*** 