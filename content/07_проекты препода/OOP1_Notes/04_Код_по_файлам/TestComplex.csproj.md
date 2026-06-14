# TestComplex.csproj

## Путь

`TestComplex/TestComplex.csproj`

## Назначение

Файл описывает тестовый проект. Он подключает xUnit и ссылается на основной проект `OOP1`.

## Исходный код

```xml
﻿<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net9.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
    <IsPackable>false</IsPackable>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="coverlet.collector" Version="6.0.2" />
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="17.12.0" />
    <PackageReference Include="xunit" Version="2.9.2" />
    <PackageReference Include="xunit.runner.visualstudio" Version="2.8.2" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\OOP1\OOP1.csproj" />
  </ItemGroup>

  <ItemGroup>
    <Using Include="Xunit" />
  </ItemGroup>

</Project>
```

## Разбор

Факты из кода:

- тестовый проект использует `net9.0`;
- проект не предназначен для упаковки как NuGet-пакет;
- подключены пакеты xUnit;
- есть ссылка на основной проект.

Пояснение:

`ProjectReference` позволяет тестам видеть класс `Complex` из основного проекта.

## Что нужно уметь объяснить преподавателю

Тестовый проект отделен от основного кода. Это удобно, потому что тесты проверяют поведение класса, но не смешиваются с логикой приложения.

