# RelayCommand.cs

## Путь

`CanvasDrawing/RelayCommand.cs`

## Назначение

Файл содержит локальную реализацию `ICommand`.

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Text;
using System.Windows.Input;

namespace CanvasDrawing
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

Локальный `RelayCommand` не является generic. В `MainViewModel` используется generic `RelayCommand<MouseEventArgs>` из MVVM Light.

