# Resume Profile
Resume Profile is the first assignment project required to complete the course *[JavaScript, jQuery and JSON](https://www.coursera.org/learn/javascript-jquery-json/home/welcome)* from Coursera.

> *In this next assignment you will write a simple resume database that support Create, Read, Update, and Delete operations (CRUD). You will also move user information into its own table and link entries between two tables using foreign keys. You will also add some in-browser JavaScript data validation.*
> Copyright Creative Commons Attribution 3.0 - Charles R. Severance.

# Usage
To use this application you must be sure that you meet the requirementes and follow the configuration steps.

## Requirements

 - PHP >= 5.3
 - MySQL 3.x/4.x/5.x

## Configuration
You must configure the following to completely run the application:

 1. Create a database (or use an existing one), for example `misc`, create the tables named `users` and `Profile`, then add a new user to `users` table with the following statements:
```sql
CREATE TABLE users (
  user_id INTEGER NOT NULL AUTO_INCREMENT,
  name VARCHAR(128),
  email VARCHAR(128),
  password VARCHAR(128),
  PRIMARY KEY(user_id)
) ENGINE = InnoDB DEFAULT CHARSET=utf8;

ALTER TABLE users ADD INDEX(email);
ALTER TABLE users ADD INDEX(password);

CREATE TABLE Profile (
  profile_id INTEGER NOT NULL AUTO_INCREMENT,
  user_id INTEGER NOT NULL,
  first_name TEXT,
  last_name TEXT,
  email TEXT,
  headline TEXT,
  summary TEXT,
  PRIMARY KEY(profile_id),
  CONSTRAINT profile_ibfk_2
  FOREIGN KEY (user_id)
  REFERENCES users (user_id)
  ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO users (name,email,password)
VALUES ('UMSI','umsi@umich.edu','1a52e17fa899cf40fb04cfc42e6352f1');
```
2. Place the folder where you cloned this repo into your web server's root folder.
3. Configure the variables `$HOST, $PORT, $DB_NAME, $DB_USER, $DB_PASSWORD` in `pdo.php` file, accordnly to the values you configured in the previous step.

Now you can access to your folder's url in the browser, for example: *localhost/res-profile* using this email for login: `umsi@umich.edu`