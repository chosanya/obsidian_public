# Класс — MainWindow

## Исходный файл

`CanvasDrawing/MainWindow.xaml.cs`

## Назначение класса

`MainWindow` — главное окно приложения.

## Поля

```csharp
private MainViewModel viewModel = new MainViewModel();
```

## Конструктор

```csharp
public MainWindow()
{
    DataContext = viewModel;
    InitializeComponent();
}
```

Назначает ViewModel как `DataContext`.

## Что сказать на экзамене

Окно выступает как View. Оно создает ViewModel и отдает ее XAML-привязкам.

