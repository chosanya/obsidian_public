# AddOrEditWindow.xaml.cs

## Путь

`SmakLivery/AddOrEditWindow.xaml.cs`

## Назначение

Файл содержит code-behind окна [[Класс — AddOrEditWindow]].

## Исходный код

```csharp
﻿using System;
using System.Collections.Generic;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Animation;
using System.Windows.Media.Imaging;
using System.Windows.Shapes;

namespace SmakLivery
{
    /// <summary>
    /// Логика взаимодействия для AddOrEditWindow.xaml
    /// </summary>
    public partial class AddOrEditWindow : Window
    {
        private AddEditViewModel viewModel;
        public bool ResultOk { get; private set; } = false;
        public AddOrEditWindow(Order order)
        {
            viewModel = new AddEditViewModel(order);
            InitializeComponent();
            DataContext = viewModel;
            Form.DataContext = viewModel.Order;
        }

        private void Save_Click(object sender, RoutedEventArgs e)
        {
            viewModel.SaveCommand.Execute(null);
            ResultOk = true;
            Close();
        }

        private void Cancel_Click(object sender, RoutedEventArgs e)
        {
            viewModel.CancelCommand.Execute(null);
            Close();
        }
    }
}
```

## Разбор

Здесь обработчики кнопок вручную вызывают команды ViewModel.

## Факты из кода

- Файл входит в проект `SmakLivery`.
- Исходный код выше сохранен без правок.

## Связанные заметки

- [[00_Обзор]]
- [[02_Архитектура]]
- [[09_Проблемные_места]]
