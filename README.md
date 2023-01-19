/*Select users table*/
SELECT * FROM users;


/*Select progress table*/
SELECT * FROM users;


/*What are the Top 25 schools (.edu domains)?*/
SELECT  email_domain AS Email FROM users 
WHERE email_domain LIKE '%.edu'
LIMIT 25;


/*How many .edu learners are located in New York?*/
SELECT city,COUNT(user_id) as no_of_users FROM users WHERE city='New York';


 /*How many of these Codecademy learners are using the mobile app?*/
 SELECT mobile_app, COUNT(mobile_app) as no_of_users
 FROM users
 GROUP BY 1;
 
 /*Use strfttime*/
 SELECT strftime ('%H', sign_up_at), COUNT(*)
 FROM users
 GROUP BY 1;
 
 /*Do different schools (.edu domains) prefer different courses?*/
SELECT users.email_domain, progress.learn_cpp, progress.learn_sql, progress.learn_html, progress.learn_javascript, progress.learn_java
FROM users 
LEFT JOIN progress 
ON users.user_id = progress.user_id
GROUP BY 1
ORDER BY 1
LIMIT 25;


/*What courses are the New Yorkers students taking?*/
SELECT users.user_id, users.city, progress.learn_cpp,progress.learn_html,progress.learn_java,progress.learn_javascript,progress.learn_sql 
FROM users
LEFT JOIN progress
ON users.user_id = progress.user_id
WHERE city = 'New York'
LIMIT 25;

/*What courses are the Chicago students taking?*/
SELECT users.user_id, users.city, progress.learn_cpp,progress.learn_html,progress.learn_java,progress.learn_javascript,progress.learn_sql 
FROM users
LEFT JOIN progress
ON users.user_id = progress.user_id
WHERE city = 'Chicago'
LIMIT 25;


 
