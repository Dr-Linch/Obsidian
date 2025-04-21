## Console

psql --- Подключение к PostgreSQL shell
(psql -U user_name) --- Подключение к пользователю (user_name) СУБД PostgreSQL 
\l --- Посмотреть все базы данных
\c db_name --- Подключиться к БД db_name
\dt --- Список всех таблиц
\d table_name --- Структура таблицы table_name
\du --- Список всех пользователей и их привилегии
\dt+ --- Список всех таблиц с описанием
\dt \*s\* ---  Список всех таблиц содержащих 's' в названии
(\*s --- В конце названия; s\* --- В начале )
\i FILE --- Выполнить команду из файла FILE
\o FILE --- Сохранить результат запроса в файл FILE
\\? --- Посмотреть список всех команд
\q --- Выйти из консоли PostgreSQL
\conninfo --- Посмотреть к какой БД сейчас подключен (хост, порт и т.д.)

### Command for working with DB

CREATE DATABASE DB_NAME --- Создание новой БД
(Если в названии БД есть заглавные буквы, обернуть в ")

DROP DATABASE DB_NAME --- Удаление БД

### Commands for working with tables
-----------------------------
CREATE TABLE  table_name(
column_name + data_type + \*constraints (if any) (\*Ограничения, если они есть)
); --- Создание новой таблицы

Example:
CREATE TABLE users(
id BIGSERIAL PRIMARY KEY,
first_name VARCHAR(50),
last_name VARCHAR(50),
gender VARCHAR(6),
email VARCHAR(150),
birth_date DATE
);

--------------------------------------
DROP TABLE table_name; --- Удалить таблицу table_name

---------------------------
INSERT INTO table_name (*column_name, column_name) VALUES(
first_name,
last_name,
gender,
email,
birth_date
),
(
\* Если добавляем несколько элементов
...
(The same data)
...
)--- Заполнение таблицы table_name

-----------------
SELECT \* FROM table_name; --- Получить все данные из таблицы table_name

----------------
SELECT column_name FROM table_name --- Получить значения колонки column_name из таблицы table_name

-------------
SELECT column_name_1, column_name_2 ... FROM table_name --- Получить значения колонок column_name_1, column_name_2 ..., из таблицы table_name

--------------------
SELECT \* FROM table_name ORDER BY ASC (DESC) --- Получить значения из таблицы table_name и отсортировать их по возрастанию (убыванию)

--------------
SELECT DISTINCT column_name FROM table_name --- Получить все уникальные значения колонки column_name из таблицы table_name

---------------
SELECT \* FROM table_name
WHERE gender = 'Female'; --- Получить все значения из таблицы table_name где поле gender равно 'Female'

-----------
SELECT \* FROM table_name WHERE gender = 'Female' AND country = 'Argentina' --- Получить все значения из таблицы table_name где поле gender равно 'Female' а поле country равно 'Argentina'

--------------
SELECT \* FROM table_name WHERE gender = 'Femail' AND (country = 'Argentina' OR country = 'Russia') --- Получить все значения из таблицы table_name где поле gender равно 'Female' а поле country_of_birth равно 'Argentina' или Russia

--------------
SELECT \* FROM table_name LIMIT 20 --- Получить первые 20 записей из таблицы table_name

---------
SELECT \* FROM table_name OFFSET 10 LIMIT 20 --- Получить 20 записей из таблицы table_name начиная с 10 позиции

----
SELECT \* FROM table_name OFFSET 10 FETCH FIRST 5 ROW ONLY --- Получить первые 5 строк из таблицы table_name начиная с 10 позиции

----------
SELECT \* FROM table_name WHERE column_name IN ('value_1', 'value_2', ...) --- Получить все значения из таблицы table_name в которых column_name равна одному из значений указанных в 'IN'

----------
SELECT \* FROM table_name WHERE column_name BETWEEN 'value_1' AND 'value_2' --- Получить все значение где значение column_name находиться между value_1 и value_2 

----------
SELECT \* FROM table_name WHERE column_name LIKE '%.com' --- Получить все значения где column_name заканчивается на '.com'
('%.com%' --- в середине, '.com%' --- в начале)

----------
SELECT \* FROM table_name WHERE column_name iLIKE '%.com' --- Получить все значения где column_name заканчивается на '.com' игнорируя регистр символов
('%.com%' --- в середине, '.com%' --- в начале)

----------
SELECT column_name, COUNT(\*) FROM table_name GROUP BY column_name --- Получить все уникальные значения column_name и количество строк которые относятся к этим значениям

----------
SELECT column_1, column_2, MAX(price) FROM table_name GROUP BY column_1, column_2 --- Вернёт уникальные сочетания column_1 и column_2 и максимальные значения price для каждого сочетания

-----------
SELECT column_name, COUNT(*) FROM table_name GROUP BY column_name HAVING COUNT(\*) > 10 --- Получить уникальные значения column_name к которым относятся более 10 строк

-----------
SELECT id, first_name AS name, last_name AS sure_name, gender AS sex FROM table_name --- Присваивает временные имена для колонок (при выводе у колонок будут указаны временные названия)

-----------
SELECT COALESCE(column_name, 'value') FROM table_name --- COALESCE позволяет заменить пустое значение в column_name на value

--------
SELECT \*, COALESCE(column_name, 'value') FROM table_name --- COALESCE позволяет заменить пустое значение в column_name на value

------
SELECT MAX(column_name) FROM table_name --- Получить максимальное значение из колонки column_name в таблице table_name

----------
SELECT MIN(coloumn_name) FROM table_name --- Получить минимальное значение из колонки column_name в таблице table_name

------------
SELECT AVG(column_name) FROM table_name --- Получить среднее значение в колонке column_name в таблице table_name

----------
SELECT ROUND(AVG(column_name)) FROM table_name --- ROUND позволяет округлять значения

----------
SELECT SUM(column_name) FROM table_name --- Получить сумму всех значений в колонке column_name из таблицы table_name

----------
ALTER TABLE table_name DROP CONSTRAINT users_pkey --- Удалить ограничитель

------
ALTER TABLE table_name ADD PRIMARY KEY(id) --- Добавление первичного ключа id

----


---
DELETE FROM table_name WHERE column_name = value --- Удалить запись, по значению

### Constraints 
-----------------------
NOT NULL --- Ограничение для строки; строка не должна быть пустой

Example:
CREATE TABLE users(
id BIGSERIAL PRIMARY KEY,
first_name VARCHAR(50) NOT NULL,
last_name VARCHAR(50) NOT NULL,
gender VARCHAR(6) NOT NULL,
email VARCHAR(150),
birth_date DATE NOT NULL
);