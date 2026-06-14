# MainWindow.xaml

## Путь

`Calc/MainWindow.xaml`

## Назначение

Файл описывает интерфейс калькулятора.

## Исходный код

```xml
﻿<Window x:Class="Calc.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:Calc"
        mc:Ignorable="d"
        Title="MainWindow" Height="500" Width="300">
	<Grid>
		<Grid.RowDefinitions>
			<RowDefinition Height="3*"/>
			<RowDefinition Height="*"/>
			<RowDefinition Height="*"/>
			<RowDefinition Height="*"/>
			<RowDefinition Height="*"/>
			<RowDefinition Height="*"/>
			<RowDefinition Height="Auto"/>
		</Grid.RowDefinitions>
		<Grid.ColumnDefinitions>
			<ColumnDefinition Width="*"/>
			<ColumnDefinition Width="*"/>
			<ColumnDefinition Width="*"/>
			<ColumnDefinition Width="*"/>
		</Grid.ColumnDefinitions>
		<TextBlock Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="4" x:Name="Display"/>
		<Button Tag="C" Content="C"   Grid.Column="0" Grid.Row="1" Style="{DynamicResource ClearButton}"/>
		<Button Tag="inv" Content="1/x" Grid.Column="1" Grid.Row="1" Style="{DynamicResource CommandButton}"/>
		<Button Tag="sqrt" Content="√"   Grid.Column="2" Grid.Row="1" Style="{DynamicResource CommandButton}"/>
		<Button Tag="/" Content="÷"   Grid.Column="3" Grid.Row="1" Style="{DynamicResource CommandButton}"/>
		<Button Tag="7" Content="7" Grid.Column="0" Grid.Row="2" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="8" Content="8" Grid.Column="1" Grid.Row="2" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="9" Content="9" Grid.Column="2" Grid.Row="2" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="*" Content="×" Grid.Column="3" Grid.Row="2" Style="{DynamicResource CommandButton}" />
		<Button Tag="4" Content="4" Grid.Column="0" Grid.Row="3" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="5" Content="5" Grid.Column="1" Grid.Row="3" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="6" Content="6" Grid.Column="2" Grid.Row="3" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="-" Content="-" Grid.Column="3" Grid.Row="3" Style="{DynamicResource CommandButton}"/>
		<Button Tag="1" Content="1" Grid.Column="0" Grid.Row="4" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="2" Content="2" Grid.Column="1" Grid.Row="4" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="3" Content="3" Grid.Column="2" Grid.Row="4" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="+" Content="+" Grid.Column="3" Grid.Row="4" Style="{DynamicResource CommandButton}"/>
		<Button Tag="pm" Content="±" Grid.Column="0" Grid.Row="5" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="0" Content="0" Grid.Column="1" Grid.Row="5" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="." Content="," Grid.Column="2" Grid.Row="5" Style="{DynamicResource DigitButton}" Click="Digit_Click"/>
		<Button Tag="=" Content="=" Grid.Column="3" Grid.Row="5" Style="{DynamicResource EqButton}"/>
		<ComboBox Grid.Row="6" Grid.ColumnSpan="4" x:Name="ThemeSelector" SelectionChanged="ThemeSelector_SelectionChanged"/>
	</Grid>
</Window>
```

## Разбор

Окно использует `Grid`, кнопки с `Tag`, стили через `DynamicResource` и `ComboBox` для выбора темы.

