---
title: Visual Studio でテスト用に UWP コントロールの一意のオートメーション プロパティを設定する
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: ce916f181a6694eabc91cdb7c6a7dec9a8f5e5ac
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>テスト用に UWP コントロールの一意のオートメーション プロパティを設定する

XAML ベースの UWP アプリケーション用のコード化された UI テストを実行する場合は、各コントロールを識別する一意のオートメーション プロパティが必要です。

 アプリケーションで XAML コントロールの種類に基づいて固有のオートメーション プロパティを割り当てることができます。 ここでは、次のような状況において、この一意のオートメーション プロパティを割り当てる方法について説明します。

-   [コントロールの静的な XAML 定義](#UniquePropertyWindowsStoreControlsStaticXAML)

-   [Visual Studio または Blend for Visual Studio を使用して一意のオートメーション プロパティを割り当てる](#UniquePropertyWindowsStoreControlsExpressionBlend)

-   [データ テンプレートを使用する](#UniquePropertyWindowsStoreControlsDataTemplate)

-   [コントロール テンプレートを使用する](#UniquePropertyWindowsStoreControlsControlTemplate)

-   [ダイナミック コントロール](#UniquePropertyWindowsStoreControlsDynamicControls)

## <a name="use-methods-to-assign-a-unique-automation-property"></a>いくつかの方法で一意のオートメーション プロパティを割り当てる

###  <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> 静的な XAML 定義
 XAML ファイルに定義されているコントロールに一意のオートメーション プロパティを指定する目的で、次の例のように、AutomationProperties.AutomationId または AutomationProperties.Name を暗黙的または明示的に設定できます。 これらの値のいずれかを設定すると、コントロールに一意のオートメーション プロパティが割り当てられ、コード化された UI テストまたは操作の記録を作成するとき、コントロールを識別するために使用できます。

 **プロパティを暗黙的に設定する**

コントロールの XAML で Name プロパティを使用して、AutomationProperties.AutomationId を **ButtonX** に設定します。

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

コントロールの XAML で Content プロパティを使用して、AutomationProperties.Name を **ButtonY** に設定します。

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

 **プロパティを明示的に設定する**

 コントロールの XAML で AutomationProperties.AutomationId を **ButtonX** に明示的に設定します。

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

 コントロールの XAML で AutomationProperties.Name を **ButtonY** に明示的に設定します。

```
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

###  <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Visual Studio または Blend for Visual Studio を使用して一意のオートメーション プロパティを割り当てる
 Visual Studio または Blend for Visual Studio を使用し、ボタン、リスト ボックス、コンボ ボックス、テキスト ボックスなど、対話型要素に一意の名前を割り当てることができます。 これにより、コントロールの AutomationProperties.Name に一意の値が割り当てられます。

 **Visual Studio:** **[ツール]** メニューの **[オプション]** をポイントし、**[テキスト エディター]**、**[XAML]**、**[その他]** の順に選択します。

 **[対話要素の作成時に自動的に名前を付ける]** を選択し、**[OK]** をクリックします。

 ![その他の XAML オプション](../test/media/cuit_windowsstoreapp_b.png "CUIT_WindowsStoreApp_B")

 **Blend for Visual Studio:** これを Blend for Visual Studio から実行するには、次のいずれかの方法を使用します。

> [!NOTE]
> この方法は、XAML を使用して静的に作成されたコントロールの場合のみ行うことができます。


 **既存のコントロールに一意の名前を付けるには**

 次に示すように、**[ツール]** メニューの **[対話型要素に名前を付ける]** をクリックします。

 ![[ツール] メニューの [対話型要素に名前を付ける] をクリック](../test/media/cuit_windowsstoreproperty_blend_1.png "CUIT_WindowsStoreProperty_Blend_1")

 **作成されるコントロールに自動的に一意の名前を付けるには**

 **[ツール]** メニューの **[オプション]** をポイントし、**[プロジェクト]** をクリックします。 次に示すように、**[対話要素の作成時に自動的に名前を付ける]** を選択し、**[OK]** をクリックします。

 ![対話型要素に名前を付けるためプロジェクトを設定](../test/media/cuit_windowsstoreproeprty_blend_2.png "CUIT_WindowsStoreProeprty_Blend_2")

###  <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> データ テンプレートを使用する
 ItemTemplate を使用して簡単なテンプレートを定義すると、リスト ボックスの値を変数にバインドできます。次のような XAML を使用します。

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemTemplate>
      <DataTemplate>
         <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding EmployeeName}" />
            <TextBlock Text="{Binding EmployeeID}" />
         </StackPanel>
      </DataTemplate>
   </ListBox.ItemTemplate>
</ListBox>
```

 ItemContainerStyle を含むテンプレートを使用して、値を変数にバインドすることもできます。次のような XAML を使用します。

```xaml
      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
            <ListBox.ItemContainerStyle>
                <Style TargetType="ListBoxItem">
                    <Setter Property="Template">
                        <Setter.Value>
                            <ControlTemplate TargetType="ListBoxItem">
                                <Grid>
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>
                                </Grid>
                            </ControlTemplate>
                        </Setter.Value>
                    </Setter>
                </Style>
            </ListBox.ItemContainerStyle>
        </ListBox>
```

 いずれの例でも、後続のコード例のように、ItemSource の ToString() メソッドをオーバーライドする必要があります。 バインディングによって各データ バインド リスト項目に一意のオートメーション プロパティを設定することはできないため、このコードを使用して、AutomationProperties.Name 値を設定し、その値が確実に一意になるようにします。 この場合、Automation Properties.Name に一意の値を設定するだけで十分です。

> [!NOTE]
> この方法を使用すると、リスト項目の内部コンテンツをバインディングによって Employee クラスの文字列に設定することもできます。 この例に示されているように、各リスト項目内のボタン コントロールには、Employee ID を表す一意のオートメーション ID が割り当てられます。

```csharp
Employee[] employees = new Employee[]
{
   new Employee("john", "4384"),
   new Employee("margaret", "7556"),
   new Employee("richard", "8688"),
   new Employee("george", "1293")
};

listBox1.ItemsSource = employees;

public override string ToString()
{
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name
}
```

###  <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> コントロール テンプレートを使用する

コントロール テンプレートを使用すると、特定の型の各インスタンスがコードで定義されるときに、一意のオートメーション プロパティが与えられるようにすることができます。 AutomationProperty がコントロール インスタンスの一意の ID にバインドされるようにテンプレートを作成します。 次の XAML は、コントロール テンプレートを使用してこのバインディングを作成する方法を示しています。

```xaml
<Style x:Key="MyButton" TargetType="Button">
<Setter Property="Template">
   <Setter.Value>
<ControlTemplate TargetType="Button">
   <Grid>
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>
   </Grid>
</ControlTemplate>
   </Setter.Value>
</Setter>
</Style>
```

 このコントロール テンプレートを使用して 1 つのボタンのインスタンスを 2 つ定義すると、テンプレート内のコントロールのオートメーション ID は一意のコンテンツ文字列に設定されます。このときの XAML を次に示します。

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

###  <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> ダイナミック コントロール
 コードから動的に作成され、静的に、または XAML ファイルのテンプレートから作成されていないコントロールがある場合は、コントロールの Content プロパティまたは Name プロパティを設定する必要があります。 これにより、各ダイナミック コントロールに確実に一意のオートメーション プロパティが与えられるようにします。 たとえば、リスト項目を選択したときに表示するチェック ボックスがある場合は、次に示すようにこれらのプロパティを設定できます。

```csharp
private void CreateCheckBox(string txt, StackPanel panel)
   {
      CheckBox cb = new CheckBox();
      cb.Content = txt; // Sets the AutomationProperties.Name
      cb.Height = 50;
      cb.Width = 100;
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId
      panel.Children.Add(cb);
    }
```

## <a name="see-also"></a>関連項目

- [コード化された UI テストを使用して Windows UWP アプリをテストする](../test/test-windows-store-8-1-apps-with-coded-ui-tests.md)
