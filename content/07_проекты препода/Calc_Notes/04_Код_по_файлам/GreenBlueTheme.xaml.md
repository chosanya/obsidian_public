# GreenBlueTheme.xaml

## Путь

`Calc/GreenBlueTheme.xaml`

## Назначение

Файл содержит словарь ресурсов со стилями кнопок для зелено-синей темы.

## Исходный код

```xml
﻿<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
					>
	<Style x:Key="Button">
		<Setter Property="Control.FontFamily" Value="Cambria" />
		<Setter Property="Control.FontSize" Value="18" />
		<Setter Property="Control.Margin" Value="4" />
		<Setter Property="Control.Foreground" Value="Black" />
	</Style>
	<Style x:Key="DigitButton" BasedOn="{StaticResource Button}">
		<Setter Property="Control.Background" Value="LightGreen"/>
		<Setter Property="Control.FontWeight" Value="Regular" />
		<!--EventSetter Event="Button.Click" Handler="Digit_Click" /-->
	</Style>
	<Style x:Key="CommandButton" BasedOn="{StaticResource Button}">
		<Setter Property="Control.Background" Value="LightBlue"/>
		<Setter Property="Control.FontWeight" Value="UltraBlack" />
	</Style>
	<Style x:Key="ClearButton" BasedOn="{StaticResource Button}">
		<Setter Property="Control.FontWeight" Value="UltraBlack" />
		<Setter Property="Control.Foreground" Value="White" />
		<Setter Property="Control.Background">
			<Setter.Value>
				<LinearGradientBrush>
					<LinearGradientBrush.GradientStops>
						<GradientStop Color="Red" Offset="0"/>
						<GradientStop Color="DarkRed" Offset="1"/>
					</LinearGradientBrush.GradientStops>
				</LinearGradientBrush>
			</Setter.Value>
		</Setter>
		<!--EventSetter Event="Button.Click" Handler="Clear_Click" /-->
	</Style>
	<Style x:Key="EqButton" BasedOn="{StaticResource CommandButton}">
		<Setter Property="Control.Foreground" Value="White" />
		<Setter Property="Control.Background">
			<Setter.Value>
				<LinearGradientBrush>
					<LinearGradientBrush.GradientStops>
						<GradientStop Color="Green" Offset="0"/>
						<GradientStop Color="DarkGreen" Offset="1"/>
					</LinearGradientBrush.GradientStops>
				</LinearGradientBrush>
			</Setter.Value>
		</Setter>
	</Style>
</ResourceDictionary>
```

## Разбор

Стили имеют ключи `DigitButton`, `CommandButton`, `ClearButton`, `EqButton` и наследуются через `BasedOn`.

