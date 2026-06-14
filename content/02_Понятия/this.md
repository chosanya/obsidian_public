---
type: concept
discipline: OOP
language: C#
tags:
  - понятие
---
# this

> [!tip] Простыми словами: `this` означает “текущий объект”, то есть тот экземпляр, внутри которого сейчас выполняется код.

#### this

```csharp
public Person(string name)
{
    this.Name = name;
}
```

this обозначает текущий объект, для которого выполняется код.

Особенно полезно при совпадении имён:

```csharp
private string _name;
public Person(string name)
{
    _name = name;
}
```

Или без подчёркивания:

```csharp
private string _name;
public Person(string name)
{
    this.name = name;
}
```

* this.name — поле текущего объекта; 
* name — параметр конструктора.
## Связи
- Связано с: [[Конструктор]]
- Связано с: [[Класс]]
- Связано с: [[Объект]]

## Источник
- файл: `1.tex`
- раздел: this
