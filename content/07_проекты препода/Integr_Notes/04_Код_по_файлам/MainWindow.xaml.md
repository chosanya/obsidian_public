# MainWindow.xaml

## Путь

`Integr/MainWindow.xaml`

## Назначение

Файл описывает интерфейс главного окна WPF.

## Исходный код

```xml
﻿<Window x:Class="Integr.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:Integr"
        mc:Ignorable="d"
        Title="MainWindow" Height="300" Width="800">
    <Grid>
		<Grid.RowDefinitions>
			<RowDefinition Height="Auto"/>
			<RowDefinition Height="Auto"/>
			<RowDefinition Height="Auto"/>
			<RowDefinition Height="Auto"/>
		</Grid.RowDefinitions>
		<Grid.ColumnDefinitions>
			<ColumnDefinition Width="Auto"/>
			<ColumnDefinition Width="*"/>
			<ColumnDefinition Width="Auto"/>
			<ColumnDefinition Width="*"/>
			<ColumnDefinition Width="Auto"/>
			<ColumnDefinition Width="*"/>
		</Grid.ColumnDefinitions>
		<TextBlock Grid.Row="0" Grid.Column="0" Text="a = " FontSize="20" Margin="8,18"/>
		<TextBlock Grid.Row="0" Grid.Column="2" Text="b = " FontSize="20" Margin="8,18"/>
		<TextBlock Grid.Row="0" Grid.Column="4" Text="n = " FontSize="20" Margin="8,18"/>
		<TextBox Grid.Row="0" x:Name="A" Grid.Column="1" Margin="8,18" />
		<TextBox Grid.Row="0" x:Name="B" Grid.Column="3" Margin="8,18"/>
		<TextBox Grid.Row="0" x:Name="N" Grid.Column="5" Margin="8,18"/>
		<TextBlock Grid.Row="1" Grid.ColumnSpan="6" Text=" f(x) = sin(x^2) + 5cos^2(2x)" TextAlignment="Center" FontSize="20" FontWeight="Bold" Margin="8,18"/>
		<Button Grid.Row="2" Grid.ColumnSpan="2" Grid.Column="2" Click="Button_Click" Content="вычислить" FontSize="20" Width="Auto" Margin="8,18"/>
		<TextBlock Grid.Row="3" Grid.Column="1" Text="Результат:" TextAlignment="Right" FontSize="20" Margin="8,18"/>
		<TextBlock Grid.Row="3" x:Name="Result" Grid.ColumnSpan="4" Grid.Column="2" Margin="8,18"/>

	</Grid>
</Window>
```

## Разбор

Окно построено на `Grid`. Ввод выполняется через `TextBox`, запуск вычисления через `Button`, результат выводится в `TextBlock`.

