# OOP5.csproj

## Путь

`OOP5/OOP5.csproj`

## Назначение

Файл описывает настройки консольного проекта `OOP5`.

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

`TargetFramework` равен `net9.0`.

`ImplicitUsings` включает стандартные пространства имен автоматически.

`Nullable` включает nullable-анализ.

## Что нужно уметь объяснить преподавателю

`.csproj` — файл проекта .NET, где указаны настройки сборки и целевая версия платформы.

