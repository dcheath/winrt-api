---
-api-id: T:Windows.UI.Xaml.Controls.TextBox
-api-type: winrt class
---

<!-- Class syntax.
public class TextBox : Windows.UI.Xaml.Controls.Control, Windows.UI.Xaml.Controls.ITextBox, Windows.UI.Xaml.Controls.ITextBox2, Windows.UI.Xaml.Controls.ITextBox3, Windows.UI.Xaml.Controls.ITextBox4, Windows.UI.Xaml.Controls.ITextBox5
-->

# Windows.UI.Xaml.Controls.TextBox

## -description

Represents a control that can be used to display and edit plain text (single or multi-line).

## -xaml-syntax

```xaml
<TextBox .../>
```

## -remarks

<img alt="Text box control" src="images/controls/TextBox.png" />

The [TextBox](textbox.md) control enables a user to type text into an app. It's typically used to capture a single line of text, but can be configured to capture multiple lines of text. The text displays on the screen in a simple uniform plaintext format.

[TextBox](textbox.md) has a number of features that can simplify text entry. It comes with a familiar, built-in context menu with support for copying and pasting text. The "clear all" button lets a user quickly delete all text that has been entered. It also has spell checking capabilities built in and enabled by default.

Here's how to create a [TextBox](textbox.md) in XAML and in code.

```xaml
<TextBox Width="500" Header="Notes" PlaceholderText="Type your notes here"/>
```

```csharp
TextBox textBox = new TextBox();
textBox.Width = 500;
textBox.Header = "Notes";
textBox.PlaceholderText = "Type your notes here";
// Add the TextBox to the visual tree.
rootGrid.Children.Add(textBox);
```

The resulting [TextBox](textbox.md) looks like this. The blue border indicates that the [TextBox](textbox.md) has focus.

<img src="images/TextBox_Ex1.png" alt="A simple text box" />### Is TextBox the right control to use?
You can use a [TextBox](textbox.md) control to display and edit unformatted text. If you need an editable text box that accepts passwords or other sensitive input, see [PasswordBox](passwordbox.md). If you need a text box to enter search terms, see [AutoSuggestBox](autosuggestbox.md). If you need to enter or edit formatted text, see [RichEditBox](richeditbox.md).

### Use TextBox for data input in a form

It’s common to use a [TextBox](textbox.md) to accept data input on a form, and use the [Text](textbox_text.md) property to get the complete text string from the [TextBox](textbox.md). You typically use an event like a submit button Click to access the [Text](textbox_text.md) property, but you can handle the [TextChanged](textbox_textchanged.md) or [TextChanging](textbox_textchanging.md) event if you need to do something when the text changes. You can add a [Header](textbox_header.md) (or label) and [PlaceholderText](textbox_placeholdertext.md) (or watermark) to the [TextBox](textbox.md) to give the user an indication of what the [TextBox](textbox.md) is for. To customize the look of the header, you can set the [HeaderTemplate](textbox_headertemplate.md) property instead of [Header](textbox_header.md). For design info, see [Guidelines for labels](http://msdn.microsoft.com/library/cfacccd4-749f-43fb-947e-2591ae673804).

You can restrict the number of characters the user can type by setting the [MaxLength](textbox_maxlength.md) property. However, [MaxLength](textbox_maxlength.md) does not restrict the length of pasted text. Use the [Paste](textbox_paste.md) event to modify pasted text if this is important for your app.

[TextBox](textbox.md) includes a *clear all* button ("x") that appears when text is entered in the box. When a user clicks the "x", the text in the [TextBox](textbox.md) is cleared. It looks like this.

<img src="images/TextBox_ClearAll.png" alt="A text box with a clear all button" />
The *clear all* button is shown only for editable, single-line text boxes that contain text and have focus. 
The *clear all* button is not shown in any of these cases:

+ [IsReadOnly](textbox_isreadonly.md) is **true**
+ [AcceptsReturn](textbox_acceptsreturn.md) is **true**
+ [TextWrapping](textbox_textwrapping.md) is **Wrap**


### Make a TextBox read-only

You can make a [TextBox](textbox.md) read-only by setting the [IsReadOnly](textbox_isreadonly.md) property to **true**. For example, you might have a [TextBox](textbox.md) for a user to enter comments that is enabled only under certain conditions. You can make the [TextBox](textbox.md) read-only until the conditions are met. If you need only to display text, consider using a [TextBlock](textblock.md) or [RichTextBlock](richtextblock.md) instead.

### Enable multi-line input

There are two properties that control whether the [TextBox](textbox.md) displays text on more than one line. 
+ To let the text box allow and display the newline or return characters, set the [AcceptsReturn](textbox_acceptsreturn.md) property to **true**.
+ To enable text wrapping, set the [TextWrapping](textbox_textwrapping.md) property to **Wrap**. ([TextBox](textbox.md) doesn't support the **TextWrapping.WrapWholeWords** enumeration value.)
 A multi-line [TextBox](textbox.md) will continue to grow vertically as text is entered unless it’s constrained by its [Height](../windows.ui.xaml/frameworkelement_height.md) or [MaxHeight](../windows.ui.xaml/frameworkelement_maxheight.md) property, or by a parent container. You should test that a multi-line [TextBox](textbox.md) doesn’t grow beyond its visible area, and constrain its growth if it does. Scrolling using a scroll-wheel or touch is automatically enabled when needed. However, vertical scrollbars are not shown by default. You can show the vertical scrollbars by setting the [ScrollViewer.VerticalScrollBarVisibility](scrollviewer_verticalscrollbarvisibility.md) to **Auto** on the embedded [ScrollViewer](scrollviewer.md), as shown here.

```xaml
<TextBox AcceptsReturn="True" TextWrapping="Wrap" 
         MaxHeight="172" Width="300" Header="Description"
         ScrollViewer.VerticalScrollBarVisibility="Auto"/>
```

```csharp
TextBox textBox = new TextBox();
textBox.AcceptsReturn = true;
textBox.TextWrapping = TextWrapping.Wrap;
textBox.MaxHeight = 172;
textBox.Width = 300;
textBox.Header = "Description";
ScrollViewer.SetVerticalScrollBarVisibility(textBox, ScrollBarVisibility.Auto);
```

Here's what the [TextBox](textbox.md) looks like after text is added.

<img src="images/TextBox_MultiLine.png" alt="A mullti line text box" />

### Format the text display

Use the [TextAlignment](textbox_textalignment.md) property to align text within a [TextBox](textbox.md). To align the [TextBox](textbox.md) within the layout of the page, use the [HorizontalAlignment](../windows.ui.xaml/frameworkelement_horizontalalignment.md) and [VerticalAlignment](../windows.ui.xaml/frameworkelement_verticalalignment.md) properties.

While the [TextBox](textbox.md) supports only unformatted text, you can customize how the text is displayed in the [TextBox](textbox.md) to match your branding. You can set standard [Control](control.md) properties like [FontFamily](control_fontfamily.md), [FontSize](control_fontsize.md), [FontStyle](control_fontstyle.md), [Background](control_background.md), [Foreground](control_foreground.md), and [CharacterSpacing](control_characterspacing.md) to change the look of the text. These properties affect only how the [TextBox](textbox.md) displays the text locally, so if you were to copy and paste the text into a rich text control, for example, no formatting would be applied.

This example shows a read-only [TextBox](textbox.md) with several properties set to customize the appearance of the text.

```xaml
<TextBox Text="Sample Text" IsReadOnly="True" 
         FontFamily="Verdana" FontSize="24"
         FontWeight="Bold" FontStyle="Italic" 
         CharacterSpacing="200" Width="300"
         Foreground="Blue" Background="Beige"/>
```

```csharp
TextBox textBox = new TextBox();
textBox.Text = "Sample Text";
textBox.IsReadOnly = true;
textBox.FontFamily = new FontFamily("Verdana");
textBox.FontSize = 24;
textBox.FontWeight = Windows.UI.Text.FontWeights.Bold;
textBox.FontStyle = Windows.UI.Text.FontStyle.Italic;
textBox.CharacterSpacing = 200;
textBox.Width = 300;
textBox.Background = new SolidColorBrush(Windows.UI.Colors.Beige);
textBox.Foreground = new SolidColorBrush(Windows.UI.Colors.Blue);
// Add the TextBox to the visual tree.
rootGrid.Children.Add(textBox);
```

The resulting [TextBox](textbox.md) looks like this.

<img src="images/TextBox_Formatted.png" alt="A simple text box" />

### Modify the context menu

By default, the commands shown in the [TextBox](textbox.md) context menu depend on the state of the [TextBox](textbox.md). For example, the following commands can be shown when the [TextBox](textbox.md) is editable.<table>
   <tr><th>Command</th><th>Shown when...</th></tr>
   <tr><td>Copy</td><td>text is selected.</td></tr>
   <tr><td>Cut</td><td>text is selected.</td></tr>
   <tr><td>Paste</td><td>the clipboard contains text.</td></tr>
   <tr><td>Select all</td><td>the [TextBox](textbox.md) contains text.</td></tr>
   <tr><td>Undo</td><td>text has been changed.</td></tr>
</table>

To modify the commands shown in the context menu, handle the [ContextMenuOpening](textbox_contextmenuopening.md) event. For an example of this, see Scenario 2 of the [ContextMenu sample](http://go.microsoft.com/fwlink/p/?linkid=234891). For design info, see [Guidelines for context menus](http://msdn.microsoft.com/library/23063edd-ed89-4a82-9857-44001fad770b).

### Selection, copy, and paste

You can get or set the selected text in a [TextBox](textbox.md) using the [SelectedText](textbox_selectedtext.md) property. Use the [SelectionStart](textbox_selectionstart.md) and [SelectionLength](textbox_selectionlength.md) properties, and the [Select](textbox_select.md) and [SelectAll](textbox_selectall.md) methods, to manipulate the text selection. Handle the [SelectionChanged](textbox_selectionchanged.md) event to do something when the user selects or de-selects text. You can change the color used to highlight the selected text by setting the [SelectionHighlightColor](textbox_selectionhighlightcolor.md) property.

[TextBox](textbox.md) supports copy and paste by default. You can provide custom handling of the [Paste](textbox_paste.md) event on editable text controls in your app. For example, you might remove the line breaks from a multi-line address when pasting it into a single-line search box. Or, you might check the length of the pasted text and warn the user if it exceeds the maximum length that can be saved to a database. For more info and examples, see the [Paste](textbox_paste.md) event.

### Use a text box with the touch keyboard

The touch keyboard can be used for text entry when your app runs on a device with a touch screen. [TextBox](textbox.md) provides properties you can set to make it much faster and easier for users to enter data in your app using the touch keyboard. Set the [InputScope](textbox_inputscope.md) property to match the kind of data the user is expected to enter. For example, if a [TextBox](textbox.md) is used only to enter a 4-digit PIN, set the [InputScope](textbox_inputscope.md) property to Number. This tells the system to show the number keypad layout, which makes it easier for the user to enter the PIN.

Other properties that affect the touch keyboard are [IsSpellCheckEnabled](textbox_isspellcheckenabledproperty.md), [IsTextPredictionEnabled](textbox_istextpredictionenabledproperty.md), and [PreventKeyboardDisplayOnProgrammaticFocus](textbox_preventkeyboarddisplayonprogrammaticfocus.md). ([IsSpellCheckEnabled](textbox_isspellcheckenabledproperty.md) also affects the [TextBox](textbox.md) when a hardware keyboard is used.) For more info and examples, see [Use input scope to change the touch keyboard](http://msdn.microsoft.com/library/6e5f55d7-24d6-47cc-b457-b6231ede2a71), and the property documentation.

### Control style and template

You can modify the default [Style](../windows.ui.xaml/style.md) and [ControlTemplate](controltemplate.md) to give the control a unique appearance. For information about modifying a control's style and template, see [Styling controls](https://msdn.microsoft.com/windows/uwp/controls-and-patterns/styling-controls). The default style, template, and resources that define the look of the control are included in the generic.xaml file. For design purposes, generic.xaml is available in the \(Program Files)\Windows Kits\10\DesignTime\CommonConfiguration\Neutral\UAP\&lt;SDK version&gt;\Generic folder from a Windows Software Development Kit (SDK) installation. Styles and resources from different versions of the SDK might have different values.

Starting in Windows 10, version 1607 (Windows Software Development Kit (SDK) version 10.0.14393.0), generic.xaml includes resources that you can use to modify the colors of a control in different visual states without modifying the control template. In apps that target this software development kit (SDK) or later, modifying these resources is preferred to setting properties such as [Background](control_background.md) and [Foreground](control_foreground.md). For more info, see the [Light-weight styling](https://msdn.microsoft.com/windows/uwp/controls-and-patterns/styling-controls) section of the [Styling controls](https://msdn.microsoft.com/windows/uwp/controls-and-patterns/styling-controls) article.

This table shows the resources used by the [TextBox](textbox.md) control. Resources that start with "TextControl" are shared by [TextBox](textbox.md), [PasswordBox](passwordbox.md), [RichEditBox](richeditbox.md), and [AutoSuggestBox](autosuggestbox.md).

<table>
   <tr><th>Resource key</th><th>Description</th></tr>
   <tr><td>TextControlForeground</td><td>Text color at rest and not focused</td></tr>
   <tr><td>TextControlForegroundPointerOver</td><td>Text color on hover</td></tr>
   <tr><td>TextControlForegroundFocused</td><td>Text color when focused</td></tr>
   <tr><td>TextControlForegroundDisabled</td><td>Text color when disabled</td></tr>
   <tr><td>TextControlBackground</td><td>Background color at rest and not focused</td></tr>
   <tr><td>TextControlBackgroundPointerOver</td><td>Background color on hover</td></tr>
   <tr><td>TextControlBackgroundFocused</td><td>Background color when focused</td></tr>
   <tr><td>TextControlBackgroundDisabled</td><td>Background color when disabled</td></tr>
   <tr><td>TextControlBorderBrush</td><td>Border color at rest and not focused</td></tr>
   <tr><td>TextControlBorderBrushPointerOver</td><td>Border color on hover</td></tr>
   <tr><td>TextControlBorderBrushFocused</td><td>Border color when focused</td></tr>
   <tr><td>TextControlBorderBrushDisabled</td><td>Border color when disabled</td></tr>
   <tr><td>TextControlPlaceholderForeground</td><td>Placeholder text color at rest and not focused</td></tr>
   <tr><td>TextControlPlaceholderForegroundPointerOver</td><td>Placeholder text color on hover</td></tr>
   <tr><td>TextControlPlaceholderForegroundFocused</td><td>Placeholder text color when focused</td></tr>
   <tr><td>TextControlPlaceholderForegroundDisabled</td><td>Placeholder text color when disabled</td></tr>
   <tr><td>TextControlHeaderForeground</td><td>Header text color</td></tr>
   <tr><td>TextControlHeaderForegroundDisabled</td><td>Header text color when disabled</td></tr>
   <tr><td>TextControlSelectionHighlightColor</td><td>Highlight color of selected text</td></tr>
   <tr><td>TextControlButtonBackground</td><td>Background color of delete button at rest</td></tr>
   <tr><td>TextControlButtonBackgroundPointerOver</td><td>Background color of delete button on hover</td></tr>
   <tr><td>TextControlButtonBackgroundPressed</td><td>Background color of delete button when pressed</td></tr>
   <tr><td>TextControlButtonBorderBrush</td><td>Border color of delete button at rest</td></tr>
   <tr><td>TextControlButtonBorderBrushPointerOver</td><td>Border color of delete button on hover</td></tr>
   <tr><td>TextControlButtonBorderBrushPressed</td><td>Border color of delete button when pressed</td></tr>
   <tr><td>TextControlButtonForeground</td><td>Foreground color of delete button at rest</td></tr>
   <tr><td>TextControlButtonForegroundPointerOver</td><td>Foreground color of delete button on hover</td></tr>
   <tr><td>TextControlButtonForegroundPressed</td><td>Foreground color of delete button when pressed</td></tr>
</table>

## -examples

<table>
<th align="left">XAML Controls Gallery<th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p>If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/TextBox">open the app and see the TextBox in action</a>.</p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT">Get the XAML Controls Gallery app (Microsoft Store)</a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics">Get the source code (GitHub)</a></li>
    </ul>
</td>
</tr>
</table>

This example shows a [TextBox](textbox.md) with a header and placeholder text. The [Text](textbox_text.md) from the [TextBox](textbox.md) is used to show a greeting to the user.

```xaml
<StackPanel>
    <TextBlock Text="What's your name?"/>
        <StackPanel Orientation="Horizontal" Margin="0,20,0,20">

            <TextBox x:Name="nameInput"
                     Header="Enter your name:" PlaceholderText="Name"
                     Width="300" HorizontalAlignment="Left"/>

            <Button Content="Hello button" Click="Button_Click"/>
        </StackPanel>
    <TextBlock x:Name="greetingOutput"/>
</StackPanel>
```

```csharp
private void Button_Click(object sender, RoutedEventArgs e)
{
    greetingOutput.Text = "Hello, " + nameInput.Text + "!";
}
```



## -see-also
[Control](control.md), [Guidelines for text input](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/text-box), [TextBox styles and templates](http://msdn.microsoft.com/library/fb929d6f-b605-41e0-8a1d-98eb55fbedc0), [How to use input scope to change the touch keyboard](http://msdn.microsoft.com/library/6e5f55d7-24d6-47cc-b457-b6231ede2a71), [XAML text editing sample](http://go.microsoft.com/fwlink/p/?linkid=251417), [Guidelines for spell checking](http://msdn.microsoft.com/library/b867c956-5ab2-4207-a8de-179ce7871180), [PasswordBox](passwordbox.md), [RichEditBox](richeditbox.md), [RichTextBlock](richtextblock.md), [SearchBox](searchbox.md), [Controls list](http://msdn.microsoft.com/library/11172840-a63d-4f48-9db4-7baca06308ee), [Controls by function](http://msdn.microsoft.com/library/8db4347b-91d6-4659-91f2-80ecf7bbb596), [Touch keyboard text input sample (Windows 10)](http://go.microsoft.com/fwlink/p/?LinkId=690716)
