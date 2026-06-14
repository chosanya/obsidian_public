# Класс — RelayCommand

## Исходный файл

`Students/RelayCommand.cs`

## Назначение класса

`RelayCommand` — реализация `ICommand`, которая позволяет связать кнопку в XAML с методом во ViewModel.

## Поля

```csharp
private Action<object?> execute;
private Func<object?, bool>? canExecute;
```

`execute` — действие команды, `canExecute` — проверка доступности.

## Интерфейс

```csharp
public class RelayCommand : ICommand
```

## Методы

- `CanExecute`;
- `Execute`.

## Событие

```csharp
public event EventHandler? CanExecuteChanged
```

Подписывается на `CommandManager.RequerySuggested`.

## Что сказать на экзамене

`RelayCommand` нужен, чтобы не писать отдельный класс команды для каждой кнопки. Он принимает делегаты и превращает их в команду WPF.

