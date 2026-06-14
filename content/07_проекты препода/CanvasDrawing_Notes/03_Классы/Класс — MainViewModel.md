# Класс — MainViewModel

## Исходный файл

`CanvasDrawing/MainViewModel.cs`

## Назначение класса

`MainViewModel` хранит коллекцию точек и команду для обработки движения мыши.

## Коллекция

```csharp
public ObservableCollection<Point> VisiblePoints { get; } = new();
```

## Команда

```csharp
public ICommand MouseMoveCommand { get; }
```

Команда создается как `RelayCommand<MouseEventArgs>`.

## Метод `OnMouseMove`

Получает позицию мыши, добавляет ее в коллекцию и удаляет старую точку, если точек больше 60.

## Что сказать на экзамене

ViewModel управляет данными для динамического отображения: интерфейс показывает содержимое `VisiblePoints`, а команда должна добавлять точки при движении мыши.

