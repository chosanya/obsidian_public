# SmakLivery.csproj

## Путь

`SmakLivery/SmakLivery.csproj`

## Назначение

Файл проекта задает .NET, WPF и зависимость Npgsql.

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
    <PackageReference Include="Npgsql" Version="10.0.2" />
  </ItemGroup>

</Project>
```

## Разбор

Проект таргетит `net10.0-windows`, поэтому сборка на macOS требует отдельного условия Windows-targeting.

## Факты из кода

- Файл входит в проект `SmakLivery`.
- Исходный код выше сохранен без правок.

## Связанные заметки

- [[00_Обзор]]
- [[02_Архитектура]]
- [[09_Проблемные_места]]
