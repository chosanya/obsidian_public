# Order.cs

## Путь

`SmakLivery/Order.cs`

## Назначение

Файл содержит модель [[Класс — Order]] и [[Перечисление — OrderStatus]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.ComponentModel.DataAnnotations;
using System.Text;

namespace SmakLivery
{
    public enum OrderStatus
    {
        [Display(Name = "Смачно принят")]
        Accepted,
        [Display(Name = "Смачно готовим заказ")]
        Preparing,
        [Display(Name = "Во смачном пути")]
        OutForDelivery,
        [Display(Name = "Смакуйте полученный заказ!")]
        Delivered,
        [Display(Name = "Антисмачно отменен")]
        Cancelled
    }

    public class Order
    {
        public long Id { get; set; }
        public string Address { get; set; } = string.Empty;
        public OrderStatus Status { get; set; } = OrderStatus.Accepted;
        public long? CourierId { get; set; } = null;
    }
}
```

## Разбор

Это основные типы предметной области.

## Факты из кода

- Файл входит в проект `SmakLivery`.
- Исходный код выше сохранен без правок.

## Связанные заметки

- [[00_Обзор]]
- [[02_Архитектура]]
- [[09_Проблемные_места]]
