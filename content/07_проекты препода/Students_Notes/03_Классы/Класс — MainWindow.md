# Класс — MainWindow

## Исходный файл

`Students/MainWindow.xaml.cs`

## Назначение класса

`MainWindow` — главное окно приложения.

## Поля

```csharp
private MainViewModel viewModel = new ();
```

## Конструктор

```csharp
public MainWindow()
{
    InitializeComponent();
    DataContext = viewModel;
}
```

Назначает ViewModel как `DataContext`.

## Обработчик закрытия

```csharp
private void Window_Closing(object sender, CancelEventArgs e)
{
    viewModel.SaveOnExit();
}
```

## Что сказать на экзамене

Окно является View. Оно не хранит бизнес-логику работы со студентами, а передает ее во ViewModel.

