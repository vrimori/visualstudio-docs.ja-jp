---
title: "スタート ページのカスタムを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 18
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
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 2902ac3b5cd4fd038bdaf277a8390d5eb9e96b28
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-custom-start-page"></a>カスタム スタート ページを作成します。
このドキュメントの手順に従って、カスタム スタート ページを作成できます。  
  
## <a name="creating-a-blank-start-page"></a>空白のスタート ページの作成  
 まず、空のスタート ページを Visual Studio で認識するタグの構造を持つ .xaml ファイルを作成してください。 次に、マークアップおよび分離コードを生成する機能と外観を追加します。  
  
#### <a name="to-create-a-blank-start-page"></a>空白のスタート ページを作成するには  
  
1.  型の新しいプロジェクトを作成**WPF アプリケーション**(**Visual C# の場合と Windows デスクトップ**します。  
  
2.  
          `Microsoft.VisualStudio.Shell.14.0` への参照を追加します。  
  
3.  XML エディターで XAML ファイルを開き、最上位レベルを変更する\<ウィンドウ > 要素を\<UserControl > 名前空間宣言を削除することがなく要素。  
  
4.  削除、`x:Class`最上位の要素を宣言します。 これにより、XAML コンテンツのスタート ページをホストしている Visual Studio ツール ウィンドウとの互換性。  
  
5.  次の名前空間宣言を最上位レベルに追加\<UserControl > 要素。  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     これらの名前空間では、Visual Studio のコマンド、コントロール、および UI 設定にアクセスできます。 詳細については、次を参照してください。[スタート ページに Visual Studio のコマンドを追加する](../extensibility/adding-visual-studio-commands-to-a-start-page.md)です。  
  
     次の例では、空白のスタート ページの .xaml ファイルで、マークアップを示します。 ユーザー設定のコンテンツは、内側のべき<xref:System.Windows.Controls.Grid>要素</xref:System.Windows.Controls.Grid>。  
  
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
  
6.  空にコントロールを追加\<UserControl > カスタム スタート ページを設定する要素。 Visual Studio に固有の機能を追加する方法については、次を参照してください。[スタート ページに Visual Studio のコマンドを追加する](../extensibility/adding-visual-studio-commands-to-a-start-page.md)です。  
  
## <a name="testing-and-applying-the-custom-start-page"></a>カスタム スタート ページのテストと適用  
 Visual Studio がクラッシュしないことを確認するまでは、カスタム スタート ページを実行する Visual Studio のプライマリ インスタンスを設定しないでください。 代わりに、実験用インスタンスでテストします。  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>手動で作成したカスタム スタート ページをテストするには  
  
1.  XAML ファイルとサポート テキスト ファイル、またはマークアップ ファイルをコピー、 **%USERPROFILE%\My documents \visual Studio 2015\StartPages\\ **フォルダーです。  
  
2.  スタート ページが、コントロールや Visual Studio がインストールされていないアセンブリ内の型を参照する場合、アセンブリをコピーし、貼り付けることで*Visual Studio インストール フォルダー***\Common7\IDE\PrivateAssemblies\\**します。  
  
3.  Visual Studio コマンド プロンプトで次のように入力します。 **devenv/rootsuffix Exp**を Visual Studio の実験用インスタンスを開きます。  
  
4.  実験用インスタンスで、**ツール/オプション/環境/スタートアップ**ページおよび元の XAML ファイルを選択、**スタート ページのカスタマイズ**ドロップダウンです。  
  
5.  **[表示]** メニューの **[スタート ページ]**をクリックします。  
  
     カスタム スタート ページが表示されます。 ファイルを変更する場合は、する必要があります実験用インスタンスを閉じる、変更を加える、コピーし変更されたファイルを貼り付けますおよび変更を表示する実験用インスタンスを再度開きます。  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Visual Studio のプライマリ インスタンスで、カスタム スタート ページを適用  
  
-   スタート ページをテストし、安定していることを検出後、使用、**スタート ページのカスタマイズ**オプション、**オプション**Visual Studio のプライマリ インスタンスのスタート ページとしてそれを選択 ダイアログ ボックス  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: カスタム XAML をスタート ページに追加します。](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [スタート ページにユーザー コントロールを追加します。](../extensibility/adding-user-control-to-the-start-page.md)   
 [Visual Studio のコマンドをスタート ページに追加します。](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [チュートリアル: [スタート] ページのユーザー設定の保存](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [カスタム スタート ページを展開します。](../extensibility/deploying-custom-start-pages.md)
