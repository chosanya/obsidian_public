# Класс — OrderEnumDisplayConverter

## Исходный файл

`SmakLivery/OrderEnumDisplayConverter.cs`

## Назначение класса

`OrderEnumDisplayConverter` преобразует значение `OrderStatus` в строку для интерфейса.

## Факты из кода

- Реализует `IValueConverter`.
- В `Convert` проверяет, что значение является `OrderStatus`.
- Через reflection получает поле enum.
- Читает `DisplayAttribute`.
- Возвращает `attr.Name` или имя enum.
- `ConvertBack` бросает `NotSupportedException`.

## Где используется

- В [[MainWindow.xaml]] для колонки статуса.
- В [[AddOrEditWindow.xaml]] для отображения элементов `ComboBox`.

## Пояснение

Без конвертера пользователь видел бы технические имена вроде `OutForDelivery`. Конвертер показывает русскоязычный текст из `[Display(Name = ...)]`.

## Что требует ручной проверки

- `ConvertBack` не поддерживается, но для текущего `ComboBox` выбранный элемент остается самим `OrderStatus`, поэтому обратное преобразование не требуется.

## Связанные заметки

- [[Перечисление — OrderStatus]]
- [[05_Темы_ООП]]
