---
type: comparison
discipline: OOP
language: C#
tags:
  - сравнение
---
# override и new

> [!tip] Простыми словами: Сравнение помогает не спутать настоящую замену метода и простое скрытие имени.

### Переопределение и скрытие

> [!definition]
> Переопределение: 
> public virtual void MakeSound() 
> public override void MakeSound() 
> Выбор метода зависит от реального типа объекта.

> [!definition]
> Скрытие: 
> public void MakeSound() 
> public new void MakeSound() 
> Выбор зависит от типа переменной.

Пример:

```csharp
Dog dog = new Dog();
Animal animal = new Dog();
dog.MakeSound();
animal.MakeSound();
```

При скрытии методы могут сработать по-разному: Гав, Животное

*Это очень вероятный дополнительный вопрос преподавателя, судя по отзывам.*
## Связи
- Связано с: [[override]]
- Связано с: [[new как скрытие метода]]
- Связано с: [[4. Полиморфизм]]

## Источник
- файл: `4.tex`
- раздел: Переопределение и скрытие
