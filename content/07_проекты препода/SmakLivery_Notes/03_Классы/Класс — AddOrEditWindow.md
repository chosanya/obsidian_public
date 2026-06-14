# Класс — AddOrEditWindow

## Исходный файл

`SmakLivery/AddOrEditWindow.xaml.cs`

## Назначение класса

`AddOrEditWindow` — окно добавления или редактирования заказа.

## Факты из кода

- Наследуется от `Window`.
- Создает `AddEditViewModel`.
- Устанавливает `DataContext = viewModel`.
- Устанавливает `Form.DataContext = viewModel.Order`.
- Хранит флаг `ResultOk`.
- В `Save_Click` вызывает `viewModel.SaveCommand.Execute(null)`.
- В `Cancel_Click` вызывает `viewModel.CancelCommand.Execute(null)`.

## Пояснение

Окно использует два уровня контекста данных: само окно связано с ViewModel, а форма внутри окна — с объектом `Order`.

## Что требует ручной проверки

- Сохранение вызывается через обработчик `Click`, а не прямой Binding команды.
- `Save_Click` закрывает окно сразу после `Execute`, не ожидая завершения асинхронного сохранения.
- `CancelCommand` в ViewModel пустая.

## Связанные заметки

- [[Класс — AddEditViewModel]]
- [[AddOrEditWindow.xaml]]
- [[09_Проблемные_места]]
