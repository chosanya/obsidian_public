# Класс — MainWindow

## Исходный файл

`SmakLivery/MainWindow.xaml.cs`

## Назначение класса

`MainWindow` — главное окно приложения со списком заказов.

## Факты из кода

- Наследуется от `Window`.
- Создает поле `MainViewModel viewModel = new MainViewModel()`.
- В конструкторе вызывает `InitializeComponent()`.
- Устанавливает `DataContext = viewModel`.
- В обработчике `Window_Loaded` вызывает `viewModel.LoadOrdersAsync()`.

## XAML

В [[MainWindow.xaml]] расположен `ListView`, привязанный к `Orders`, и контекстное меню с командами добавления, редактирования и удаления.

## Пояснение

`MainWindow` играет роль View. Оно почти не содержит бизнес-логики: основная логика находится в [[Класс — MainViewModel]].

## Что требует ручной проверки

- `Window_Loaded` объявлен как `async void`.
- Окно вручную создает ViewModel, а не получает ее через DI.
