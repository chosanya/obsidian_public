# Класс — OrderWithCourier

## Исходный файл

`SmakLivery/OrderWithCourier.cs`

## Назначение класса

`OrderWithCourier` — модель для отображения заказа вместе с данными курьера.

## Факты из кода

Содержит свойства заказа:

- `Id`.
- `Address`.
- `Status`.
- `CourierId`.

Содержит свойства курьера:

- `CourierFirstName`.
- `CourierLastName`.
- `Transport`.

Вычисляемое свойство:

```csharp
public string CourierName => CourierFirstName + " " + CourierLastName;
```

Метод:

```csharp
public Order ToOrder()
```

## Пояснение

Этот класс удобен для `ListView`: в таблице можно показать и данные заказа, и ФИО курьера.

## Что требует ручной проверки

- Класс не реализует `INotifyPropertyChanged`.
- `CourierName` просто склеивает имя и фамилию.
- Данные курьера появляются только если SQL `JOIN` нашел курьера.

## Связанные заметки

- [[Класс — Order]]
- [[Класс — DbHelper]]
