# Класс — App

## Исходный файл

`Integr/App.xaml.cs`

## Назначение класса

`App` — класс WPF-приложения. Он наследуется от `Application`.

## Наследование

```csharp
public partial class App : Application
```

## Связь с XAML

Класс связан с `App.xaml`, где указано:

```xml
StartupUri="MainWindow.xaml"
```

## Что сказать на экзамене

`App` представляет приложение целиком. Через `StartupUri` WPF понимает, какое окно открыть первым.

