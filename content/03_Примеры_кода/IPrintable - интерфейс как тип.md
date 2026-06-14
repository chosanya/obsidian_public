---
type: code-example
discipline: OOP
language: C#
tags:
  - пример-кода
---
# IPrintable - интерфейс как тип

> [!tip] Простыми словами: Пример показывает, как разные классы можно использовать одинаково через интерфейс `IPrintable`.

### Интерфейс

> [!definition]
> Интерфейс задаёт контракт: какие элементы должен иметь класс.

```csharp
public interface IPrintable
{
    void Print();
}
```

По соглашению имена интерфейсов в C# начинаются с I.
#### IPrintable
IPrintable можно читать как: Объект можно печатать.

Класс реализует интерфейс:

```csharp
public class Report : IPrintable
{
    public void Print()
    {
        Console.WriteLine("Печать отчёта");
    }
}
```

Запись: "Report : IPrintable"
означает, что класс обязуется реализовать элементы интерфейса.

Если метод Print() не будет реализован, класс не скомпилируется.

#### Интерфейс как тип

Переменная интерфейсного типа может хранить объект класса, реализующего этот интерфейс:

```csharp
IPrintable printable = new Report();
printable.Print();
```

Это полиморфизм через интерфейс.

Разные классы могут реализовывать один интерфейс:

```csharp
public class Document : IPrintable
{
    public void Print()
    {
        Console.WriteLine("Печать документа");
    }
}
public class Photo : IPrintable
{
    public void Print()
    {
        Console.WriteLine("Печать фотографии");
    }
}
List<IPrintable> items = new List<IPrintable>
{
    new Document(),
    new Photo()
};
foreach (IPrintable item in items)
{
    item.Print();
}
```

Каждый объект выполняет одну операцию по-своему.
## Связи
- Связано с: [[Интерфейс]]
- Связано с: [[4. Полиморфизм]]

## Источник
- файл: `5.tex`
- раздел: Интерфейс
