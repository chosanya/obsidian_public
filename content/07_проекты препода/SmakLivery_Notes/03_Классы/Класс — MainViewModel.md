# Класс — MainViewModel

## Исходный файл

`SmakLivery/MainViewModel.cs`

## Назначение класса

`MainViewModel` хранит данные и команды главного окна.

## Факты из кода

- Реализует `INotifyPropertyChanged`.
- Хранит `ObservableCollection<OrderWithCourier> Orders`.
- Хранит выбранный заказ `SelectedOrder`.
- Создает команды `AddOrder`, `EditOrder`, `DeleteOrder`.
- Загружает данные через `DbHelper.GetOrders()`.

## Коллекция

```csharp
public ObservableCollection<OrderWithCourier> Orders { get; } = new ObservableCollection<OrderWithCourier>();
```

## Команды

- `AddOrder` открывает окно добавления.
- `EditOrder` открывает окно редактирования выбранного заказа.
- `DeleteOrder` удаляет заказ через БД и из коллекции.

## Пояснение

Это центральная ViewModel проекта. Она связывает интерфейс с данными из PostgreSQL.

## Что требует ручной проверки

- `SelectedOrder` не вызывает `OnPropertyChanged`.
- `LoadOrdersAsync()` скрывает ошибки через пустой `catch`.
- `DeleteOrder.CanExecute` проверяет `o is Order`, хотя команда удаления получает `OrderWithCourier`.
- Асинхронные лямбды передаются в `RelayCommand`, который принимает `Action<object?>`.

## Связанные заметки

- [[Класс — RelayCommand]]
- [[Класс — DbHelper]]
- [[Класс — OrderWithCourier]]
