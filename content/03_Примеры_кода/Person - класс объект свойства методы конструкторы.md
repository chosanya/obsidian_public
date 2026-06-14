---
type: code-example
discipline: OOP
language: C#
tags:
  - пример-кода
---
# Person - класс объект свойства методы конструкторы

> [!tip] Простыми словами: Пример собирает основные элементы класса в одном месте: поле, свойства, конструкторы и методы.

### Цельный пример
```csharp
public class Person
{
    // Поле: непосредственно хранит возраст 
    private int _age = 18; 
    // Автореализуемое свойство
    public string Name { get; private set; } 
    // Свойство с проверкой 
    public int Age
    { 
        get => _age; 
        set => _age = Math.Max(Math.Min(value, 150), 0); 
    }
    // Вычисляемое свойство только для чтения
    public string PersonData 
    { 
        get => Name + ". Возраст: " + Age; 
    } 
    // Конструктор без параметров 
    public Person() 
    {
        Name = "Неизвестно"; 
    }
    // Конструктор с параметрами 
    public Person(string name, int age)
    { 
        Name = name; 
        Age = age; 
    } 
    // Метод без возвращаемого значения 
    public void PrintInformation() 
    { 
        Console.WriteLine(PersonData); 
    } 
    // Метод с возвращаемым значением
    public bool IsAdult() 
    { 
        return Age >= 18; 
    } 
    }
```
Использование:

- Person firstPerson = new Person();
- Person secondPerson = new Person("Анна", 20);
- secondPerson.PrintInformation();
- bool isAdult = secondPerson.IsAdult();
- Console.WriteLine(isAdult);

**Итог**

Person — это класс, описывающий человека. firstPerson и secondPerson — объекты этого класса. 
Поле _age хранит возраст и закрыто модификатором private. 
Свойство Age предоставляет контролируемый доступ к полю и ограничивает значение диапазоном от 0 до 150. 
Name является автореализуемым свойством с закрытым set, поэтому изменить имя извне класса нельзя. 
Конструкторы задают начальное состояние объектов. 
Метод PrintInformation выводит данные, а метод IsAdult возвращает результат проверки возраста.
## Связи
- Связано с: [[Класс]]
- Связано с: [[Объект]]
- Связано с: [[Поле]]
- Связано с: [[Свойство]]
- Связано с: [[Метод]]
- Связано с: [[Конструктор]]

## Источник
- файл: `1.tex`
- раздел: Цельный пример
