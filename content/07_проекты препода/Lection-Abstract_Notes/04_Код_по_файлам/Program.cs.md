# Program.cs

## Путь

`Lection-Abstract/Program.cs`

## Назначение

Файл создает объекты наследников `Nodes` и выводит их узлы.

## Исходный код

```csharp
﻿using Lection_Abstract;
EqvidNodes en = new EqvidNodes(11);
for (int i = 0; i < 11; i++)
{
    Console.WriteLine(en[i]);
}

ChebyshevNodes chn = new ChebyshevNodes(5);
for (int i = 0; i < 5; i++)
{
    Console.WriteLine(chn[i]);
}

Console.WriteLine();
RandomNodes rn = new RandomNodes(5);
for (int i = 0; i < 5; i++)
{
    Console.WriteLine(rn[i]);
}
```

## Разбор

Создаются три объекта:

- `EqvidNodes`;
- `ChebyshevNodes`;
- `RandomNodes`.

Каждый объект используется одинаково: через индексатор `[i]`. Но результат получается по разной логике, потому что индексатор переопределен в каждом наследнике.

## Связи

- Использует: [[Класс — EqvidNodes]], [[Класс — ChebyshevNodes]], [[Класс — RandomNodes]].

