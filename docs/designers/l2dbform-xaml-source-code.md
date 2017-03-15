---
title: "L2DBForm.xaml ソース コード | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b62eac5ab4b057e26ed4a0a34551655984449cf1
ms.lasthandoff: 02/22/2017

---
# <a name="l2dbformxaml-source-code"></a>L2DBForm.xaml ソース コード
このトピックでは、「[LINQ to XML を使用した WPF のデータ バインドの例](../designers/wpf-data-binding-using-linq-to-xml-example.md)」の XAML ソース ファイル L2DBForm.xaml の内容を紹介し、説明します。  
  
## <a name="overall-ui-structure"></a>UI の全体的な構造  
 WPF プロジェクトで一般に見られるように、このファイルには親要素として <xref:System.Windows.Window> XML 要素が含まれており、この要素に `LinqToXmlDataBinding` 名前空間の派生クラス `L2XDBFrom` が関連付けられています。  
  
 クライアント領域は、明るい青色の背景の <xref:System.Windows.Controls.StackPanel> 内に表示されます。 このパネルには、4 つの <xref:System.Windows.Controls.DockPanel> UI セクションが <xref:System.Windows.Controls.Separator> バーで区切られて含まれています。 これらのセクションの目的については、[前のトピック](../designers/walkthrough-linqtoxmldatabinding-example.md)の「**解説**」で説明されています。  
  
 各セクションには、それぞれを識別するラベルが含まれています。 最初の 2 つのセクションでは、<xref:System.Windows.FrameworkElement.LayoutTransform%2A> を使用してこのラベルは 90 度回転されています。 セクションの残りの部分には、そのセクションの目的に適したテキスト ブロック、テキスト ボックス、ボタンなどの UI 要素が含まれています。 これらの子のコントロールを配置するために子の <xref:System.Windows.Controls.StackPanel> が使用されることがあります。  
  
## <a name="window-resource-section"></a>ウィンドウ リソース セクション  
 9 行目の `<Window.Resources>` 開始タグは、ウィンドウ リソース セクションの開始を示します。 このセクションは、35 行目の終了タグで終了します。  
  
 `<ObjectDataProvider>` タグ (11 ～ 25 行目) では、`LoadedBooks` という <xref:System.Windows.Data.ObjectDataProvider> を宣言しています。これはソースとして <xref:System.Xml.Linq.XElement> を使用します。 この <xref:System.Xml.Linq.XElement> は、埋め込みの XML ドキュメント (`CDATA` 要素) を解析して初期化されます。 組み込み XML ドキュメントの宣言時および解析時に、空白が保持されることに注意してください。 これは、生の XML の表示に使用されている <xref:System.Windows.Controls.TextBlock> コントロールに、XML の書式を設定する機能がないためです。  
  
 最後に、`BookTemplate` という <xref:System.Windows.DataTemplate> が 28 ～ 34 行目で宣言されます。 このテンプレートは、[Book List] UI セクションにエントリを表示するために使用されます。 **** ここでは、データ バインドおよび LINQ to XML の動的プロパティを使用し、次の代入を通じて書籍の ID と名前を取得します。  
  
```  
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"  
```  
  
## <a name="data-binding-code"></a>データ バインド コード  
 このファイルでは、<xref:System.Windows.DataTemplate> 要素に加えて、データ バインドが各所で使用されています。  
  
 38 行目の始まりの `<StackPanel>` タグで、このパネルの <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティは `LoadedBooks` データ プロバイダーに設定されています。  
  
```  
DataContext="{Binding Source={StaticResource LoadedBooks}}  
```  
  
 これにより、このデータ プロバイダーの `Xml` プロパティにバインドして、`tbRawXml` という名前の <xref:System.Windows.Controls.TextBlock> に生の XML を表示できるようになります (46 行目)。  
  
```  
Text="{Binding Path=Xml}"   
```  
  
 58 ～ 62 行目では、**[Book List]** UI セクションの <xref:System.Windows.Controls.ListBox> が、その表示アイテムのテンプレートをウィンドウ リソース セクションで定義された `BookTemplate` に設定しています。  
  
```  
ItemTemplate ="{StaticResource BookTemplate}"   
```  
  
 59 ～ 62 行目では、書籍の実際の値がこのリスト ボックスにバインドされています。  
  
```  
<ListBox.ItemsSource>  
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
</ListBox.ItemsSource>  
```  
  
 3 つ目の UI セクションの **[Edit Selected Book]** は、まず親 <xref:System.Windows.Controls.StackPanel> の <xref:System.Windows.FrameworkElement.DataContext%2A> を **[Book List]** UI セクション (82 行目) の現在選択されているアイテムにバインドします。  
  
```  
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"  
```  
  
 次に、双方向データ バインドを使用して、書籍要素の現在の値がこのパネルの&2; つのテキスト ボックスに表示され、そこで更新されるようにしています。 動的プロパティへのデータ バインドは、 `BookTemplate` データ テンプレートで使用されているデータ バインドと似ています。  
  
```  
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"  
```  
  
 最後の UI セクション [Add New Book] では、XAML コード内でデータ バインドが使用されていません。代わりに、データ バインドに類似したコードが L2DBForm.xaml.cs ファイルのイベント処理コードに記述されています。 ****  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
  
> [!NOTE]
>  行番号を追跡しやすいように、次のコードを Visual Studio の C# ソース コード エディターなどのコード エディターにコピーすることをお勧めします。  
  
### <a name="code"></a>コード  
  
```xml  
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:system="clr-namespace:System;assembly=mscorlib"  
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"  
    xmlns:local="clr-namespace:LinqToXmlDataBinding"  
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">  
  
    <Window.Resources>  
        <!-- Books provider and inline data -->  
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">  
            <ObjectDataProvider.MethodParameters>  
                <system:String xml:space="preserve">  
<![CDATA[  
<books xmlns="http://www.mybooks.com">  
  <book id="0">book zero</book>  
  <book id="1">book one</book>  
  <book id="2">book two</book>  
  <book id="3">book three</book>  
</books>  
]]>                  
                </system:String>  
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>  
            </ObjectDataProvider.MethodParameters>  
        </ObjectDataProvider>  
  
        <!-- Template for use in Books List listbox. -->  
        <DataTemplate x:Key="BookTemplate">  
            <StackPanel Orientation="Horizontal">  
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>  
                <TextBlock Margin="3" Text="-"/>  
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>  
            </StackPanel>  
        </DataTemplate>  
    </Window.Resources>  
  
    <!-- Main visual content container -->  
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">  
        <!-- Raw XML display section -->  
        <DockPanel Margin="5">  
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML  
            <Label.LayoutTransform>  
                <RotateTransform Angle="90"/>  
            </Label.LayoutTransform>  
            </Label>  
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- List box to display all books section -->  
        <DockPanel Margin="5">  
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List  
                <Label.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </Label.LayoutTransform>  
            </Label>  
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">  
                <ListBox.ItemsSource>  
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
                </ListBox.ItemsSource>  
            </ListBox>  
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">      
            <Button.LayoutTransform>  
                <RotateTransform Angle="90"/>  
            </Button.LayoutTransform>  
            </Button>  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- Edit current selection section -->  
        <DockPanel Margin="5">  
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">  
                    Changes are live!  
                <TextBlock.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </TextBlock.LayoutTransform>  
            </TextBlock>  
            <StackPanel>  
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>      
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">ID:</Label>  
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Edit the selected book ID and see it changed.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">Value:</Label>  
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Edit the selected book Value and see it changed.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                </StackPanel>  
            </StackPanel>  
        </DockPanel>  
  
        <Separator Height="4" Margin="5" />  
  
        <!-- Add new book section -->  
        <DockPanel Margin="5">  
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book  
                <Button.LayoutTransform>  
                    <RotateTransform Angle="90"/>  
                </Button.LayoutTransform>  
            </Button>  
            <StackPanel>  
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>  
                <StackPanel Margin="1">  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">ID:</Label>  
                        <TextBox Name="tbAddID" Width="410">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="Bold" TextAlignment="Center">  
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                    <StackPanel Orientation="Horizontal">  
                        <Label Width="40">Value:</Label>  
                        <TextBox Name="tbAddValue" Width="410" Height="25">  
                            <TextBox.ToolTip>  
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">  
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>  
                                </TextBlock>  
                            </TextBox.ToolTip>  
                        </TextBox>  
                    </StackPanel>  
                </StackPanel>  
            </StackPanel>  
        </DockPanel>  
    </StackPanel>  
</Window>  
  
```  
  
### <a name="comments"></a>コメント  
 WPF UI 要素に関連付けられているイベント ハンドラーの C# ソース コードについては、「[L2DBForm.xaml.cs ソース コード](../designers/l2dbform-xaml-cs-source-code.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: LinqToXmlDataBinding の例](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [L2DBForm.xaml.cs ソース コード](../designers/l2dbform-xaml-cs-source-code.md)
