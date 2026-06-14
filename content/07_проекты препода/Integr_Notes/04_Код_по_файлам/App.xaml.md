# App.xaml

## Путь

`Integr/App.xaml`

## Назначение

Файл задает WPF-приложение и стартовое окно.

## Исходный код

```xml
﻿<Application x:Class="Integr.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:local="clr-namespace:Integr"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
         
    </Application.Resources>
</Application>
```

## Разбор

`StartupUri="MainWindow.xaml"` означает, что при запуске откроется главное окно.

