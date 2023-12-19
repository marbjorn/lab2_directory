# Лабораторная работа 2. Справочники
Антонченко Евгений, 3 курс 12 группа, 2023
 **©** All rights reserved
## 1. Описание базы данных
База данных состоит из следующих справочников:

 **Клиент**
 - id *(первичный ключ)*
 - ФИО
 - серия и номер паспорта
 - номер телефона
 - адрес электронной почты

 **Счет**
 - id *(первичный ключ)*
 - сумма на счете
 - id владельца *(внешний ключ к Клиенту)*

## 2. Проектирование БД
![Схема базы данных](https://github.com/marbjorn/lab2_directory/blob/main/UML_scheme.png)

**Создание таблиц:**

    CREATE TABLE Client {
    	id INTEGER PRIMARY KEY AUTOINCREMENT,
    	name TEXT NOT NULL,
    	passport TEXT NOT NULL,
    	phone_num TEXT, 
    	email TEXT
    };
    
    CREATE TABLE Account {
    	id INTEGER PRIMARY KEY AUTOINCREMENT,
    	sum REAL NOT NULL,
    	client_id INT NOT NULL,
    	FOREIGN KEY (client_id) REFERENCES Client (id)
    };

**Пример заполнения таблиц:**

    INSERT INTO Client (name, passport, phone_num, email) VALUES
    ("Притыцкий Павел Валерьевич", "HB7714321", 8(033)9945221, prytipav@gmail.com),
    ("Кропотко Елена Витальевна", "HB9832893", 8(033)5792401, cropelen@gmail.com),
    ("Кашкевич Сергей Иванович", "HB3113454", 8(033)9843031, kashser@gmail.com),
    ("Березовских Анастасия Борисовна", "HB0932214", 8(033)5431145, berezanas@gmail.com);

    INSERT INTO Account (sum, client_id) VALUES
    (100.98, 1),
    (75.10, 3),
    (503.23, 3),
    (409.18, 2),
    (167.37, 1),
    (30.00, 4),
    (89.43, 4);


