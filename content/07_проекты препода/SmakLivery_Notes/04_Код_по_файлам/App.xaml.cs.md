# App.xaml.cs

## Путь

`SmakLivery/App.xaml.cs`

## Назначение

Файл содержит code-behind класса [[Класс — App]] и запуск инициализации БД.

## Исходный код

```csharp
﻿using System.Configuration;
using System.Data;
using System.Windows;

namespace SmakLivery
{
    /// <summary>
    /// Interaction logic for App.xaml
    /// </summary>
    public partial class App : Application
    {
        protected override async void OnStartup(StartupEventArgs e)
        {
            base.OnStartup(e);
            try
            {
                await DbHelper.CreateDbAsync();
            }
            catch (Exception ex)
            {
                MessageBox.Show($"Не удалось подключиться к БД:\n{ex.Message}",
                                "Ошибка инициализации",
                                MessageBoxButton.OK, MessageBoxImage.Error);
                Shutdown(1); // Закрываем приложение с кодом ошибки
                return;
            }
        }
    }

}
```

## Разбор

Здесь находится `async void OnStartup`, см. [[09_Проблемные_места]].

## Факты из кода

- Файл входит в проект `SmakLivery`.
- Исходный код выше сохранен без правок.

## Связанные заметки

- [[00_Обзор]]
- [[02_Архитектура]]
- [[09_Проблемные_места]]
