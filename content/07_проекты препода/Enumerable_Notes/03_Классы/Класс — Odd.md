# Класс — Odd

## Исходный файл

`Enumerable/Odd.cs`

## Назначение класса

`Odd` представляет последовательность нечетных чисел.

## Поля

```csharp
private OddEnumerator enumerator;
```

Поле хранит объект ручного перечислителя.

## Конструктор

```csharp
public Odd(int minValue, int maxValue) {
    enumerator = new OddEnumerator(minValue, maxValue);
}
```

## Интерфейсы

```csharp
public class Odd : IEnumerable<int>
```

## Методы

```csharp
public IEnumerator<int> GetEnumerator()
{
    return enumerator;
}
```

## Связи

- Использует: [[Класс — OddEnumerator]].

## Что сказать на экзамене

`Odd` показывает ручной вариант реализации перечисления: класс-последовательность возвращает объект-перечислитель.

## Проблемное место

`GetEnumerator` возвращает один и тот же объект. Обычно для повторного обхода лучше создавать новый перечислитель.

