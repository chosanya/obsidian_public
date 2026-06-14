# OrderWithCourier.cs

## Путь

`SmakLivery/OrderWithCourier.cs`

## Назначение

Файл содержит модель [[Класс — OrderWithCourier]].

## Исходный код

```csharp
﻿namespace SmakLivery
{
    public class OrderWithCourier
    {
        public long Id { get; set; }
        public string Address { get; set; } = string.Empty;
        public OrderStatus Status { get; set; } = OrderStatus.Accepted;
        public long? CourierId { get; set; } = null;
        public string CourierFirstName { get; set; } = string.Empty;
        public string CourierLastName { get; set; } = string.Empty;
        public string Transport { get; set; } = string.Empty;
        public string CourierName => CourierFirstName + " " + CourierLastName;
        public Order ToOrder()
        {
            return new Order { Id = Id, Address = Address, Status = Status, CourierId = CourierId };
        }
            
    }
}
```

## Разбор

Тип используется для отображения результата SQL `JOIN`.

## Факты из кода

- Файл входит в проект `SmakLivery`.
- Исходный код выше сохранен без правок.

## Связанные заметки

- [[00_Обзор]]
- [[02_Архитектура]]
- [[09_Проблемные_места]]
