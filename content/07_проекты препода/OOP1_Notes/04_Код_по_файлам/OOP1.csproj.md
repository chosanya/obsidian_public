# OOP1.csproj

## Путь

`OOP1/OOP1.csproj`

## Назначение

Файл описывает настройки основного консольного проекта.

## Исходный код

```xml
﻿<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net9.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## Разбор

`OutputType` равен `Exe`, значит проект собирается как исполняемое консольное приложение.

`TargetFramework` равен `net9.0`, значит проект рассчитан на .NET 9.

`ImplicitUsings` включает автоматические стандартные `using`.

`Nullable` включает nullable-анализ. Поэтому типы вроде `object?` и `double?` имеют значение для компилятора.

## Что нужно уметь объяснить преподавателю

`.csproj` — это файл проекта .NET. В нем указывается тип сборки, целевая платформа и настройки компиляции.

