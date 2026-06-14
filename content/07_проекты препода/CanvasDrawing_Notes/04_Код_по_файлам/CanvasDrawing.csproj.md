# CanvasDrawing.csproj

## Путь

`CanvasDrawing/CanvasDrawing.csproj`

## Назначение

Файл описывает настройки WPF-проекта и зависимости.

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

  <ItemGroup>
    <PackageReference Include="Microsoft.Xaml.Behaviors.Wpf" Version="1.1.142" />
    <PackageReference Include="MvvmLightLibs" Version="5.4.1.1" />
  </ItemGroup>

</Project>
```

## Разбор

Проект подключает behaviors для WPF и MVVM Light.

