# Класс — RelayCommand

## Исходный файл

`CanvasDrawing/RelayCommand.cs`

## Назначение класса

`RelayCommand` — локальная реализация `ICommand`.

## Важный нюанс

В `MainViewModel.cs` используется:

```csharp
using GalaSoft.MvvmLight.Command;
MouseMoveCommand = new RelayCommand<MouseEventArgs>(OnMouseMove);
```

Это generic-команда из MVVM Light, а не локальный `RelayCommand`, потому что локальный класс не является generic.

## Что сказать на экзамене

В проекте есть две идеи команд: локальный `RelayCommand` и команда из MVVM Light. Для `MouseMoveCommand` фактически используется MVVM Light.

