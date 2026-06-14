# Класс — OddEnumerator

## Исходный файл

`Enumerable/Odd.cs`

## Назначение класса

`OddEnumerator` вручную реализует обход нечетных чисел.

## Поля

```csharp
private int _current;
private int _minValue;
private int _maxValue;
```

## Интерфейсы

```csharp
class OddEnumerator : IEnumerator<int>
```

Класс реализует:

- `Current`;
- `MoveNext`;
- `Reset`;
- `Dispose`.

## Методы

```csharp
public bool MoveNext()
{
    _current += 2;
    return _current <= _maxValue;
}
```

Переходит к следующему нечетному числу.

```csharp
public void Reset()
{
    _current = _minValue - 2;
}
```

Возвращает перечислитель к начальному состоянию.

## Что сказать на экзамене

`OddEnumerator` показывает внутреннюю механику `foreach`: текущий элемент хранится в `Current`, а переход выполняется методом `MoveNext`.

