# Класс — MainWindow

## Исходный файл

`Integr/MainWindow.xaml.cs`

## Назначение класса

`MainWindow` — главное окно WPF-приложения. Оно принимает ввод пользователя, вызывает вычисление интеграла и выводит результат.

## Наследование

```csharp
public partial class MainWindow : Window
```

## Конструктор

```csharp
public MainWindow()
{
    InitializeComponent();
}
```

`InitializeComponent` загружает XAML-разметку окна.

## Обработчик события

```csharp
private void Button_Click(object sender, RoutedEventArgs e)
```

Метод вызывается при нажатии кнопки `вычислить`.

## Что делает обработчик

1. Читает текст из `TextBox` `A`, `B`, `N`.
2. Преобразует строки в числа.
3. Создает `Integrator`.
4. Вызывает `IntegrateByMidpointRule`.
5. Записывает результат в `Result.Text`.
6. При ошибке показывает `MessageBox`.

## Что сказать на экзамене

Это пример code-behind: событие кнопки связано с методом в классе окна.

