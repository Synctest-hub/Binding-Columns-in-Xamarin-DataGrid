# How to bind and control the columns on SfDataGrid using the MVVM pattern.

This article demonstrates how to bind and control the columns on SfDataGrid.

To achieve this, a bindable SfGridColumns property is exposed in the ViewModel. This property remains synchronized with the grid’s current selection and also updates the grid when its value changes from the ViewModel, ensuring two-way communication between the UI and the data layer.

## Xaml#:

```xml
<sfgrid:SfDataGrid x:Name="dataGrid"
                    ItemsSource="{Binding State}" 
                    Columns="{Binding SfGridColumns}"
                    NavigationMode="Cell"
                    ColumnSizer="Auto"
                    SelectionMode="Multiple"
                    AutoGenerateColumns="False">
</sfgrid:SfDataGrid>
```

## C#:

```C#
class ViewModel : INotifyPropertyChanged
{
    public Columns SfGridColumns
    {
        get
        {
            return column;
        }
        set
        {
            column = value;
        }
    }

    private void GenerateColumn()
    {
        SfGridColumns.Add(new GridTextColumn() { MappingName = "Name" });
        SfGridColumns.Add(new GridTextColumn() { MappingName = "LargestCity" });
        SfGridColumns.Add(new GridNumericColumn() { MappingName = "Population" });
    }
}
```