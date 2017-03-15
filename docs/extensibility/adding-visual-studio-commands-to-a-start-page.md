---
title: "Visual Studio のコマンドをスタート ページに追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c75d9b41d0e51d6db2e78d0afa0e1ddf37e87b8a
ms.lasthandoff: 02/22/2017

---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Visual Studio のコマンドをスタート ページに追加します。
カスタム スタート ページを作成するときに Visual Studio のコマンドを追加できます。 このドキュメントでは、Visual Studio のコマンドを [スタート] ページの XAML オブジェクトにバインドするさまざまな方法について説明します。  
  
 XAML でコマンドの詳細については、次を参照してください[コマンドの実行の概要。](http://msdn.microsoft.com/Library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>コマンドのコマンドを追加します。  
 スタート ページで作成[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)追加、<xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>と<xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>名前空間には、次のようにします</xref:Microsoft.VisualStudio.Shell?displayProperty=fullName></xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>。  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 アセンブリ Microsoft.VisualStudio.Shell.Immutable.11.0.dll から Microsoft.VisualStudio.Shell の別の名前空間を追加します。 (このアセンブリへの参照をプロジェクトに追加する必要があります)。  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 使用することができます、`vscom:`を設定して Visual Studio のコマンドを XAML にバインドするエイリアスのコントロール、ページに、<xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>するコントロールのプロパティ`vscom:VSCommands.ExecuteCommand`</xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>。 設定することができますし、<xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>プロパティを次の例に示すように実行するコマンドの名前にします</xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>。  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` XAML スキーマを指すエイリアスはすべてのコマンドの先頭に必須です。  
  
 値を設定することができます、`Command`プロパティからアクセスできる任意のコマンドを**コマンド**ウィンドウです。 使用可能なコマンドの一覧は、次を参照してください。 [Visual Studio のコマンドのエイリアス](../ide/reference/visual-studio-command-aliases.md)します。  
  
 値に追加するコマンドを追加するには、追加のパラメーターが必要とする場合、`CommandParameter`プロパティです。 次の例のように、スペースを使用して、コマンドからパラメーターを分割します。  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>コマンドからの拡張機能を呼び出す  
 その他の Visual Studio コマンドの呼び出しに使用されるのと同じ構文を使用して、登録されている vspackages コマンドを呼び出すことができます。 たとえば、インストールされている VSPackage を追加した場合、**ホーム ページ**コマンドを**ビュー**  メニューを設定してそのコマンドを呼び出すことができます`CommandParameter`に`View.HomePage`します。  
  
> [!NOTE]
>  VSPackage に関連付けられているコマンドを呼び出す場合は、コマンドが呼び出されたときに、パッケージが読み込ま必要があります。  
  
## <a name="adding-commands-from-assemblies"></a>アセンブリからコマンドを追加します。  
 アセンブリ、またはメニュー コマンドに関連付けられていない VSPackage でのアクセス コードには、コマンドを呼び出す、アセンブリのエイリアスを作成し、エイリアスを呼び出す必要があります。  
  
#### <a name="to-call-a-command-from-an-assembly"></a>アセンブリからコマンドを呼び出すには  
  
1.  ソリューションでは、アセンブリへの参照を追加します。  
  
2.  StartPage.xaml ファイルの先頭には、次の例に示すように、アセンブリの名前空間ディレクティブを追加します。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  設定してコマンドを呼び出す、`Command`次の例で示すように、XAML オブジェクトのプロパティです。  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  アセンブリをコピーし、それを貼り付けて必要があります.\\ *Visual Studio インストール フォルダー*\Common7\IDE\PrivateAssemblies\ を呼び出す前に読み込まれるかどうかを確認します。  
  
## <a name="adding-commands-with-the-dte-object"></a>DTE オブジェクトのコマンドを追加します。  
 DTE オブジェクトは、スタート ページ、マークアップとコードの両方からアクセスできます。  
  
 マークアップでは、アクセスできるを使用して、[バインド マークアップ拡張機能の選択](http://msdn.microsoft.com/Library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63)を呼び出す構文、<xref:EnvDTE.DTE>オブジェクト</xref:EnvDTE.DTE>。 単純なプロパティのコレクションを返すようにバインドするこの方法を使用することができますが、メソッドやサービスにバインドすることはできません。 例を次に、<xref:System.Windows.Controls.TextBlock>にバインドするコントロール、<xref:EnvDTE._DTE.Name%2A>プロパティ、および<xref:System.Windows.Controls.ListBox>を列挙するコントロール、<xref:EnvDTE.Window.Caption%2A>によって返されるコレクションのプロパティ、<xref:EnvDTE._DTE.Windows%2A>プロパティ</xref:EnvDTE._DTE.Windows%2A></xref:EnvDTE.Window.Caption%2A></xref:System.Windows.Controls.ListBox></xref:EnvDTE._DTE.Name%2A></xref:System.Windows.Controls.TextBlock>。  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 例については、次を参照してください。[チュートリアル: [スタート] ページのユーザー設定の保存](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)します。  
  
## <a name="see-also"></a>関連項目  
 [スタート ページにユーザー コントロールを追加します。](../extensibility/adding-user-control-to-the-start-page.md)
