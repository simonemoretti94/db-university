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

***1.*** 

***2.*** 

***3.*** 

***4.*** 

### Joins

***1.*** 

***2.*** 

***3.*** 

***4.*** 

***5*** 

***6.*** 

***7.*** 