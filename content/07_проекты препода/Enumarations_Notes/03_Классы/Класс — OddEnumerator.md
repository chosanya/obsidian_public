# Класс — OddEnumerator

## Исходный файл

`Enumarations/Program.cs`

## Назначение класса

`OddEnumerator` вручную реализует перебор нечетных чисел.

## Поля

```csharp
private int _min;
private int _max;
private int _current;
```

`_min` и `_max` задают границы, `_current` хранит текущее значение.

## Интерфейсы

```csharp
class OddEnumerator : IEnumerator<int>
```

Класс обязан реализовать:

- `Current`;
- `MoveNext`;
- `Reset`;
- `Dispose`.

## Конструктор

```csharp
public OddEnumerator(int min, int max)
```

Конструктор подгоняет границы к нечетным числам и задает стартовое состояние.

## Методы

```csharp
public bool MoveNext()
{
    _current += 2;
    return _current < _max;
}
```

Переходит к следующему нечетному числу.

```csharp
public void Reset()
{
    _current = _min - 2;
}
```

Возвращает перечислитель в начальное состояние.

## Что сказать на экзамене

Этот класс показывает, как `foreach` работает внутри: он многократно вызывает `MoveNext`, а текущее значение берет из `Current`.

