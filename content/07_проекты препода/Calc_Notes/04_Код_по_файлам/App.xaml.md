# App.xaml

## Путь

`Calc/App.xaml`

## Назначение

Файл задает WPF-приложение и стартовое окно.

## Исходный код

```xml
﻿<Application x:Class="Calc.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:local="clr-namespace:Calc"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
         
    </Application.Resources>
</Application>
```

## Разбор

`StartupUri="MainWindow.xaml"` открывает главное окно при запуске.

