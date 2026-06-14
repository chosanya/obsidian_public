# Calc.csproj

## Путь

`Calc/Calc.csproj`

## Назначение

Файл описывает настройки WPF-проекта.

## Исходный код

```xml
﻿<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net10.0-windows</TargetFramework>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## Разбор

`UseWPF=true` включает WPF, а `net10.0-windows` означает Windows-таргет.

