# Перечисление — NodesType

## Исходный файл

`IEnum/Program.cs`

## Назначение

`NodesType` задает тип построения узлов.

## Исходный код

```csharp
public enum NodesType{
    Equidistant, Chebyshev, Random
}
```

## Элементы

- `Equidistant` — равномерные узлы.
- `Chebyshev` — узлы Чебышева.
- `Random` — случайные узлы.

## Что сказать на экзамене

`enum` нужен, чтобы вместо числового кода способа построения использовать понятное имя.

## Проблемное место

В `GetEnumerator` реально реализован только `Equidistant`. Ветки `Chebyshev` и `Random` пустые.

