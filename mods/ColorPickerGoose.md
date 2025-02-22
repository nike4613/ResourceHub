# 🙂 Color Picker Goose
Use a color picker to select a color for your goose instead of setting it in the config
Simplifies running multiple nametagged geese.
Shows a Windows color dialog box on launch, like the one used in MS Paint.

## Download
[GooseColorPicker.dll](https://drive.google.com/file/d/1mo6Rre8YCARkxI-6BeiQ5_jYjLIGpNvQ/view)

## Source code
```csharp
 public class ModMain : IMod
    {
        Color gooseColor = Color.FromName("White");
        bool dialogAccepted = false;
        public void Init()
        {
            InjectionPoints.PostModsLoaded += AskForColor;
            InjectionPoints.PreRenderEvent += SetColor;
        }

        private void SetColor(GooseEntity goose, Graphics g)
        {
            if (!dialogAccepted)
                goose.renderData.brushGooseWhite.Color = gooseColor;
        }

        public void AskForColor()
        {
            ColorDialog dialog = new ColorDialog();
            if (dialog.ShowDialog() == DialogResult.OK) {
                gooseColor = dialog.Color;
                dialogAccepted = true;
            }
            
        }

    }
```

{% include install_guide.md modname="ColorPickerGoose" iszip=false %}
