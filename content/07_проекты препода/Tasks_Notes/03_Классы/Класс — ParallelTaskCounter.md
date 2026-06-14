# Класс — ParallelTaskCounter

## Исходный файл

`TaskTest/ParallelTaskCounter.cs`

## Назначение класса

`ParallelTaskCounter` считает количество простых чисел в диапазоне с помощью задач `Task<int>`.

## Поля

```csharp
private int _start;
private int _end;
```

## Главный метод

```csharp
public async Task<int> GetPrimeCount()
```

Метод разбивает диапазон на части, создает список задач, ожидает их через `Task.WhenAll` и суммирует результаты.

## Вспомогательные методы

```csharp
private bool IsPrime(int value)
```

Проверяет число на простоту.

```csharp
private Task<int> CountPrimesInRange(int start, int end)
```

Создает задачу через `Task.Run`.

## Что сказать на экзамене

Этот класс показывает безопасный подход: каждая задача считает локальный результат и возвращает его, поэтому общий счетчик не нужно защищать `lock`.

