# SQL Vehicles Project

## Описание проекта
Этот проект представляет собой набор SQL-запросов для работы с базами данных, содержащими информацию о транспортных средствах, автомобильных гонках, бронировании отелей и структуре организации. Он предназначен для отработки навыков работы с реляционными базами данных на языке SQL.

## Цели и задачи
- Повторение основ работы с SQL, включая создание, наполнение и манипуляцию данными.
- Решение 13 задач по работе с базами данных, охватывающих различные сценарии работы с данными.
- Гарантированное соответствие результатов выполнения запросов тестовым данным, предоставленным в задании.

## Структура базы данных

В проекте используются 4 различных базы данных:

1. **Транспортные средства**  
   Хранит информацию о различных типах транспортных средств (автомобили, мотоциклы, велосипеды).
   - `Vehicle` (maker VARCHAR, model VARCHAR, type VARCHAR) – Основная таблица, содержащая информацию о производителе, модели и типе транспортного средства.
   - `Car` (vin VARCHAR, model VARCHAR, engine_capacity DECIMAL, horsepower INT, price DECIMAL, transmission VARCHAR) – Таблица автомобилей, связывается с `Vehicle` по model.
   - `Motorcycle` (vin VARCHAR, model VARCHAR, engine_capacity DECIMAL, horsepower INT, price DECIMAL, type VARCHAR) – Таблица мотоциклов, связывается с `Vehicle` по model.
   - `Bicycle` (serial_number VARCHAR, model VARCHAR, gear_count INT, price DECIMAL, type VARCHAR) – Таблица велосипедов, связывается с `Vehicle` по model.

2. **Автомобильные гонки**  
   Содержит информацию о гонках, гонщиках и результатах соревнований.
   - `Race` (id SERIAL, name VARCHAR, date DATE) – Основная таблица с информацией о гонках.
   - `Driver` (id SERIAL, name VARCHAR, team VARCHAR) – Таблица гонщиков.
   - `Result` (race_id INT, driver_id INT, position INT, time INTERVAL) – Таблица результатов гонок, связывает `Race` и `Driver`.

3. **Бронирование отелей**  
   Описывает систему бронирования номеров в отелях.
   - `Hotel` (ID_hotel SERIAL, name VARCHAR, location VARCHAR) – Таблица отелей.
   - `Room` (ID_room SERIAL, ID_hotel INT, room_type VARCHAR, price DECIMAL, capacity INT) – Таблица номеров, связанная с отелями.
   - `Customer` (ID_customer SERIAL, name VARCHAR, email VARCHAR, phone VARCHAR) – Таблица клиентов.
   - `Booking` (ID_booking SERIAL, ID_room INT, ID_customer INT, check_in_date DATE, check_out_date DATE) – Записи о бронированиях номеров.

4. **Структура организации**  
   Описывает иерархию сотрудников в организации.
   - `Employee` (id SERIAL, name VARCHAR, position VARCHAR, department VARCHAR, manager_id INT) – Таблица сотрудников, где `manager_id` связывает сотрудника с его начальником.

## Установка и запуск
1. **Убедитесь, что у вас установлен PostgreSQL**.
2. **Запустите скрипт инициализации для нужной базы данных**:
   - Для базы данных "Транспортные средства":
     ```
     psql -U ваш_пользователь -d ваша_база -f vehicles/initialization/base_init.sql
     ```
   - Для базы данных "Автомобильные гонки":
     ```
     psql -U ваш_пользователь -d ваша_база -f car_races/initialization/base_init.sql
     ```
   - Для базы данных "Бронирование отелей":
     ```
     psql -U ваш_пользователь -d ваша_база -f hotel_booking/initialization/base_init.sql
     ```
3. **Выполните SQL-запросы для решения задач**, находящиеся в соответствующих папках:
   - Запросы по "Транспортным средствам" – в `vehicles/`
   - Запросы по "Автомобильным гонкам" – в `car_races/`
   - Запросы по "Бронированию отелей" – в `hotel_booking/`

## Примечания
- Используется предоставленный SQL-скрипт без изменений.
- Решения задач будут оформлены в отдельных SQL-файлах.
