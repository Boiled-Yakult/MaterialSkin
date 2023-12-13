# MaterialSkin 2 for .NET WinForms

Theming .NET WinForms, C# or VB.Net, to Google's Material Design Principles.

> 嵌入 HarmonyOS Sans - [HarmonyOS Sans 字体](https://developer.huawei.com/consumer/cn/design/resource/) 替换思源黑体

> ~~嵌入 Source Han Sans - [思源黑体中文字体](https://github.com/adobe-fonts/source-han-sans)替换原生字体~~

## Preview!

更改字体后的 MaterialSkin 组件简单演示：

![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/345a639b-4692-4c7b-b9f9-dd713094267c)

*The MaterialSkin Drawer (menu).*

![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/bdf7afd0-c853-42a5-94a8-0ea9e0ea3794)

*Every MaterialSkin button variant - this is 1 control, 3 properties*

![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/cb4d9232-8f1c-4efe-9dfe-ace4aa81d5fd)

*The MaterialSkin checkboxes, radio and Switch.*

![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/8667fb30-2b5f-4d92-933a-f9f8798d4615)

*Material skin textfield*

![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/a06ae714-3aee-431a-b8ea-e47b4cd54da4)

*Table control*

![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/41b3cc75-1ced-4833-ab47-c4d39affe3da)

*Progress bar*

![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/030b0483-a553-463e-a85c-93adbd39cf7c)

*Cards*
![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/aaeda08d-84f3-49fa-9baa-1719dc3b2336)

*List Box*

![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/527de055-3574-44a4-8355-87e67ab6b367)

*Expansion Panel*

![expansion](https://user-images.githubusercontent.com/77468294/119881153-419a5900-bf2d-11eb-95a2-ab29089acdd3.png)

*Label*

![image](https://github.com/kanoakliu/MaterialSkin/assets/73887119/ac734d63-4917-4edb-9ef4-e372d49507bb)

---

## Current state of the MaterialSkin components

| Component                    | Supported | Disabled mode | Animated |
| ---------------------------- | :-------: | :-----------: | :------: |
| Backdrop                     |  **No**   |       -       |    -     |
| Banner                       |  **No**   |       -       |    -     |
| Buttons                      |    Yes    |      Yes      |   Yes    |
| Cards                        |    Yes    |      N/A      |   N/A    |
| Check Box                    |    Yes    |      Yes      |   Yes    |
| Check Box List               |    Yes    |      Yes      |   Yes    |
| Chips                        |  **No**   |       -       |    -     |
| Combobox                     |    Yes    |      Yes      |   Yes    |
| Context Menu                 |    Yes    |      Yes      |   Yes    |
| Date Picker                  |  **No**   |       -       |    -     |
| Dialog                       |    Yes    |      N/A      |  **No**  |
| Divider                      |    Yes    |      N/A      |   N/A    |
| Drawer                       |    Yes    |      N/A      |   Yes    |
| Expansion Panel              |    Yes    |      Yes      |  **No**  |
| Flexible Dialog (big)        |    Yes    |      Yes      |   N/A    |
| FAB - Floating Action Button |    Yes    |      Yes      |   Yes    |
| Label                        |    Yes    |      Yes      |   N/A    |
| ListBox                      |    Yes    |      Yes      |   N/A    |
| ListView                     |    Yes    |    **No**     |   N/A    |
| Progress Bar                 |  _Partial_  |    **No**     |  **No**  |
| Radio Button                 |    Yes    |      Yes      |   Yes    |
| Text field                   |    Yes    |      Yes      |   Yes    |
| Sliders                      |    Yes    |      Yes      |  **No**  |
| SnackBar                     |    Yes    |      N/A      |   Yes    |
| Switch                       |    Yes    |      Yes      |   Yes    |
| Tabs                         |    Yes    |      N/A      |   Yes    |
| Time Picker                  |  **No**   |       -       |    -     |
| Tooltips                     |  **No**   |       -       |    -     |

All supported components have a dark theme

## Implementing MaterialSkin 2 in your application

### 1. Add the library to your project

There are a few methods to add this lib:

#### Manual way

Download the precompiled DLL available on the releases section and add it as a external reference on your project.

#### Compile from the latest master

Clone the project from GitHub, then add the MaterialSkin.csproj to your own solution, then add it as a project reference on your project.

### 2. Add the MaterialSkin components to your ToolBox

Simply drag the MaterialSkin.dll file into your IDE's ToolBox and all the controls should be added there.

### 3. Inherit from MaterialForm

Open the code behind your Form you wish to skin. Make it inherit from MaterialForm rather than Form. Don't forget to put the library in your imports, so it can find the MaterialForm class!

#### C# (Form1.cs)

```cs
public partial class Form1 : MaterialForm
```

#### VB.NET (Form1.Designer.vb)

```vb
Partial Class Form1
  Inherits MaterialSkin.Controls.MaterialForm
```

### 4. Initialize your colorscheme

Set your preferred colors & theme. Also add the form to the manager so it keeps updated if the color scheme or theme changes later on.

#### C# (Form1.cs)

```cs
public Form1()
{
    InitializeComponent();

    var materialSkinManager = MaterialSkinManager.Instance;
    materialSkinManager.AddFormToManage(this);
    materialSkinManager.Theme = MaterialSkinManager.Themes.LIGHT;
    materialSkinManager.ColorScheme = new ColorScheme(Primary.BlueGrey800, Primary.BlueGrey900, Primary.BlueGrey500, Accent.LightBlue200, TextShade.WHITE);
}
```

#### VB.NET (Form1.vb)

```vb
Imports MaterialSkin

Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        Dim SkinManager As MaterialSkinManager = MaterialSkinManager.Instance
        SkinManager.AddFormToManage(Me)
        SkinManager.Theme = MaterialSkinManager.Themes.LIGHT
        SkinManager.ColorScheme = New ColorScheme(Primary.BlueGrey800, Primary.BlueGrey900, Primary.BlueGrey500, Accent.LightBlue200, TextShade.WHITE)
    End Sub
End Class
```
