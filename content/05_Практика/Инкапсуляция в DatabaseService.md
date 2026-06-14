---
type: practice
discipline: OOP
language: C#
tags:
  - практика
---
# Инкапсуляция в DatabaseService

> [!tip] Простыми словами: Практика показывает, как спрятать подключение и SQL внутри отдельного сервиса.

### Инкапсуляция в вашем Avalonia-проекте

```csharp
Она будет встречаться в ViewModel:
private string _result = string.Empty;
public string Result
{
    get => _result;
    set
    {
        _result = value;
        OnPropertyChanged();
    }
}
```

Поле _result скрыто.
Свойство Result предоставляет доступ к данным и дополнительно уведомляет интерфейс об изменении.
То есть внешний код не должен напрямую изменять _result. Он работает со свойством Result.

```csharp
Инкапсуляция будет и в сервисе БД:
public class DatabaseService
{
    private readonly string _connectionString;
    public async Task SaveResultAsync(double value)
    {
        // Внутренняя работа с соединением и SQL
    }
}
```

Другие части программы вызывают: await databaseService.SaveResultAsync(result);

Здесь `await` нужен, чтобы дождаться сохранения, но не заморозить интерфейс.

> [!tip] Простыми словами: ViewModel просит сервис сохранить данные и спокойно ждёт ответ, а окно продолжает жить.

Они не обязаны знать:

- как открывается соединение;
- какая SQL-команда создаётся;
- как передаются параметры;
- как закрывается соединение.

Эти детали скрыты внутри DatabaseService.

В PostgreSQL-проекте внутри такого сервиса обычно используются:

- `NpgsqlConnection` — открыть соединение;
- `NpgsqlCommand` — выполнить SQL-запрос;
- `ExecuteNonQueryAsync()` — выполнить `INSERT`, `UPDATE`, `DELETE` или `CREATE TABLE`;
- `ExecuteReaderAsync()` — прочитать строки из `SELECT`;
- `ExecuteScalarAsync()` — получить одно значение, например `COUNT(*)`.

Пример сохранения:

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

> [!tip] Простыми словами: ViewModel просит “сохрани”, а все детали подключения, SQL и параметров остаются внутри `DatabaseService`.

**Итог:**
Инкапсуляция — это принцип ООП, при котором данные и действия над ними объединяются внутри класса, а детали реализации скрываются от внешнего кода.
Доступ к состоянию объекта предоставляется через открытые свойства и методы. Например, поле баланса можно сделать private, а изменение баланса выполнять через методы пополнения и снятия, которые проверяют корректность операции.

**Короткий ответ на 30 секунд**

Инкапсуляция — это объединение данных и методов работы с ними в одном классе и сокрытие внутренней реализации.
Обычно поля делают private, а внешний доступ предоставляют через public-свойства и методы. 
Это позволяет контролировать изменения и не допускать некорректного состояния объекта.
## Связи
- Связано с: [[2. Инкапсуляция]]
- Связано с: [[Базы данных]]
- Связано с: [[SQL]]
- Связано с: [[8. Асинхронность async await]]
- Связано с: [[9. PostgreSQL C# Avalonia]]

## Источник
- файл: `2.tex`
- раздел: Инкапсуляция в вашем Avalonia-проекте
