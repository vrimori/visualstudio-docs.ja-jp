---
title: スタート ページへの Visual Studio のコマンドの追加 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8a301357765f85d80afb71985d51044227204997
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256244"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Visual Studio コマンドのスタート ページへの追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

カスタム スタート ページを作成するときに、Visual Studio コマンドを追加できます。 このドキュメントでは、Visual Studio のコマンドを [スタート] ページの XAML オブジェクトにバインドするさまざまな方法について説明します。  
  
 XAML でのコマンドの詳細については、次を参照してください[コマンド実行の概要。](http://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>コマンドからコマンドを追加します。  
 スタート ページで作成[カスタム スタート ページを作成する](../extensibility/creating-a-custom-start-page.md)追加、<xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>と<xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>名前空間には、次のようにします。  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 アセンブリ Microsoft.VisualStudio.Shell.Immutable.11.0.dll から Microsoft.VisualStudio.Shell の別の名前空間を追加します。 (このアセンブリへの参照をプロジェクトに追加する必要があります)。  
  
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
  
 値を設定することができます、`Command`プロパティからアクセスできる任意のコマンドを**コマンド**ウィンドウ。 使用可能なコマンドの一覧は、次を参照してください。 [Visual Studio Command Aliases](../ide/reference/visual-studio-command-aliases.md)します。  
  
 追加するコマンドには、追加のパラメーターが必要とする場合の値に追加できます、`CommandParameter`プロパティ。 次の例に示すように、スペースを使用して、コマンドから別のパラメーター。  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>コマンドからも拡張機能を呼び出す  
 その他の Visual Studio コマンドの呼び出しに使用する同じ構文を使用して、登録済みの Vspackage からコマンドを呼び出すことができます。 インストール済みの VSPackage に追加する場合など、**ホーム ページ**コマンドを**ビュー**  メニューを設定してそのコマンドを呼び出すことができます`CommandParameter`に`View.HomePage`します。  
  
> [!NOTE]
>  VSPackage に関連付けられているコマンドを呼び出す場合は、コマンドが呼び出されたときにパッケージを読み込む必要があります。  
  
## <a name="adding-commands-from-assemblies"></a>アセンブリからのコマンドの追加  
 アセンブリの場合、またはメニュー コマンドに関連付けられていない VSPackage でのアクセス コードには、コマンドを呼び出す、アセンブリのエイリアスを作成し、エイリアスを呼び出してください。  
  
#### <a name="to-call-a-command-from-an-assembly"></a>アセンブリからコマンドを呼び出す  
  
1.  ソリューションでは、アセンブリへの参照を追加します。  
  
2.  StartPage.xaml ファイルの上部にある次の例に示すように、アセンブリの名前空間ディレクティブを追加します。  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  設定してコマンドを呼び出す、`Command`次の例に示すように、XAML オブジェクトのプロパティ。  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  アセンブリをコピーして貼り付けます.\\ *Visual Studio インストール フォルダー*\Common7\IDE\PrivateAssemblies\ にそれを呼び出す前に読み込まれるかどうかを確認します。  
  
## <a name="adding-commands-with-the-dte-object"></a>DTE オブジェクトにコマンドを追加します。  
 DTE オブジェクトは、スタート ページ、マークアップとコードの両方からアクセスできます。  
  
 マークアップでは、アクセスできるを使用して、[バインディング マークアップ拡張機能](http://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63)を呼び出す構文、<xref:EnvDTE.DTE>オブジェクト。 このアプローチを使用して単純なプロパティのコレクションを返すようにバインドすることができますが、メソッドやサービスにバインドすることはできません。 次の例は、<xref:System.Windows.Controls.TextBlock>コントロールにバインドする、<xref:EnvDTE._DTE.Name%2A>プロパティと<xref:System.Windows.Controls.ListBox>を列挙するコントロール、<xref:EnvDTE.Window.Caption%2A>によって返されるコレクションのプロパティ、<xref:EnvDTE._DTE.Windows%2A>プロパティ。  
  
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
 [スタート ページへのユーザー コントロールの追加](../extensibility/adding-user-control-to-the-start-page.md)

