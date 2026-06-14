# Класс — Student

## Исходный файл

`Students/Student.cs`

## Назначение класса

`Student` — модель данных студента.

## Свойства

- `Id`;
- `LastName`;
- `FirstName`;
- `Group`;
- `Birthday`;
- `Level`;
- `Speciality`.

## Статическое поле

```csharp
private static int maxId = 0;
```

Хранит максимальный известный `Id`, чтобы генерировать следующий.

## Метод `GenerateId`

```csharp
public void GenerateId()
{
    Id = maxId + 1;
}
```

## Метод `ToString`

Возвращает строку вида:

```text
Id: Фамилия Имя
```

## Что сказать на экзамене

`Student` — модель MVVM. Она хранит данные, которые отображаются и редактируются через привязки в XAML.

