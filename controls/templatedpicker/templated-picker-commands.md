---
title: Commands
page_title: Commands
description: Check our &quot;Commands&quot; documentation article for Telerik TemplatedPicker for Xamarin control.
position: 7
slug: templated-picker-commands
---

# Commands

Templated Picker exposes the following commands:

* **ToggleCommand**(*ICommand*): Allows you to open and close the dialog
* **ClearCommand**(*ICommand*): Allows you to clear the displayed date/time.

The SelectorSettings property of the RadPickerBase class, allows you to add a custom logic for the Accept and Cancel commands which are executed when Ok and Cancel button are pressed. 

* **AcceptCommand**(*ICommand*): Defines the command which propagates the current selection of the picker. 
* **CancelCommand**(*ICommand*): Defines the command which rejects the current selection of the picker and closes the popup.

## Example

Here is the Templated Picker definition:

```XAML
<StackLayout>
    <Button Text="Toggle Command" Command="{Binding Source={x:Reference picker}, Path=ToggleCommand}"/>
    <Button Text="Clear Command" Command="{Binding Source={x:Reference picker}, Path=ClearCommand}"/>
    <telerikInput:RadTemplatedPicker x:Name="picker">
        <telerikInput:RadTemplatedPicker.SelectorTemplate>
            <ControlTemplate>
                <telerikInput:RadCalendar SelectedDate="{TemplateBinding SelectedValue, Mode=TwoWay}"/>
            </ControlTemplate>
        </telerikInput:RadTemplatedPicker.SelectorTemplate>
		<telerikInput:RadTemplatedPicker.SelectorSettings>
                <telerikInput:PickerPopupSelectorSettings AcceptCommand="{Binding Accept}"
                                                          CancelCommand="{Binding Cancel}"/>
            </telerikInput:RadTemplatedPicker.SelectorSettings>
            <telerikInput:RadTemplatedPicker.BindingContext>
                <local:ViewModel/>
            </telerikInput:RadTemplatedPicker.BindingContext>
    </telerikInput:RadTemplatedPicker>
</StackLayout>
```

a sample ViewModel:

```C#
public class ViewModel
{
    public ViewModel()
    {
        this.Accept = new Command(this.OnAccept);
        this.Accept = new Command(this.OnCancel);
    }

    private void OnAccept(object obj)
    {
        // implement your custom logic here
    }

    private void OnCancel(object obj)
    {
        // implement your custom logic here
    }

    public ICommand Accept { get; set; }
    public ICommand Cancel { get; set; }
}
```

also you will need to add the following namespace:

```XAML
xmlns:telerikInput="clr-namespace:Telerik.XamarinForms.Input;assembly=Telerik.XamarinForms.Input"
```

## See Also

- [Events]({%slug templated-picker-events%})
- [Templates]({%slug templated-picker-templates%})