# MainWindow.xaml.cs

## Путь

`SmakLivery/MainWindow.xaml.cs`

## Назначение

Файл содержит code-behind главного окна [[Класс — MainWindow]].

## Исходный код

```csharp
﻿using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

namespace SmakLivery
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private MainViewModel viewModel = new MainViewModel();
        public MainWindow()
        {
            InitializeComponent();
            DataContext = viewModel;
        }

        private async void Window_Loaded(object sender, RoutedEventArgs e)
        {
            await viewModel.LoadOrdersAsync();
        }
    }
}
```

## Разбор

Здесь устанавливается `DataContext` и запускается загрузка заказов.

## Факты из кода

- Файл входит в проект `SmakLivery`.
- Исходный код выше сохранен без правок.

## Связанные заметки

- [[00_Обзор]]
- [[02_Архитектура]]
- [[09_Проблемные_места]]
