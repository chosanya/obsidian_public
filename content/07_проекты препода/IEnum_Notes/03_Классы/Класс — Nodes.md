# Класс — Nodes

## Исходный файл

`IEnum/Program.cs`

## Назначение класса

`Nodes` представляет коллекцию узлов на отрезке и реализует `IReadOnlyCollection<double>`.

## Поля

```csharp
double _left;
double _right;
int _count;
NodesType _type;
```

## Свойства

```csharp
public int Count => _count;
```

`Count` требуется интерфейсом `IReadOnlyCollection<double>`.

## Конструктор

```csharp
public Nodes(double left, double right, int count, NodesType type)
```

Проверяет параметры и сохраняет границы, количество узлов и тип построения.

## Интерфейсы

```csharp
public class Nodes : IReadOnlyCollection<double>
```

Класс можно обходить через `foreach`, и у него есть количество элементов.

## `GetEnumerator`

Для `Equidistant` вычисляет равномерные узлы и возвращает их через `yield return`.

## Индексатор

```csharp
public double this[int index]
```

Проверяет индекс и получает нужный элемент через обход `foreach(var elem in this)`.

## Что сказать на экзамене

`Nodes` показывает, как сделать свой объект похожим на коллекцию: у него есть `Count`, `GetEnumerator` и индексатор.

