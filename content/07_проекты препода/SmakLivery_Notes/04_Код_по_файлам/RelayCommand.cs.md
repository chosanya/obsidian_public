# RelayCommand.cs

## Путь

`SmakLivery/RelayCommand.cs`

## Назначение

Файл содержит реализацию [[Класс — RelayCommand]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Text;
using System.Windows.Input;

namespace SmakLivery
{
    public class RelayCommand : ICommand
    {
        private Action<object?> execute;
        private Func<object?, bool>? canExecute;

        public event EventHandler? CanExecuteChanged
        {
            add { CommandManager.RequerySuggested += value; }
            remove { CommandManager.RequerySuggested -= value; }
        }

        public RelayCommand(Action<object?> execute, Func<object?, bool>? canExecute = null)
        {
            this.execute = execute;
            this.canExecute = canExecute;
        }

        public bool CanExecute(object? parameter)
        {
            return canExecute == null || canExecute(parameter);
        }

        public void Execute(object? parameter)
        {
            execute(parameter);
        }
    }
}
```

## Разбор

Это основа команд `ICommand` в проекте.

## Факты из кода

- Файл входит в проект `SmakLivery`.
- Исходный код выше сохранен без правок.

## Связанные заметки

- [[00_Обзор]]
- [[02_Архитектура]]
- [[09_Проблемные_места]]
