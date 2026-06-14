# Класс — SequentialSummator

## Исходный файл

`Threads1/SequentialSummator.cs`

## Назначение класса

`SequentialSummator` считает сумму чисел от `1` до `N` последовательно, в одном потоке.

## Свойства

```csharp
public int N
{
    get => field;
    set => field = Math.Abs(value);
}
```

`N` хранит верхнюю границу суммы. Значение приводится к положительному через `Math.Abs`.

```csharp
public long Result
{
    get => field;
    private set => field = value;
}
```

`Result` хранит результат. Снаружи его можно читать, но нельзя записывать.

## Конструктор

```csharp
public SequentialSummator(int n)
{
    N = n;
}
```

## Методы

```csharp
public void CalcSum()
{
    for (int i = 1; i <= N; i++)
    {
        Result += i;
    }
}
```

## Что сказать на экзамене

Это базовая версия алгоритма. Она нужна как контрольный вариант для сравнения с многопоточной реализацией.

