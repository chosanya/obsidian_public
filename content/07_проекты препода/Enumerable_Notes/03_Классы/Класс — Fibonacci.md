# Класс — Fibonacci

## Исходный файл

`Enumerable/Odd.cs`

## Назначение класса

`Fibonacci` задает последовательность чисел Фибоначчи типа `long`.

## Интерфейсы

```csharp
public class Fibonacci : IEnumerable<long>
```

Класс можно обходить через `foreach`.

## Методы

```csharp
public IEnumerator<long> GetEnumerator()
```

Возвращает перечислитель, созданный через `yield`.

```csharp
IEnumerator IEnumerable.GetEnumerator()
```

Негeneric-версия для совместимости.

## Фрагмент кода

```csharp
yield return b;
while (b > 0)
{
    b += a;
    a = b - a;
    if (b < 0) yield break;
    yield return b;
}
```

## Что сказать на экзамене

`Fibonacci` не хранит все числа заранее. Он лениво генерирует значения во время обхода. `yield break` завершает последовательность, когда возникает переполнение и `b` становится отрицательным.

