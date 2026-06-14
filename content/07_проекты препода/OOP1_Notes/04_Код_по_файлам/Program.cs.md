# Program.cs

## Путь

`OOP1/Program.cs`

## Назначение

Файл содержит демонстрационный код и определение класса [[Класс — Complex]]. Активная часть программы минимальна: она выводит пустую строку. Основной учебный материал — класс `Complex`.

## Исходный код

```csharp
﻿using System.Text;
/*
Complex z1 = new Complex();
z1.Re = 1;
z1.Im = 2;
Console.WriteLine(z1.Abs);
Console.WriteLine(z1);

var z2 = new Complex() { Re = 1, Im = -2 };
Console.WriteLine(z2);

var z3 = new Complex() { Re = 0, Im = -3 };
Console.WriteLine(z3);

var z4 = new Complex(1, 1);
Console.WriteLine(z4);

var z5 = new Complex(1, -1);
Console.WriteLine(z5);

var z6 = new Complex(3, 0);
Console.WriteLine(z6);

var z7 = new Complex();
Console.WriteLine(z7);

var z8 = new Complex(0, 2);
Console.WriteLine(z8);

var z9 = new Complex(re: -1, im: 7);
Console.WriteLine(z9);

Console.WriteLine(z9["Re"]);
Console.WriteLine(z9["i"]);
Console.WriteLine(z9["Привет!"]?.ToString() ?? "неверный индекс");
//var y = (x ?? 0) + 1;

var z10 = z8.Plus(z9);
Console.WriteLine(z10);
var z11 = Complex.Plus(z8, z9);
Console.WriteLine(z11);

var z12 = z8 + z9;
Console.WriteLine(z12);

Console.WriteLine(new Complex(5, 7).Equals(new Complex(5, 7)));
Console.WriteLine(new Complex(5).Equals(5));
Console.WriteLine(new Complex(5, 7) == new Complex(5, 7));

Complex z13 = z8 + 3.5;
var z14 = 3.5 + z8;
double v = (double)z14 - 1;
*/
Console.WriteLine();

public class Complex
{
    double _re;
    private double _im;
    public double Re
    {
        get { return _re; }
        set { _re = value; }
    }

    public double Im
    {
        get => _im;
        set => _im = value;
    }

    //public double Real { get; set; }
    //public double Imaginary { get; set; }

    public double Abs => Math.Sqrt(_re * _re + _im * _im);

    //public Complex()
    //{
    //    Console.WriteLine("По умолчанию");
    //}
    public Complex(double re = 0.0, double im = 0.0)
    {
        Re = re;
        Im = im;
    }

    public double? this[string part]
    {
        get
        {
            switch (part.ToLower())
            {
                case "re":
                case "r":
                case "real":
                    {
                        return Re;
                    }
                case "im":
                case "i":
                case "imaginary":
                    {
                        return Im;
                    }
                default:
                    return null;
            }
        }
    }
    
    public override string ToString()
    {
        StringBuilder sb = new StringBuilder();
        if (Re != 0 || Im == 0)
        {
            sb.Append(Re);
        }
        if (Im != 0) { 
            if (Im > 0)
            {
                if (Re != 0) sb.Append("+");
            } else
            {
                sb.Append("-");
            }
            if (Math.Abs(Im) != 1) sb.Append(Math.Abs(Im));
            sb.Append("i");
        }

        return sb.ToString();
    }

    public Complex Plus(Complex other)
    {
        return new Complex(this.Re + other.Re, Im + other.Im);
    }

    public static Complex Plus(Complex z1, Complex z2)
    {
        return new Complex(z1.Re + z2.Re, z1.Im + z2.Im);
    }

    public static Complex operator+(Complex z1, Complex z2)
    {
        return new Complex(z1.Re + z2.Re, z1.Im + z2.Im);
    }
    
    public static explicit operator double(Complex z) => z.Re;
    public static implicit operator Complex(double z) => new(z, 0);

    public static Complex operator -(Complex z1, Complex z2)
    {
        return new Complex(z1.Re - z2.Re, z1.Im - z2.Im);
    }

    public static Complex operator -(Complex z1)
    {
        return new Complex(z1.Re, -z1.Im);
    }

    public static bool operator ==(Complex z1, Complex z2)
    {
        return z1.Re == z2.Re && z1.Im == z2.Im;
    }

    public static bool operator !=(Complex z1, Complex z2) => !(z1 == z2);

    public override bool Equals(object? obj)
    {
        if (obj is Complex z)
        {
            return Re == z.Re && Im == z.Im;
        }
        if (obj is double d)
        {
            return Re == d && Im == 0;
        }
        if (obj is int i)
        {
            return Re == i && Im == 0;
        }
        return false;
    }

    public override int GetHashCode()
    {
        return HashCode.Combine(Re, Im);
    }

}
```

## Разбор по блокам

### Блок 1. Демонстрационный код

Что делает: показывает, как можно создавать объекты `Complex`, задавать свойства, выводить модуль, обращаться к индексатору, складывать числа и сравнивать их.

Почему нужен: это учебная демонстрация возможностей класса.

Какие конструкции C# используются:

- создание объекта через `new`;
- инициализатор объекта;
- именованные аргументы;
- оператор `??`;
- индексатор;
- перегруженные операторы;
- явное и неявное приведение.

Связанные темы:

- [[Классы и объекты]]
- [[Свойство]]
- [[Конструктор]]

### Блок 2. Поля и свойства

Что делает: хранит действительную и мнимую части комплексного числа.

Почему нужен: объект должен иметь внутреннее состояние.

Какие конструкции C# используются:

- поля;
- свойства с `get` и `set`;
- expression-bodied accessor.

Связанные темы:

- [[Поле]]
- [[Свойство]]
- [[Инкапсуляция]]

### Блок 3. Конструктор

Что делает: задает начальные значения `Re` и `Im`.

Почему нужен: объект должен получать корректное начальное состояние при создании.

Какие конструкции C# используются:

- конструктор;
- параметры по умолчанию.

Связанные темы:

- [[Конструктор]]

### Блок 4. Индексатор

Что делает: возвращает `Re` или `Im` по строковому ключу.

Почему нужен: демонстрирует тему создания индексатора.

Какие конструкции C# используются:

- `this[string part]`;
- `switch`;
- nullable-тип `double?`;
- `return null`.

Связанные темы:

- создание индексаторов;
- [[Инкапсуляция]].

### Блок 5. Строковое представление

Что делает: переопределяет `ToString`, чтобы комплексное число выводилось в математическом виде.

Почему нужен: без этого `Console.WriteLine(z)` вывел бы имя типа, а не красивое значение.

Какие конструкции C# используются:

- `override`;
- `StringBuilder`;
- условия `if`;
- `Math.Abs`.

Связанные темы:

- виртуальные и переопределенные методы.

### Блок 6. Сложение

Что делает: реализует сложение комплексных чисел тремя способами.

Почему нужен: показывает разницу между методом экземпляра, статическим методом и перегрузкой оператора.

Какие конструкции C# используются:

- метод экземпляра;
- `static`;
- `operator +`.

Связанные темы:

- методы;
- переопределение операторов.

### Блок 7. Сравнение и хеш-код

Что делает: сравнивает комплексные числа по значениям, а не по ссылкам.

Почему нужен: объекты класса должны сравниваться по математическому смыслу.

Какие конструкции C# используются:

- `operator ==`;
- `operator !=`;
- `Equals`;
- pattern matching `obj is Complex z`;
- `GetHashCode`.

Связанные темы:

- полиморфизм;
- переопределение методов;
- сравнение объектов.

## Связи

- Использует: `System.Text.StringBuilder`, `Math`, `HashCode`.
- Вызывается из: `ComplexTest.cs`.
- Работает с: объектами `Complex`.

## Что нужно уметь объяснить преподавателю

- Почему `Complex` является классом.
- Чем поля отличаются от свойств.
- Как работает конструктор с параметрами по умолчанию.
- Зачем нужен индексатор.
- Чем отличается `Plus` от `operator +`.
- Почему нужно переопределять `Equals` и `GetHashCode`.

## Возможные вопросы

### Почему `_re` без модификатора доступа все равно закрытое поле?

Потому что для членов класса в C# модификатор доступа по умолчанию — `private`.

### Что вернет `z9["Привет!"]`?

Вернет `null`, потому что строка не совпадает ни с одним допустимым вариантом.

### Почему `Abs` сделан свойством, а не методом?

Потому что снаружи модуль воспринимается как характеристика числа. При этом он вычисляется при обращении.

