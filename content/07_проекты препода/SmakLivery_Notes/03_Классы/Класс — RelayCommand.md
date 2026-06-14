# Класс — RelayCommand

## Исходный файл

`SmakLivery/RelayCommand.cs`

## Назначение класса

`RelayCommand` — универсальная реализация интерфейса `ICommand` для MVVM.

## Факты из кода

- Реализует `ICommand`.
- Хранит `Action<object?> execute`.
- Хранит необязательный `Func<object?, bool>? canExecute`.
- Подписывает `CanExecuteChanged` на `CommandManager.RequerySuggested`.

## Основные методы

- `CanExecute` проверяет, доступна ли команда.
- `Execute` выполняет действие.

## Пояснение

Класс позволяет создавать команды через лямбда-выражения прямо во ViewModel.

## Что требует ручной проверки

- Класс принимает `Action<object?>`, поэтому асинхронные команды становятся `async void`.
- Для БД-операций лучше иметь отдельную async-команду, возвращающую `Task`.

## Связанные заметки

- [[Класс — MainViewModel]]
- [[Класс — AddEditViewModel]]
- [[05_Темы_ООП]]
