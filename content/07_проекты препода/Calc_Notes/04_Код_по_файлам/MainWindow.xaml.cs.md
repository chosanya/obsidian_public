# MainWindow.xaml.cs

## Путь

`Calc/MainWindow.xaml.cs`

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

namespace Calc
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private double _c = 0.0;
        private int _d = 0;
        public MainWindow()
        {
            InitializeComponent();
            List<string> themes = new List<string>() { "GreenBlueTheme", "OtherTheme" };
            ThemeSelector.ItemsSource = themes;
            ThemeSelector.SelectedIndex = 0;
        }

        private void Clear_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Сброс", "Действие:", MessageBoxButton.OK, MessageBoxImage.Information);
        }

        private void Digit_Click(object sender, RoutedEventArgs e)
        {  
            if (sender is Button btn)
            {

                string tag;
                switch (btn.Tag)
                {
                    case "pm": _c = -_c; break;
                    case ".": _d = 1 ; break;
                    default:
                        {
                            var digit = Double.Parse(btn.Tag.ToString());
                            if (_d == 0)
                            {
                                _c = (Math.Sign(_c) == 0 ? 1 : Math.Sign(_c)) * (Math.Abs(_c) * 10 + digit);
                            } else
                            {
                                _d *= 10;
                                _c = (Math.Sign(_c) ==0 ? 1 : Math.Sign(_c)) * (Math.Abs(_c) + digit/_d);
                            }
                            break;
                        }
                }
                Display.Text = _c.ToString();
            }
        }

        private void ThemeSelector_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {
            var style = ThemeSelector.SelectedItem as string;
            var uri = new Uri(style + ".xaml", UriKind.Relative);
            ResourceDictionary resourceDictionary = Application.LoadComponent(uri) as ResourceDictionary;
            Application.Current.Resources.Clear();
            Application.Current.Resources.MergedDictionaries.Add(resourceDictionary);
        }
    }
}
```

## Разбор

Файл реализует ввод цифр и переключение тем. Смена темы выполняется загрузкой XAML-словаря ресурсов.

