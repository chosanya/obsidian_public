# Перечисление — OrderStatus

## Исходный файл

`SmakLivery/Order.cs`

## Назначение перечисления

`OrderStatus` описывает возможные статусы заказа.

## Факты из кода

Значения:

- `Accepted`.
- `Preparing`.
- `OutForDelivery`.
- `Delivered`.
- `Cancelled`.

Каждое значение помечено атрибутом `[Display(Name = ...)]`.

## Связь с PostgreSQL

В `DbHelper` PostgreSQL enum `order_status` маппится на C# enum:

```csharp
.MapEnum<OrderStatus>("order_status")
```

## Пояснение

Перечисление ограничивает статус заказа набором допустимых значений. Атрибут `Display` нужен для красивого отображения в интерфейсе через [[Класс — OrderEnumDisplayConverter]].

## Что требует ручной проверки

- Соответствие имен C# enum и PostgreSQL enum после маппинга Npgsql.
- В C# значения PascalCase, а в PostgreSQL — snake_case.

## Связанные заметки

- [[Класс — Order]]
- [[Класс — OrderEnumDisplayConverter]]
- [[Класс — DbHelper]]
