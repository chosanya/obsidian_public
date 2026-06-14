---
type: code-example
discipline: OOP
language: C#
tags:
  - пример-кода
---
# RelayCommand - реализация ICommand

> [!tip] Простыми словами: Пример показывает, как команда хранит действие и запускает его при нажатии кнопки.

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

-- Слева — интерфейсный тип ICommand.

-- Справа — конкретная реализация RelayCommand.
## Связи
- Связано с: [[ICommand]]
- Связано с: [[Интерфейс]]
- Связано с: [[MVVM]]

## Источник
- файл: `5.tex`
- раздел: Связь с ICommand
