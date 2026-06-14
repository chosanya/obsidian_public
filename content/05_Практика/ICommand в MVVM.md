---
type: practice
discipline: OOP
language: C#
tags:
  - практика
---
# ICommand в MVVM

> [!tip] Простыми словами: Практика показывает, как кнопка вызывает действие через команду, а не напрямую через метод окна.

### Связь с ICommand

В MVVM кнопка обычно привязывается к свойству типа ICommand.

```csharp
public ICommand CalculateCommand { get; }
```

ICommand — интерфейс. Он требует наличие основных элементов:

```csharp
bool CanExecute(object? parameter);
void Execute(object? parameter);
event EventHandler? CanExecuteChanged;
```

Класс команды реализует этот интерфейс:

```csharp
public class RelayCommand : ICommand
{
    private readonly Action _execute;
    public RelayCommand(Action execute)
    {
        _execute = execute;
    }
    public bool CanExecute(object? parameter)
    {
        return true;
    }
    public void Execute(object? parameter)
    {
        _execute();
    }
    public event EventHandler? CanExecuteChanged;
}
```

Главная мысль: 
-- Интерфейс ICommand сообщает Avalonia, что объект можно использовать как команду кнопки. 
-- ViewModel не обязана зависеть от конкретного класса RelayCommand. Она работает через общий тип:

```csharp
public ICommand CalculateCommand { get; }
```

А внутри может находиться объект:

```csharp
CalculateCommand = new RelayCommand(Calculate);
```

Если действие должно ждать долгую операцию, например БД или задержку, в команду передают async-лямбду:

```csharp
CalculateCommand = new RelayCommand(async () => await CalculateAsync());
```

> [!tip] Простыми словами: кнопка не знает, что внутри есть ожидание. Она просто вызывает команду, а команда запускает async-метод.

Пример асинхронного метода:

```csharp
private async Task CalculateAsync()
{
    Result = "Считаю...";
    await Task.Delay(2000);
    Result = "Готово";
}
```

Через Binding пользователь сначала увидит `Считаю...`, а после ожидания — `Готово`.

-- Слева — интерфейсный тип ICommand.

-- Справа — конкретная реализация RelayCommand.
## Связи
- Связано с: [[ICommand]]
- Связано с: [[MVVM]]
- Связано с: [[Интерфейс]]
- Связано с: [[8. Асинхронность async await]]

## Источник
- файл: `5.tex`
- раздел: Связь с ICommand
