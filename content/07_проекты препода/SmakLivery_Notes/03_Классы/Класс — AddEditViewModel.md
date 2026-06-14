# Класс — AddEditViewModel

## Исходный файл

`SmakLivery/AddEditViewModel.cs`

## Назначение класса

`AddEditViewModel` управляет данными формы добавления или редактирования заказа.

## Факты из кода

- Хранит `Order Order`.
- Хранит команды `CancelCommand` и `SaveCommand`.
- Создает копию переданного заказа.
- Свойство `SaveButtonText` меняет текст кнопки в зависимости от `Order.Id`.
- `SaveCommand` вызывает `DbHelper.AddOrderAsync()` или `DbHelper.EditOrderAsync()`.

## Пояснение

ViewModel отделяет логику сохранения от окна, но не полностью управляет закрытием окна.

## Что требует ручной проверки

- `CancelCommand` ничего не делает.
- `SaveCommand` асинхронная, но `RelayCommand` не умеет возвращать `Task`.
- При добавлении заказа `CourierId` не передается в SQL `INSERT`.

## Связанные заметки

- [[Класс — Order]]
- [[Класс — DbHelper]]
- [[Класс — RelayCommand]]
