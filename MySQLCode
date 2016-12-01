DROP TABLE IF EXISTS resume_company;
DROP TABLE IF EXISTS company_address;
DROP TABLE IF EXISTS company;
DROP TABLE IF EXISTS resume_skill;
DROP TABLE IF EXISTS account_skill;
DROP TABLE IF EXISTS skill;
DROP TABLE IF EXISTS resume_school;
DROP TABLE IF EXISTS resume;
DROP TABLE IF EXISTS account_school;
DROP TABLE IF EXISTS school;
DROP TABLE IF EXISTS address; 
DROP TABLE IF EXISTS account;
DROP PROCEDURE IF EXISTS getAccountCompanies;
DROP PROCEDURE IF EXISTS getSkills;
DROP FUNCTION IF EXISTS avgGPA;
DROP FUNCTION IF EXISTS HasHired;
DROP PROCEDURE IF EXISTS company_info;
DROP PROCEDURE IF EXISTS good_gpa;


CREATE TABLE account( account_id int auto_increment primary key, email varchar(200) unique,
 first_name varchar(100), last_name varchar(100));
 
 CREATE TABLE address(address_id int auto_increment primary key, street varchar(50), zip_code varchar(50));
 
 CREATE TABLE school(school_id int auto_increment primary key, school_name varchar(100) unique, address_id int,
 FOREIGN KEY(address_id) REFERENCES address(address_id) ON DELETE CASCADE);
 
 CREATE TABLE account_school(account_id int, school_id int, primary key(account_id, school_id),
 start_date DATETIME, end_date DATETIME, gpa float(5),
 FOREIGN KEY(account_id) REFERENCES account(account_id) ON DELETE CASCADE,
 FOREIGN KEY(school_id) REFERENCES school(school_id) ON DELETE CASCADE);

 CREATE TABLE resume( resume_id int auto_increment primary key, account_id int, resume_name varchar(100), unique(account_id, resume_id),
 FOREIGN KEY(account_id) REFERENCES account(account_id) ON DELETE CASCADE);

 CREATE TABLE resume_school(resume_id int, school_id int, primary key( resume_id, school_id),
 FOREIGN KEY(resume_id) REFERENCES resume(resume_id) ON DELETE CASCADE,
 FOREIGN KEY(school_id) REFERENCES school(school_id) ON DELETE CASCADE);
 
  CREATE TABLE skill(skill_id int auto_increment primary key, skill_name varchar(100) unique, description varchar(256));
 
 CREATE TABLE account_skill(account_id int, skill_id int, primary key(account_id, skill_id),
 FOREIGN KEY(account_id) REFERENCES account(account_id) ON DELETE CASCADE);
 
 CREATE TABLE resume_skill(skill_id int, resume_id int, primary key(skill_id, resume_id),
FOREIGN KEY(resume_id) REFERENCES resume(resume_id) ON DELETE CASCADE,
FOREIGN KEY(skill_id) REFERENCES skill(skill_id) ON DELETE CASCADE);
 
CREATE TABLE company( company_id int auto_increment primary key, company_name varchar(50) unique);
 
 CREATE TABLE company_address(company_id int, address_id int, primary key(company_id, address_id),
FOREIGN KEY(company_id) REFERENCES company(company_id) ON DELETE CASCADE,
FOREIGN KEY(address_id) REFERENCES address(address_id) ON DELETE CASCADE);

CREATE TABLE resume_company( resume_id int, company_id int, date_shared DATETIME, was_hired bool,
primary key(resume_id, company_id),
FOREIGN KEY(company_id) REFERENCES company(company_id) ON DELETE CASCADE,
FOREIGN KEY(resume_id) REFERENCES resume(resume_id) ON DELETE CASCADE);

CREATE TABLE account_company(account_id int, company_id int, primary key(account_id, company_id),
FOREIGN KEY(account_id) REFERENCES account(account_id) ON DELETE CASCADE,
FOREIGN KEY(company_id) REFERENCES company(company_id) ON DELETE CASCADE);



INSERT into account(email, first_name, last_name)
values('abc@aol.com', 'Dan', 'Thompson');
INSERT into account(email, first_name, last_name)
values('rep@aol.com', 'Archie', 'McGhee');
INSERT into account(email, first_name, last_name)
values('edf@aol.com', 'Sean', 'Cullen');
INSERT into account(email, first_name, last_name)
values('def@aol.com', 'Max', 'Well');
INSERT into account(email, first_name, last_name)
values('123@aol.com', 'Winston', 'Churchill');

INSERT into address(street, zip_code)
values('A Street', '00001');
INSERT into address(street, zip_code)
values('B Street', '00002');
INSERT into address(street, zip_code)
values('C Street', '00003');
INSERT into address(street, zip_code)
values('D Street', '00004');
INSERT into address(street, zip_code)
values('E Street', '00005');

INSERT into school(school_name, address_id)
values('School Uno', 1);
INSERT into school(school_name, address_id)
values('School Deux', 2);
INSERT into school(school_name, address_id)
values('School Trois', 3);
INSERT into school(school_name, address_id)
values('School 4', 4);
INSERT into school(school_name, address_id)
values('School 5', 5);

INSERT into account_school(account_id, school_id, start_date, end_date, gpa) values
(1, 1, '01-02-2016', '01-02-2017', 1.0),
(2, 2, '01-03-2016', '01-03-2017', 3.0),
(3, 3, '01-04-2016', '01-04-2017', 2.0),
(4, 4, '01-05-2016', '01-05-2017', 1.1),
(5, 5, '01-06-016', '01-0-2017', 1.2);

INSERT into resume(account_id, resume_name) values
(1, 'Resume One'),
(2, 'Resume Two'),
(3, 'Resume Three'),
(4, 'Resume Four'),
(5, 'Resume Five');

INSERT into resume_school(resume_id, school_id) values
(1, 1),
(2, 2),
(3, 3),
(4, 4),
(5, 5);

INSERT into skill(skill_name, description) values
("Underwater welding", "For when you drop out and want hazard pay instead"),
("Stuff", "For more stuff"),
("Things", "For things"),
("Skill4", "For having skillz"),
("Skill5", "Moar skillz m8");

INSERT into account_skill(account_id, skill_id) values
(1, 1),
(2, 2),
(3, 3),
(3, 2),
(4, 4),
(5, 5);

INSERT into resume_skill(skill_id, resume_id) values
(1, 1),
(2, 2),
(3, 3),
(4, 4),
(5, 5);

INSERT into company(company_name) values
("Idiots United"),
("Stupidheads Ultd."),
("People"),
("Prestige World-Wide"),
("Bad Company");

INSERT into company_address(company_id, address_id) values
(1, 1),
(2, 2),
(3, 3),
(4, 4),
(5, 5);

INSERT into resume_company(resume_id, company_id, date_shared, was_hired) values
(3, 1, '01-02-2015', 0),
(2, 2, '01-03-2015', 0),
(3, 3, '01-04-2015', 1),
(4, 4, '01-05-2015', 1),
(5, 5, '01-06-2015', 1),
(2, 3, '01-03-2015', 0),
(1, 2, '01-05-2015', 1),
(3, 2, '01-05-2015', 1);

INSERT into account_company(account_id, company_id) values
(1, 1),
(2, 2),
(3, 3),
(4, 4),
(5, 5);

SELECT company_name, AVG(GPA) AS average_gpa
FROM company c
LEFT JOIN resume_company rc ON c.company_id = rc.company_id
LEFT JOIN resume r ON r.resume_id = rc.resume_id
LEFT JOIN resume_school rs ON rs.resume_id = r.resume_id
LEFT JOIN account_school as1 ON as1.account_id = r.account_id
WHERE rc.was_hired = 1
GROUP BY company_name;

SELECT first_name, last_name
FROM account a
LEFT JOIN resume r ON r.account_id = a.account_id
LEFT JOIN resume_company rc ON rc.resume_id = r.resume_id
WHERE rc.was_hired = 1;

SELECT company_name
FROM company c
LEFT JOIN resume_company rc ON c.company_id = rc.company_id
LEFT JOIN resume r ON r.resume_id = rc.resume_id
WHERE account_id = 2;

SELECT COUNT(company_name)
FROM company c
LEFT JOIN resume_company rc ON c.company_id = rc.company_id
LEFT JOIN resume r ON r.resume_id = rc.resume_id
WHERE account_id = 1;

SELECT COUNT(company_name) AS num_shared
FROM company c
LEFT JOIN resume_company rc ON c.company_id = rc.company_id
LEFT JOIN resume r ON r.resume_id = rc.resume_id
WHERE account_id = 1;

SELECT first_name, last_name, COUNT(company_name) AS num_shared
FROM company c
RIGHT JOIN resume_company rc ON c.company_id = rc.company_id
RIGHT JOIN resume r ON r.resume_id = rc.resume_id
RIGHT JOIN account a ON a.account_id = r.account_id
GROUP BY first_name, last_name;

SELECT first_name, last_name, COUNT(company_name) AS num_shared
FROM company c
RIGHT JOIN resume_company rc ON c.company_id = rc.company_id
RIGHT JOIN resume r ON r.resume_id = rc.resume_id
RIGHT JOIN account a ON a.account_id = r.account_id
GROUP BY first_name, last_name
ORDER BY last_name;

SELECT first_name, last_name, COUNT(company_name) AS num_shared
FROM company c
RIGHT JOIN resume_company rc ON c.company_id = rc.company_id
RIGHT JOIN resume r ON r.resume_id = rc.resume_id
RIGHT JOIN account a ON a.account_id = r.account_id
GROUP BY first_name, last_name
HAVING COUNT(num_shared) > 1;

CREATE or REPLACE view AccountCompanyView as
SELECT c.company_id, company_name, email,a.account_id, first_name, last_name, was_hired
FROM account a
join resume r on r.account_id = a.account_id
join resume_company rc on rc.resume_id = r.resume_id
join company c on c.company_id = rc.company_id
WHERE EXISTS(SELECT a.account_id FROM resume_company);
SELECT * from AccountCompanyView WHERE email = 'edf@aol.com' and was_hired = 1;

#View used for last function
CREATE or REPLACE view getGpas as
SELECT company_name, AVG(GPA) AS av_gpa
FROM company c
JOIN resume_company rc ON c.company_id = rc.company_id
JOIN resume r ON r.resume_id = rc.resume_id
JOIN resume_school rs ON rs.resume_id = r.resume_id
JOIN account_school as1 ON as1.account_id = r.account_id
GROUP BY company_name;


DELIMITER //
 CREATE PROCEDURE getAccountCompanies(_email varchar(100))
   BEGIN
   SELECT company_name, company_id, was_hired from AccountCompanyView WHERE email = _email;
END //
DELIMITER ;

CALL getAccountCompanies('edf@aol.com');

CREATE or REPLACE view AccountSkills as
SELECT a.*, s.*
FROM account a
join account_skill acs on acs.account_id = a.account_id
join skill s on s.skill_id = acs.skill_id;

DELIMITER //
 CREATE PROCEDURE getSkills(_email varchar(100))
   BEGIN
   SELECT account_id, email, skill_name from AccountSkills WHERE email = _email;
END //
DELIMITER ;

#Call the procedure
CALL getSkills('edf@aol.com');
select * from AccountSkills

DELIMITER //
 CREATE FUNCTION avgGPA(_company_name varchar(100)) RETURNS float
   BEGIN
   DECLARE avGPA float;
   SELECT av_gpa into avGPA
   FROM getGpas
   WHERE company_name = _company_name;
   return avGPA;
   
   END//
   DELIMITER ;
   
   select company_name, avgGPA(company_name) FROM company;
   
   CREATE or REPLACE view company_resume_statistics as
   SELECT c.company_id, company_name, COUNT(rc.resume_id) AS num_shared, AVG(acs.gpa) as aGPA, SUM(was_hired) as num_hired 
   FROM company c
   join account_company ac on ac.company_id = c.company_id
   join account_school acs on acs.account_id = ac.account_id
   join resume_company rc on rc.company_id = c.company_id
   WHERE was_hired = 1
   GROUP by company_name;
   select * from company_resume_statistics;
   
   DELIMITER //
   CREATE PROCEDURE company_info(_company_id int)
   BEGIN
   SELECT * FROM company_resume_statistics where company_id = _company_id;
   END//
   DELIMITER ;
   #BELOW IS AN EXAMPLE OF A CALL TO ABOVE PROCEDURE
   CALL company_info(3);
   
   DELIMITER //
   CREATE PROCEDURE good_gpa(num float)
   BEGIN 
   SELECT * FROM company_resume_statistics WHERE aGPA >= num;
   END//
   DELIMITER ;
   #Calls to prove procedure works
   CALL good_gpa(1.2);
   
   
   DELIMITER //
	CREATE FUNCTION hasHired(_company_name varchar(100)) RETURNS boolean
    BEGIN
    DECLARE _hired int;
    DECLARE _hired_ boolean;
    SELECT num_hired into _hired
    FROM company_resume_statistics WHERE company_name = _company_name;
    IF _hired > 0 THEN set _hired_ = 1;
    ELSE set _hired_ = 0;
    END IF;
    RETURN _hired_;
    END//
    DELIMITER ;
    
    SELECT company_name, hasHired(company_name) from company;

		
create or replace view school_view as
select s.*, a.street, a.zip_code from school s
join address a on a.address_id = s.address_id;
Select * from school_view;	

CREATE OR REPLACE VIEW resume_view as
select r.*, a.first_name, a.last_name from resume r
join account a on a.account_id = r.account_id;
select * from resume_view;

CREATE OR REPLACE VIEW account_view as
select a.* from account a;
select * from account_view;

CREATE OR REPLACE VIEW skill_view as
select s.* from skill s;
select * from skill_view;

CREATE OR REPLACE VIEW company_view as 
select c.* from company c;

CREATE OR REPLACE VIEW address_view as
select a.* from address a;

DROP PROCEDURE IF EXISTS company_getinfo;
 DELIMITER //
 CREATE PROCEDURE company_getinfo (_company_id int)
 BEGIN
 SELECT * FROM company WHERE company_id = _company_id;
 SELECT a.*, s.company_id FROM address a
 LEFT JOIN company_address s on s.address_id = a.address_id AND company_id = _company_id;
 END //
 DELIMITER ;
 
