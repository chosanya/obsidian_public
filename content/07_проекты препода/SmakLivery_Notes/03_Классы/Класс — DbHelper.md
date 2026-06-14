# Класс — DbHelper

## Исходный файл

`SmakLivery/DbHelper.cs`

## Назначение класса

`DbHelper` — статический класс для работы с PostgreSQL.

## Факты из кода

- Хранит строку подключения к БД.
- Создает `NpgsqlDataSource`.
- Маппит PostgreSQL enum `order_status` на C# enum `OrderStatus`.
- Создает enum и таблицы.
- Загружает заказы.
- Добавляет, редактирует и удаляет заказы.

## Основные методы

- `CreateDbAsync()` — создание enum и таблиц.
- `GetOrders()` — чтение заказов с курьерами.
- `DeleteOrderByIdAsync(long orderId)` — удаление заказа.
- `AddOrderAsync(Order order)` — добавление заказа.
- `EditOrderAsync(Order order)` — редактирование заказа.

## PostgreSQL и Npgsql

Используется `NpgsqlDataSourceBuilder`, `NpgsqlCommand`, `ExecuteReaderAsync`, `ExecuteNonQueryAsync`, `ExecuteScalarAsync`.

## SQL

В классе есть запросы `CREATE TYPE`, `CREATE TABLE`, `SELECT JOIN`, `INSERT`, `UPDATE`, `DELETE`.

## Что требует ручной проверки

- Строка подключения захардкожена.
- Создание `courier` содержит `FOREIGN KEY (id)` без `REFERENCES`.
- `order.courier_id` не объявлен внешним ключом.
- `SELECT *` вместе с `JOIN` читается по индексам колонок.
- `INNER JOIN` скрывает заказы без курьера.
- `INSERT` не записывает `CourierId`.
- `UPDATE` не очищает `courier_id`, если `CourierId == null`.

## Связанные заметки

- [[09_Проблемные_места]]
- [[05_Темы_ООП]]
