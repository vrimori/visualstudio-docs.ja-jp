---
title: Visual Studio のコマンドをスタート ページに追加する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87a5e6d29877efb857b846a7b3fac5f19f790d7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Visual Studio のコマンドをスタート ページに追加します。
カスタム スタート ページを作成するときに Visual Studio のコマンドを追加できます。 このドキュメントでは、Visual Studio のコマンドを [スタート] ページの XAML オブジェクトにバインドするさまざまな方法について説明します。  
  
 XAML でのコマンドの詳細については、次を参照してください[コマンド実行の概要。](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="adding-commands-from-the-command-well"></a>コマンドからのコマンドの追加  
 スタート ページで作成[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)追加、<xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>と<xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>名前空間には、次のようにします。  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 アセンブリ Microsoft.VisualStudio.Shell.Immutable.11.0.dll から Microsoft.VisualStudio.Shell の別の名前空間を追加します。 (プロジェクトにこのアセンブリへの参照を追加する必要があります)。  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 使用することができます、 `vscom:` XAML に Visual Studio のコマンドをバインドするエイリアスを設定 ページで制御、<xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>するコントロールのプロパティ`vscom:VSCommands.ExecuteCommand`です。 設定することができますし、<xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>プロパティを実行するには、次の例に示すようにコマンドの名前にします。  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` XAML スキーマを指すのエイリアスがすべてのコマンドの先頭に必要です。  
  
 値を設定することができます、`Command`プロパティからアクセスできる任意のコマンドを**コマンド**ウィンドウです。 使用可能なコマンドの一覧は、次を参照してください。 [Visual Studio コマンドのエイリアス](../ide/reference/visual-studio-command-aliases.md)です。  
  
 コマンドを追加するには、追加のパラメーターが必要とする場合は、値に追加できます、`CommandParameter`プロパティです。 次の例のように、スペースを使用して、コマンドからパラメーターを分割します。  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>コマンドからの拡張機能の呼び出し  
 その他の Visual Studio コマンドの呼び出しに使用する同じ構文を使用して、登録済みの Vspackage からコマンドを呼び出すことができます。 たとえば、インストールされている VSPackage に追加する場合、**ホーム ページ**コマンドを**ビュー**  メニューを設定してそのコマンドを呼び出すことができます`CommandParameter`に`View.HomePage`です。  
  
> [!NOTE]
>  VSPackage に関連付けられているコマンドを呼び出す場合は、コマンドが呼び出されたときにパッケージを読み込む必要があります。  
  
## <a name="adding-commands-from-assemblies"></a>アセンブリからのコマンドの追加  
 アセンブリ、またはアクセス コードは、メニュー コマンドに関連付けられていない、VSPackage にコマンドを呼び出すするにはアセンブリのエイリアスを作成し、エイリアスを呼び出します。  
  
#### <a name="to-call-a-command-from-an-assembly"></a>アセンブリからコマンドを呼び出すには  
  
1.  ソリューションでは、アセンブリへの参照を追加します。  
  
2.  StartPage.xaml ファイルの先頭には、次の例で示すように、アセンブリの名前空間ディレクティブを追加します。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  設定して、コマンドを呼び出し、`Command`次の例で示すように、XAML オブジェクトのプロパティです。  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  アセンブリをコピーおよびに貼り付ける必要があります.\\ *Visual Studio インストール フォルダー*\Common7\IDE\PrivateAssemblies\ を呼び出す前に読み込まれるかどうかを確認します。  
  
## <a name="adding-commands-with-the-dte-object"></a>DTE オブジェクトとコマンドの追加  
 DTE オブジェクトは、スタート ページ、マークアップとコードの両方からアクセスできます。  
  
 マークアップでは、アクセスできるを使用して、[マークアップ拡張機能のバインド](/dotnet/framework/wpf/advanced/binding-markup-extension)を呼び出す構文、<xref:EnvDTE.DTE>オブジェクト。 このアプローチを使用するには、コレクションを返すなどの単純なプロパティにバインドするが、メソッドやサービスにバインドすることはできません。 次の例は、<xref:System.Windows.Controls.TextBlock>コントロールにバインドする、<xref:EnvDTE._DTE.Name%2A>プロパティ、および<xref:System.Windows.Controls.ListBox>を列挙するコントロール、<xref:EnvDTE.Window.Caption%2A>によって返されるコレクションのプロパティ、<xref:EnvDTE._DTE.Windows%2A>プロパティです。  
  
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
  
 例については、次を参照してください。[チュートリアル: スタート ページ上のユーザー設定の保存](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)です。  
  
## <a name="see-also"></a>関連項目  
 [スタート ページへのユーザー コントロールの追加](../extensibility/adding-user-control-to-the-start-page.md)