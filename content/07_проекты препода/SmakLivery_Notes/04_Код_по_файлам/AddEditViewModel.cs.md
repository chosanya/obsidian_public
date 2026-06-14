# AddEditViewModel.cs

## Путь

`SmakLivery/AddEditViewModel.cs`

## Назначение

Файл содержит ViewModel формы заказа [[Класс — AddEditViewModel]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Runtime.CompilerServices;
using System.Text;

namespace SmakLivery
{
    public class AddEditViewModel
    {
        public Order Order { get; init; }
        public RelayCommand CancelCommand { get; init; }
        public RelayCommand SaveCommand { get; init; }
        public String SaveButtonText => (Order.Id == 0) ? "Смачно создать заказ" : "Смачно все изменить";
        public AddEditViewModel(Order order)
        {
            Order = new Order()
            {
                Id = order.Id,
                Address = order.Address,
                Status = order.Status,
                CourierId = order.CourierId,
            };
            CancelCommand = new RelayCommand(
                async (o) =>
                {

                }
            );
            SaveCommand = new RelayCommand(async (o) =>
            {
                if ( order.Id == 0)
                await DbHelper.AddOrderAsync(Order);
                else await DbHelper.EditOrderAsync(Order);
            });
        }
    }
}
```

## Разбор

Здесь выбирается добавление или редактирование заказа.

## Факты из кода

- Файл входит в проект `SmakLivery`.
- Исходный код выше сохранен без правок.

## Связанные заметки

- [[00_Обзор]]
- [[02_Архитектура]]
- [[09_Проблемные_места]]
