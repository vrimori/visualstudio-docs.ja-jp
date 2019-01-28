---
title: スタート ページへの Visual Studio のコマンドの追加 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de713065b61df07a791fa81e89425481227676ea
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006712"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>スタート ページを Visual Studio のコマンドを追加します。
カスタム スタート ページを作成するときに、Visual Studio コマンドを追加できます。 このドキュメントでは、Visual Studio のコマンドを [スタート] ページの XAML オブジェクトにバインドするさまざまな方法について説明します。  
  
 XAML でのコマンドの詳細については、次を参照してください[Commanding の概要。](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="add-commands-from-the-command-well"></a>コマンドからのコマンドを追加します。  
 開始ページで作成[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)追加、<xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>と<xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>名前空間には、次のようにします。  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 アセンブリから Microsoft.VisualStudio.Shell 用の別の名前空間を追加*Microsoft.VisualStudio.Shell.Immutable.11.0.dll*します。 (このアセンブリへの参照をプロジェクトに追加する必要があります)。  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 使用することができます、`vscom:`ページを設定してコントロールの XAML に Visual Studio のコマンドをバインドするエイリアス、<xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>するコントロールのプロパティ`vscom:VSCommands.ExecuteCommand`します。 設定することができますし、<xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>プロパティを次の例に示すように実行するコマンドの名前にします。  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` XAML スキーマを指すのエイリアスがすべてのコマンドの先頭に必要です。  
  
 値を設定することができます、`Command`プロパティからアクセスできる任意のコマンドを**コマンド**ウィンドウ。 使用可能なコマンドの一覧は、次を参照してください。 [Visual Studio コマンドのエイリアス](../ide/reference/visual-studio-command-aliases.md)します。  
  
 追加するコマンドには、追加のパラメーターが必要とする場合の値に追加できます、`CommandParameter`プロパティ。 次の例に示すように、スペースを使用して、コマンドから別のパラメーター。  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="call-extensions-from-the-command-well"></a>コマンドからも拡張機能を呼び出す  
 その他の Visual Studio コマンドの呼び出しに使用する同じ構文を使用して、登録済みの Vspackage からコマンドを呼び出すことができます。 インストール済みの VSPackage に追加する場合など、**ホーム ページ**コマンドを**ビュー**  メニューを設定してそのコマンドを呼び出すことができます`CommandParameter`に`View.HomePage`します。  
  
> [!NOTE]
>  VSPackage に関連付けられているコマンドを呼び出す場合は、コマンドが呼び出されたときにパッケージを読み込む必要があります。  
  
## <a name="add-commands-from-assemblies"></a>アセンブリからのコマンドを追加します。  
 アセンブリの場合、またはメニュー コマンドに関連付けられていない VSPackage でのアクセス コードには、コマンドを呼び出す、アセンブリのエイリアスを作成し、エイリアスを呼び出してください。  
  
### <a name="to-call-a-command-from-an-assembly"></a>アセンブリからコマンドを呼び出す  
  
1.  ソリューションでは、アセンブリへの参照を追加します。  
  
2.  上部にある、 *StartPage.xaml*ファイルをアセンブリの名前空間ディレクティブを追加する次の例に示すようにします。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  設定してコマンドを呼び出す、`Command`次の例に示すように、XAML オブジェクトのプロパティ。  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  アセンブリをコピーして貼り付けます *.\\{Visual Studio インストール フォルダー} \Common7\IDE\PrivateAssemblies\*それを呼び出す前に読み込まれるかどうかを確認します。  
  
## <a name="add-commands-with-the-dte-object"></a>DTE オブジェクトにコマンドを追加します。  
 DTE オブジェクトは、スタート ページ、マークアップとコードの両方からアクセスできます。  
  
 マークアップでは、アクセスできるを使用して、[バインディング マークアップ拡張機能](/dotnet/framework/wpf/advanced/binding-markup-extension)を呼び出す構文、<xref:EnvDTE.DTE>オブジェクト。 このアプローチを使用して単純なプロパティのコレクションを返すようにバインドすることができますが、メソッドやサービスにバインドすることはできません。 次の例は、<xref:System.Windows.Controls.TextBlock>コントロールにバインドする、<xref:EnvDTE._DTE.Name%2A>プロパティと<xref:System.Windows.Controls.ListBox>を列挙するコントロール、<xref:EnvDTE.Window.Caption%2A>によって返されるコレクションのプロパティ、<xref:EnvDTE._DTE.Windows%2A>プロパティ。  
  
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
  
 例については、次を参照してください。[チュートリアル。[スタート] ページのユーザー設定を保存して](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)します。  
  
## <a name="see-also"></a>関連項目  
 [スタート ページにユーザー コントロールを追加します。](../extensibility/adding-user-control-to-the-start-page.md)