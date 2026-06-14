---
type: practice
discipline: OOP
language: C#
tags:
  - практика
  - postgresql
  - npgsql
  - база-данных
---
# DatabaseService PostgreSQL

> [!tip] Простыми словами: это отдельный класс-помощник, который берёт на себя все разговоры с PostgreSQL.

## Минимальная структура

```csharp
using Npgsql;

public class DatabaseService
{
    private const string ConnectionString =
        "Host=localhost;" +
        "Port=5432;" +
        "Database=oop_exam;" +
        "Username=postgres;" +
        "Password=1234";
}
```

## Создание таблицы

```csharp
public async Task InitializeAsync()
{
    await using var connection =
        new NpgsqlConnection(ConnectionString);
    await connection.OpenAsync();

    const string sql = """
        CREATE TABLE IF NOT EXISTS calculation_results
        (
            id INTEGER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
            input_value DOUBLE PRECISION NOT NULL,
            result_value DOUBLE PRECISION NOT NULL,
            created_at TIMESTAMP NOT NULL
        );
        """;

    await using var command =
        new NpgsqlCommand(sql, connection);
    await command.ExecuteNonQueryAsync();
}
```

## Сохранение записи

```csharp
public async Task SaveAsync(double input, double result)
{
    await using var connection =
        new NpgsqlConnection(ConnectionString);
    await connection.OpenAsync();

    const string sql = """
        INSERT INTO calculation_results
            (input_value, result_value, created_at)
        VALUES
            (@input, @result, @createdAt);
        """;

    await using var command =
        new NpgsqlCommand(sql, connection);
    command.Parameters.AddWithValue("@input", input);
    command.Parameters.AddWithValue("@result", result);
    command.Parameters.AddWithValue("@createdAt", DateTime.Now);

    await command.ExecuteNonQueryAsync();
}
```

## Загрузка записей

```csharp
public async Task<List<CalculationRecord>> LoadAsync()
{
    var records = new List<CalculationRecord>();

    await using var connection =
        new NpgsqlConnection(ConnectionString);
    await connection.OpenAsync();

    const string sql = """
        SELECT
            id,
            input_value,
            result_value,
            created_at
        FROM calculation_results
        ORDER BY id DESC;
        """;

    await using var command =
        new NpgsqlCommand(sql, connection);
    await using var reader =
        await command.ExecuteReaderAsync();

    while (await reader.ReadAsync())
    {
        records.Add(new CalculationRecord
        {
            Id = reader.GetInt32(0),
            InputValue = reader.GetDouble(1),
            ResultValue = reader.GetDouble(2),
            CreatedAt = reader.GetDateTime(3)
        });
    }

    return records;
}
```

## Коротко для экзамена

`DatabaseService` хранит строку подключения, открывает соединение через `NpgsqlConnection`, создаёт SQL-команды через `NpgsqlCommand`, передаёт значения через параметры и выполняет запросы асинхронно. ViewModel вызывает готовые методы сервиса и не содержит SQL.

## Связи

- Связано с: [[9. PostgreSQL C# Avalonia]]
- Связано с: [[10. Связь MVVM с PostgreSQL]]
- Связано с: [[Инкапсуляция в DatabaseService]]
- Связано с: [[8. Асинхронность async await]]
- Связано с: [[7. MVVM и структура Avalonia-приложения]]

## Источник

- файл: `pasted-text.txt`
- раздел: PostgreSQL + C# + Avalonia
