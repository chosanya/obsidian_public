# OrderEnumDisplayConverter.cs

## Путь

`SmakLivery/OrderEnumDisplayConverter.cs`

## Назначение

Файл содержит WPF-конвертер [[Класс — OrderEnumDisplayConverter]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations;
using System.Globalization;
using System.Reflection;
using System.Text;
using System.Windows.Data;

namespace SmakLivery
{
    public class OrderEnumDisplayConverter : IValueConverter
    {
        public object Convert(object value, Type targetType, object parameter, CultureInfo culture)
        {
            if (value is not OrderStatus e) return value;

            var field = e.GetType().GetField(e.ToString());
            var attr = field?.GetCustomAttribute<DisplayAttribute>();
            return attr?.Name ?? e.ToString();
        }

        public object ConvertBack(object value, Type targetType, object parameter, CultureInfo culture)
            => throw new NotSupportedException();
    }
}
```

## Разбор

Конвертер превращает enum в текст из `DisplayAttribute`.

## Факты из кода

- Файл входит в проект `SmakLivery`.
- Исходный код выше сохранен без правок.

## Связанные заметки

- [[00_Обзор]]
- [[02_Архитектура]]
- [[09_Проблемные_места]]
