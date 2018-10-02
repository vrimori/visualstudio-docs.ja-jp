---
title: スタート ページのカスタムの作成 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b217c098f34240ddc4505821ae8446e4244605da
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592806"
---
# <a name="creating-a-custom-start-page"></a>カスタム スタート ページの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[カスタム スタート ページを作成する](https://docs.microsoft.com/visualstudio/extensibility/creating-a-custom-start-page)します。  
  
」の説明に従って、スタート ページ プロジェクト テンプレートを使用してカスタム スタート ページを作成できない場合[スタート ページ](../misc/creating-your-own-start-page.md)、このドキュメントの手順に従って 1 つを手動で作成できます。  
  
## <a name="creating-a-blank-start-page"></a>空白のスタート ページの作成  
 まず、空白のスタート ページを Visual Studio で認識するタグ構造を持つ .xaml ファイルを作成してください。 次に、マークアップと分離コードを生成する機能と外観を追加します。  
  
#### <a name="to-create-a-blank-start-page"></a>空白のスタート ページを作成するには  
  
1.  型の新しいプロジェクトを作成する**WPF アプリケーション**(**Visual c#/Windows デスクトップ**します。  
  
2.  `Microsoft.VisualStudio.Shell.14.0` への参照を追加します。  
  
3.  XML エディターで XAML ファイルを開き、変更、最上位\<ウィンドウ > 要素を\<UserControl > 名前空間宣言を削除することがなく要素。  
  
4.  削除、`x:Class`最上位の要素を宣言します。 これにより、XAML コンテンツのスタート ページをホストしている Visual Studio ツール ウィンドウとの互換性。  
  
5.  最上位レベルに次の名前空間宣言を追加\<UserControl > 要素。  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     これらの名前空間では、Visual Studio コマンド、制御、および UI 設定にアクセスできます。 詳細については、次を参照してください。[スタート ページを Visual Studio のコマンドを追加する](../extensibility/adding-visual-studio-commands-to-a-start-page.md)します。  
  
     次の例では、空白のスタート ページの .xaml ファイルに、マークアップを示します。 内部で任意のカスタム コンテンツを移動する必要があります<xref:System.Windows.Controls.Grid>要素。  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  空のコントロールを追加\<UserControl > カスタム スタート ページを入力する要素。 Visual Studio に固有の機能を追加する方法については、次を参照してください。[スタート ページを Visual Studio のコマンドを追加する](../extensibility/adding-visual-studio-commands-to-a-start-page.md)します。  
  
## <a name="testing-and-applying-the-custom-start-page"></a>カスタム スタート ページのテストと適用  
 Visual Studio がクラッシュしないことを確認するまでは、カスタム スタート ページを実行する Visual Studio のプライマリ インスタンスを設定しないでください。 代わりに、実験用インスタンスでテストします。  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>手動で作成したカスタム スタート ページをテストするには  
  
1.  コピーは、XAML ファイルとサポート テキスト ファイルまたはマークアップをファイルに、 **%USERPROFILE%\My documents \visual Studio 2015 \startpages\\** フォルダー。  
  
2.  スタート ページは、すべてのコントロールまたは Visual Studio がインストールされていないアセンブリで型を参照する場合、アセンブリをコピーし、貼り付けることで_Visual Studio インストール フォルダー_**\Common7\IDE\PrivateAssemblies\\**します。  
  
3.  Visual Studio コマンド プロンプトで「 **devenv/rootsuffix Exp**を Visual Studio の実験用インスタンスを開きます。  
  
4.  実験用のインスタンスに移動、**ツール/オプション/環境/スタートアップ**ページおよび元の XAML ファイルを選択、**スタート ページのカスタマイズ**ドロップダウンします。  
  
5.  **[表示]** メニューの **[スタート ページ]** をクリックします。  
  
     カスタム スタート ページが表示されます。 ファイルを変更する場合は、する必要があります実験用インスタンスを閉じて、変更を行います、コピーし、変更されたファイルを貼り付けるして変更を表示する実験用インスタンスを再度開きます。  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Visual Studio のプライマリ インスタンスで、カスタム スタート ページを適用  
  
-   スタート ページをテストして、安定していることと、使用、**スタート ページのカスタマイズ**オプション、**オプション**Visual Studio のプライマリ インスタンスのスタート ページとしてそれを選択するダイアログ ボックス  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: カスタム XAML をスタート ページに追加します。](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [スタート ページにユーザー コントロールを追加します。](../extensibility/adding-user-control-to-the-start-page.md)   
 [Visual Studio のコマンドをスタート ページに追加します。](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [チュートリアル: スタート ページでユーザー設定の保存](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [カスタム スタート ページのデプロイ](../extensibility/deploying-custom-start-pages.md)

