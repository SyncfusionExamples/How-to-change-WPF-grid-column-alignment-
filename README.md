# How-to-change-WPF-grid-column-alignment
## About the sample
This example illustrates how to align a column content in WPF DataGrid by enabling TextAlignment and VerticalAlignment properties

### Column alignment for manual generation
You can change the content alignment of [GridColumn](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn.html) using [TextAlignment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~TextAlignment.html) and [VerticalAlignment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~VerticalAlignment.html) properties.

```xml
<syncfusion:SfDataGrid  x:Name="dataGrid" 
                        AutoGenerateColumns="False"
                        ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="OrderID" 
                                   HeaderText="Order ID"
                                   TextAlignment="Left"  
                                   VerticalAlignment="Center"/>
        <syncfusion:GridTextColumn MappingName="CustomerID" 
                                   HeaderText="Customer ID"
                                   TextAlignment="Center"  
                                   VerticalAlignment="Center"/>
        <syncfusion:GridTextColumn MappingName="CustomerName" 
                                   HeaderText="Customer Name"
                                   TextAlignment="Center"  
                                   VerticalAlignment="Center"/>
        <syncfusion:GridTextColumn MappingName="Country" 
                                   HeaderText="Country"
                                   TextAlignment="Center"  
                                   VerticalAlignment="Center"/>
        <syncfusion:GridTextColumn MappingName="ShipCity" 
                                   HeaderText="Ship City"
                                   TextAlignment="Right"  
                                   VerticalAlignment="Center"/>
    </syncfusion:SfDataGrid.Columns>

</syncfusion:SfDataGrid>
```

### Column alignment for autogeneration
You can change the auto generating columns alignment by using the [AutoGeneratingColumn](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AutoGeneratingColumn_EV.html) event.

```c#
this.dataGrid.AutoGeneratingColumn += DataGrid_AutoGeneratingColumn;
private void DataGrid_AutoGeneratingColumn(object sender, Syncfusion.UI.Xaml.Grid.AutoGeneratingColumnArgs e)
 {
         e.Column.TextAlignment = TextAlignment.Center;
         e.Column.VerticalAlignment = VerticalAlignment.Center;
 }
```

### Column header alignment for manual generation
You can change the column header alignment using [HorizontalHeaderContentAlignment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~HorizontalHeaderContentAlignment.html) property.

```xml
<syncfusion:SfDataGrid  x:Name="dataGrid" 
                        AutoGenerateColumns="False"
                        ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="OrderID" 
                                   HeaderText="Order ID"
                                   HorizontalHeaderContentAlignment="Left"/>
        <syncfusion:GridTextColumn MappingName="CustomerID" 
                                   HeaderText="Customer ID"
                                   HorizontalHeaderContentAlignment="Center"/>
        <syncfusion:GridTextColumn MappingName="CustomerName" 
                                   HeaderText="Customer Name"
                                   HorizontalHeaderContentAlignment="Center"/>
        <syncfusion:GridTextColumn MappingName="Country" 
                                   HeaderText="Country"
                                   HorizontalHeaderContentAlignment="Center"/>
        <syncfusion:GridTextColumn MappingName="ShipCity" 
                                   HeaderText="Ship City"
                                   HorizontalHeaderContentAlignment="Right"/>
    </syncfusion:SfDataGrid.Columns>

</syncfusion:SfDataGrid>
```

### Column header alignment for autogeneration
You can change the column header alignment for auto generating columns by using the [AutoGeneratingColumn](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AutoGeneratingColumn_EV.html) event.

```c#
this.dataGrid.AutoGeneratingColumn += DataGrid_AutoGeneratingColumn;
private void DataGrid_AutoGeneratingColumn(object sender, Syncfusion.UI.Xaml.Grid.AutoGeneratingColumnArgs e)
{
    e.Column.HorizontalHeaderContentAlignment = HorizontalAlignment.Center;
}
```

### Styles for GridColumn
You can customize the background and foreground colors for [GridColumn](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn.html).

```xml
<syncfusion:SfDataGrid  x:Name="dataGrid" 
                        AutoGenerateColumns="False"
                        ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="OrderID" 
                                   HeaderText="Order ID">
            <syncfusion:GridTextColumn.CellStyle>
                <Style TargetType="syncfusion:GridCell">
                    <Setter Property="Background" Value="Bisque" />
                    <Setter Property="Foreground" Value="Green"/>
                </Style>
            </syncfusion:GridTextColumn.CellStyle>
        </syncfusion:GridTextColumn>
                                  
        <syncfusion:GridTextColumn MappingName="CustomerID" 
                                   HeaderText="Customer ID"/>
        <syncfusion:GridTextColumn MappingName="CustomerName" 
                                   HeaderText="Customer Name"/>
        <syncfusion:GridTextColumn MappingName="Country" 
                                   HeaderText="Country"/>
        <syncfusion:GridTextColumn MappingName="ShipCity" 
                                   HeaderText="Ship City"/>
    </syncfusion:SfDataGrid.Columns>

</syncfusion:SfDataGrid>
```

### Conditional styles for GridColumn
You can customize the foreground and background color of the [GridColumn](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn.html) content based on condition.

```xml
<Window.DataContext>
    <local:ViewModel/>
</Window.DataContext>
<Window.Resources>
   <local:ColorConverter x:Key="converter"/>
</Window.Resources>
<Grid>
    <syncfusion:SfDataGrid  x:Name="dataGrid" 
                            AutoGenerateColumns="False"
                            ItemsSource="{Binding Orders}">
        <syncfusion:SfDataGrid.Columns>
            <syncfusion:GridTextColumn MappingName="OrderID" 
                                       HeaderText="Order ID">
                <syncfusion:GridTextColumn.CellStyle>
                    <Style TargetType="syncfusion:GridCell">
                        <Setter Property="Background" Value="{Binding Path=OrderID,Converter={StaticResource converter}}"/>
                    </Style>
                </syncfusion:GridTextColumn.CellStyle>
            </syncfusion:GridTextColumn>
                                      
            <syncfusion:GridTextColumn MappingName="CustomerID" 
                                       HeaderText="Customer ID"/>
            <syncfusion:GridTextColumn MappingName="CustomerName" 
                                       HeaderText="Customer Name"/>
            <syncfusion:GridTextColumn MappingName="Country" 
                                       HeaderText="Country"/>
            <syncfusion:GridTextColumn MappingName="ShipCity" 
                                       HeaderText="Ship City"/>
        </syncfusion:SfDataGrid.Columns>

    </syncfusion:SfDataGrid>
</Grid>
```

```c#
public class ColorConverter : IValueConverter
 {
     public object Convert(object value, Type targetType, object parameter, CultureInfo culture)
     {
         int input = (int)value;

         //custom condition is checked based on data.

         if (input % 2 == 0)
             return new SolidColorBrush(Colors.LightBlue);

         else 
             return new SolidColorBrush(Colors.Bisque);
     }

     public object ConvertBack(object value, Type targetType, object parameter, CultureInfo culture)
     {
         throw new NotImplementedException();
     }
 }
```

## Requirements to run the demo
Visual Studio 2015 and above versions
