# Класс — App

## Исходный файл

`Calc/App.xaml.cs`

## Назначение класса

`App` представляет WPF-приложение и наследуется от `Application`.

## Наследование

```csharp
public partial class App : Application
```

## Связь с XAML

В `App.xaml` указано стартовое окно:

```xml
StartupUri="MainWindow.xaml"
```

## Что сказать на экзамене

`App` запускает WPF-приложение, а `StartupUri` определяет первое открываемое окно.

