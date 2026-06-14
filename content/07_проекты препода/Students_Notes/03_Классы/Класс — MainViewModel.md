# Класс — MainViewModel

## Исходный файл

`Students/MainViewModel.cs`

## Назначение класса

`MainViewModel` хранит состояние экрана: список студентов, выбранного студента и команды кнопок.

## Коллекция

```csharp
ObservableCollection<Student> students = new ObservableCollection<Student>();
public ObservableCollection<Student> Students => students;
```

`ObservableCollection` уведомляет интерфейс об изменении списка.

## Выбранный студент

```csharp
public Student? SelectedStudent
```

При изменении вызывает `OnPropertyChanged`.

## Команды

- `AddButtonPress`;
- `ExpelButtonPress`;
- `SaveButtonPress`.

## Работа с JSON

В конструкторе данные читаются из `students.json`.

В `SaveAll` коллекция сериализуется обратно в файл.

## Что сказать на экзамене

`MainViewModel` связывает View и Model. View обращается к свойствам и командам через Data Binding, а ViewModel управляет данными и сохранением.

