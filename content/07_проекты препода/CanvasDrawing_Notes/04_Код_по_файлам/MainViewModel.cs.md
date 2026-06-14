# MainViewModel.cs

## Путь

`CanvasDrawing/MainViewModel.cs`

## Назначение

Файл содержит ViewModel приложения.

## Исходный код

```csharp
﻿using GalaSoft.MvvmLight.Command;
using System;
using System.Collections.Generic;
using System.Collections.ObjectModel;
using System.ComponentModel;
using System.Runtime.CompilerServices;
using System.Text;
using System.Windows;
using System.Windows.Input;

namespace CanvasDrawing
{
    public class MainViewModel : INotifyPropertyChanged
    {

        public event PropertyChangedEventHandler? PropertyChanged;
        private void OnPropertyChanged([CallerMemberName] string name = null) =>
            PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(name));
        private const int maxPointsCount = 60;
        public ObservableCollection<Point> VisiblePoints { get; } = new();
        public ICommand MouseMoveCommand { get; }

        public MainViewModel()
        {
            MouseMoveCommand = new RelayCommand<MouseEventArgs>(OnMouseMove);
        }

        private void OnMouseMove(MouseEventArgs args)
        {
            if (args?.Source is UIElement source)
            {
                var position = args.GetPosition(source);
                VisiblePoints.Add(position);

                if (VisiblePoints.Count > maxPointsCount)
                {
                    VisiblePoints.RemoveAt(0);
                }
            }
        }

    }
}
```

## Разбор

ViewModel добавляет точки в `VisiblePoints`. Коллекция привязана к `ItemsControl`.

