# Класс — Even

## Исходный файл

`Enumerable/Odd.cs`

## Назначение класса

`Even` задает последовательность четных чисел в заданном диапазоне.

## Поля

```csharp
private int _minValue;
private int _maxValue;
```

Поля хранят границы диапазона.

## Конструктор

```csharp
public Even(int minValue, int maxValue)
```

Проверяет корректность границ и подгоняет их к четным значениям.

## Интерфейсы

```csharp
public class Even : IEnumerable<int>
```

## Методы

```csharp
public IEnumerator<int> GetEnumerator()
{
    for (int current = _minValue; current <= _maxValue; current+=2)
    {
        yield return current;
    }
}
```

## Что сказать на экзамене

`Even` показывает удобный вариант `IEnumerable<T>` через `yield return`: состояние цикла хранит сгенерированный компилятором перечислитель.

