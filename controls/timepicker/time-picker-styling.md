---
title: Styling
page_title: Xamarin Time Picker Documentation | Styling
description: Check our &quot;Styling&quot; documentation article for Telerik TimePicker for Xamarin control.
position: 8
slug: time-picker-styling
---

# Styling

## TimePicker Styling

Time Picker control for Xamаrin provides the following Style properties for customizing its look:

* **SpinnerStyle**(of type *Style* with target type **telerikDataControls:RadSpinner**): Defines the style applied to the spinner item and selected item.
* **SpinnerHeaderStyle**(of type *Style* with target type **Xamarin.Forms.Label**): Specifies the style applied to the spinner header labels.
* **SelectionHighlightStyle**(of type *Style* with target type **telerikPrimitives:RadBorder**): Specifies the style applied to the selection inside the popup. 
* **PlaceholderLabelStyle**(of type *Style* with target type **Xamarin.Forms.Label**): Defines the style applied to the placeholder label. 
* **DisplayLabelStyle**(of type *Style* with target type **Xamarin.Forms.Label**): Defines the style applied to the label which is visualized when time is selected.

In addition, RadTimePicker exposes properties for specifying its border style and background color, namely:

* **BackgroundColor**(*Xamarin.Forms.Color*): Defines the background color of the picker.
* **BorderColor**(*Xamarin.Forms.Color*): Defines the border color of the picker.
* **BorderThickness**(*Xamarin.Forms.Thickness*): Specifies the border thickness of the picker. Default value is `new Thickness(0,0,0,1)`.
* **CornerRadius**(*Xamarin.Forms.Thinckness*): Specifies the corner radius of the picker.

## Popup Styling

Using the **SelectorSettings** property (of type *Telerik.XamarinForms.Input.PickerPopupSelectorSettings*) of the TimePicker you can modify the appearance of the dialog (popup). PickerPopupSelectorSettings class exposes the following Style properties:

* **PopupViewStyle**(of type *Style* with target type **telerikInput:PickerPopupContentView**): Defines the popup view style.
* **HeaderStyle**(of type *Style* with target type **telerikInput:PickerPopupHeaderView**): Defines the popup header style.
* **HeaderLabelStyle**(of type *Style* with target type **Xamarin.Forms.Label**): Defines the popup header label style.
* **FooterStyle**(of type *Style* with target type **telerikInput:PickerPopupFooterView**): Defines the popup footer style.
* **AcceptButtonStyle**(of type *Style* with target type **Xamarin.Forms.Button**): Defines the Accept button style.
* **CancelButtonStyle**(of type *Style* with target type **Xamarin.Forms.Button**): Defines the Cancel button style.

The SelectorSettings also provides the following properties for popup customization:

* **PopupOutsideBackgroundColor**(*Xamarin.Forms.Color*): Defines the color outside of the popup.
* **IsPopupModal**(*bool*): Defines a boolean value indicating if the popup should be closed when tapped outside of the popup. 
	* When *IsPopupModal="True"*  the UI behind the popup gets inactive and cannot be used until the popup is closed. 
	* When *IsPopupModal="False"* the popup could be closed when clicking outside the popup. By default the value of the **IsPopupModal** is **false**.
	
* **HeaderLabelText**(*string*): Specifies the text visualized in the popup header.
* **IsHeaderVisible**(*bool*): Specifies whether the Popup header is currently visible. By default the valuse is *True*.
* **IsFooterVisible**(*bool*): Specifies whether the Popup footer is currently visible. By default the valuse is *True*.
* **AcceptButtonText**(*string*): Defines the text visualized for the accept button. By default the text is *OK*.
* **CancelButtonText**(*string*): Defines the text visualized for the cancel button. By default the text is *Cancel*. 

## Namespaces

When defining some of these Styles you would need to include additional namespaces, so that the target types are properly resolved.

Using **PopupViewStyle**, **HeaderStyle** or **FooterStyle** you will need to add the following namespace:

```XAML
xmlns:telerikInput="clr-namespace:Telerik.XamarinForms.Input;assembly=Telerik.XamarinForms.Input"
```

Using **SelectionHighlightStyle**, **TabStripStyle** you need to add the following namespace:

```XAML
xmlns:telerikPrimitives="clr-namespace:Telerik.XamarinForms.Primitives;assembly=Telerik.XamarinForms.Primitives"
```

Using **SpinnerStyle** you need to add the following namespace:

```XAML
xmlns:telerikDatacontrols="clr-namespace:Telerik.XamarinForms.DataControls;assembly=Telerik.XamarinForms.DataControls"
```

## Example

Here is a sample example that shows how the styling properties are applied.

Let's have the following **Time Picker** definition:

<snippet id='timepicker-style' />

And here are how the styles are defined in the page resources.

#### Spinner Style

<snippet id='timepicker-style-spinner-style' />

#### SpinnerHeader Style

<snippet id='timepicker-style-spinner-header-style' />

#### SelectionHighlight Style

<snippet id='timepicker-style-selection-highlight-style' />

#### PlaceholderLabel Style

<snippet id='timepicker-style-placeholder-label-style' />

#### DisplayLabel Style

<snippet id='timepicker-style-display-label-style' />

#### PopupView Style

<snippet id='timepicker-style-popupview-style' />

#### Header Style

<snippet id='timepicker-style-header-style' />

#### HeaderLabel Style

<snippet id='timepicker-style-header-label-style' />

#### Footer Style

<snippet id='timepicker-style-footer-style' />

#### AcceptButton Style

<snippet id='timepicker-style-accept-button-style' />

#### CancelButton Style

<snippet id='timepicker-style-cancel-button-style' />

#### Namespaces

In addition, add the following namespaces:

```XAML
xmlns:telerikInput="clr-namespace:Telerik.XamarinForms.Input;assembly=Telerik.XamarinForms.Input"
xmlns:telerikDataControls="clr-namespace:Telerik.XamarinForms.DataControls;assembly=Telerik.XamarinForms.DataControls"
xmlns:telerikPrimitives="clr-namespace:Telerik.XamarinForms.Primitives;assembly=Telerik.XamarinForms.Primitives"
```

This is how the Time Picker control looks when the styles described above are applied:

![Time Picker](images/timepicker_style.png)

>important A sample Styling example can be found in the TimePicker/Features folder of the [SDK Samples Browser application]({%slug developer-focused-examples%}).

## See Also

- [Key Features]({%slug time-picker-key-features%})
- [Custom Templates]({%slug time-picker-templates%})
- [Commands]({%slug time-picker-commands%})
- [Visual Structure]({%slug time-picker-visual-structure%})
