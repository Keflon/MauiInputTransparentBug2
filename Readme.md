# Android bug

## InputTransparent adversely affects position or visibility of Labels. 

On Android, setting `IsTransparent` to `True` causes a Label to either never be visible, or to be drawn in the wrong place when `IsVisible` is `False`. 
##
Given the Label:
```xaml
<Label  IsVisible="{Binding IsToggled, Source={x:Reference theSwitch}}"
             InputTransparent="{Binding IsToggled, Source={x:Reference theSwitch1}}"
             Text="(A) Switch is on. InputTransparent is databound."/>
```
- If `IsToggled` is initially `False`, the Label is not drawn at all. 
- When `IsToggled` swaps to `True` the Label becomes visible. 
- **BUG:** When `IsToggled` swaps to `False`, the Label remains visible but is drawn in the wrong place.  


##
Given the Label:
```xaml
<Label IsVisible="{Binding IsToggled, Source={x:Reference theSwitch}}"
            InputTransparent="True"
            Text="(B) Switch is on. InputTransparent is True."/>
```
If `IsToggled` is initially `False`:
- The Label is not drawn at all.
- **BUG:** When `IsToggled` swaps to `True`, the Label does not become visible.



