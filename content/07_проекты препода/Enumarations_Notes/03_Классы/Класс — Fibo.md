# Класс — Fibo

## Исходный файл

`Enumarations/Program.cs`

## Назначение класса

`Fibo` задает последовательность чисел Фибоначчи и позволяет обходить ее через `foreach`.

## Интерфейсы

```csharp
class Fibo : IEnumerable<int>
```

Класс реализует `IEnumerable<int>`, значит он должен предоставить `GetEnumerator`.

## Методы

```csharp
public IEnumerator<int> GetEnumerator()
```

Метод возвращает перечислитель. Из-за `yield return` компилятор создает перечислитель автоматически.

```csharp
IEnumerator IEnumerable.GetEnumerator()
```

Это негeneric-версия метода для совместимости со старым `IEnumerable`.

## Фрагмент кода

```csharp
int a = 0, b = 1;
yield return a;
yield return b;
for (int i = 0; i <= 7; i++) {
    b = a + b;
    a = b - a;
    yield return b;
}
```

## Какие темы используются

- `IEnumerable<T>`;
- `IEnumerator<T>`;
- `yield return`;
- `foreach`;
- локальные переменные;
- цикл `for`.

## Что сказать на экзамене

`Fibo` — это класс-последовательность. Он не хранит заранее весь список чисел, а выдает значения по одному при обходе через `foreach`.

