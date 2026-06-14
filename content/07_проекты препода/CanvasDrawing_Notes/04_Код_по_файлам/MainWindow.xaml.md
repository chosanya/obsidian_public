# MainWindow.xaml

## Путь

`CanvasDrawing/MainWindow.xaml`

## Назначение

Файл описывает отображение точек на Canvas.

## Исходный код

```xml
﻿<Window x:Class="CanvasDrawing.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:CanvasDrawing"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Grid>
		<ItemsControl ItemsSource="{Binding VisiblePoints}" >
			<ItemsControl.ItemsPanel>
				<ItemsPanelTemplate>
					<Canvas />
				</ItemsPanelTemplate>
			</ItemsControl.ItemsPanel>

			<ItemsControl.ItemTemplate>
				<DataTemplate>
					<Ellipse Width="10" Height="10" Fill="#40FF81" Opacity="0.75" />
				</DataTemplate>
			</ItemsControl.ItemTemplate>

			<ItemsControl.ItemContainerStyle>
				<Style TargetType="ContentPresenter">
					<Setter Property="Canvas.Left" Value="{Binding X}"/>
					<Setter Property="Canvas.Top" Value="{Binding Y}"/>
				</Style>
			</ItemsControl.ItemContainerStyle>
		</ItemsControl>

		<Canvas Background="Transparent"/>
	</Grid>
</Window>
```

## Разбор

`ItemsControl` отображает точки как `Ellipse`. Координаты задаются через `Canvas.Left` и `Canvas.Top`.

## Проблемное место

В XAML нет привязки `MouseMove` к `MouseMoveCommand`.

