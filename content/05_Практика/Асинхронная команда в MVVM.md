---
type: practice
discipline: OOP
language: C#
tags:
  - практика
  - асинхронность
  - mvvm
  - команды
---
# Асинхронная команда в MVVM

> [!tip] Простыми словами: кнопка запускает команду, команда запускает метод, метод ждёт, а окно всё это время остаётся живым.

## Код

```csharp
private string _result = string.Empty;

public string Result
{
    get => _result;
    set
    {
        _result = value;
        OnPropertyChanged();
    }
}

public ICommand StartCommand { get; }

public MainWindowViewModel()
{
    StartCommand = new RelayCommand(async () => await StartAsync());
}

private async Task StartAsync()
{
    Result = "Запуск";
    await Task.Delay(1000);
    Result = "Завершено";
}
```

## Разбор

- `StartCommand` — команда, к которой привязывается кнопка.
- `RelayCommand` получает async-лямбду.
- `StartAsync()` запускается по команде.
- `Result = "Запуск"` сразу обновляет свойство.
- `await Task.Delay(1000)` ждёт 1 секунду без заморозки окна.
- `Result = "Завершено"` обновляет свойство после ожидания.
- `OnPropertyChanged()` нужен, чтобы Binding обновил интерфейс.

## Вопросы и ответы

1. Какой метод запускается по кнопке?

Запускается `StartAsync()`, потому что команда `StartCommand` вызывает его через `RelayCommand`.

2. Что делает `await Task.Delay(1000)`?

Ждёт 1 секунду асинхронно.

3. Что увидит пользователь сначала и что через секунду?

Сначала `Запуск`, через секунду `Завершено`.

4. Почему интерфейс не зависает?

Потому что ожидание выполняется через `await`, а не блокирует поток интерфейса.

5. Что здесь означает `Task`?

`Task` означает асинхронную операцию, завершения которой можно дождаться.

## Связи

- Связано с: [[8. Асинхронность async await]]
- Связано с: [[7. MVVM и структура Avalonia-приложения]]
- Связано с: [[ICommand в MVVM]]
- Связано с: [[6.  делегаты, события и лямбда-выражения]]

## Источник

- файл: добавлено вручную
- раздел: Асинхронная команда в MVVM
