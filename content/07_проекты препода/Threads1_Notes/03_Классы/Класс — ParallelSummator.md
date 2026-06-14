# Класс — ParallelSummator

## Исходный файл

`Threads1/ParallelSummator.cs`

## Назначение класса

`ParallelSummator` пытается посчитать сумму от `1` до `N` в 16 потоках.

## Поля и свойства

```csharp
private const int parts = 16;
```

Количество частей и потоков.

```csharp
public int N { get => field; set => field = Math.Abs(value); }
public long Result { get => field; private set => field = value; }
```

## Метод `CalcPartSum`

```csharp
private void CalcPartSum(object k)
```

Каждый поток получает номер `step` и суммирует числа:

```csharp
for (int i = step + 1; i <= N; i += parts)
```

## Метод `CalcSum`

```csharp
public void CalcSum()
```

Создает список потоков, запускает каждый поток и ждет завершения через `Join`.

## Проблемное место

Внутри потоков выполняется:

```csharp
Result += i;
```

Это не атомарная операция и не защищена `lock`, поэтому возможна гонка данных.

## Что сказать на экзамене

Класс показывает ручную многопоточность через `Thread`. Но его важно критиковать: общее свойство `Result` изменяется несколькими потоками без синхронизации.

