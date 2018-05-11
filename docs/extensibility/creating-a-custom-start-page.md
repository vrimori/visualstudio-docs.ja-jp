---
title: 作成するカスタム スタート ページ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71892262d98b175b111218068a02d03ad3d04caa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-custom-start-page"></a>カスタム スタート ページを作成します。
このドキュメントでの手順に従って、カスタム スタート ページを作成できます。  
  
## <a name="creating-a-blank-start-page"></a>空白のスタート ページの作成  
 まず、空白のスタート ページを Visual Studio が認識できるタグ構造を持つ .xaml ファイルを作成してください。 次に、マークアップと分離コードを生成する機能と外観を追加します。  
  
#### <a name="to-create-a-blank-start-page"></a>空白のスタート ページを作成するには  
  
1.  型の新しいプロジェクトを作成**WPF アプリケーション**(**Visual c#/Windows デスクトップ**です。  
  
2.  `Microsoft.VisualStudio.Shell.14.0` への参照を追加します。  
  
3.  XML エディターで XAML ファイルを開き、変更、最上位\<ウィンドウ > 要素を\<UserControl > 名前空間の宣言を削除することがなく要素。  
  
4.  削除、`x:Class`最上位の要素を宣言します。 これにより、XAML のコンテンツのスタート ページをホストしている Visual Studio のツール ウィンドウとの互換性。  
  
5.  次の名前空間宣言を最上位レベルに追加\<UserControl > 要素。  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     これらの名前空間では、Visual Studio コマンド、コントロール、および UI 設定にアクセスできます。 詳細については、次を参照してください。[スタート ページを Visual Studio のコマンドを追加する](../extensibility/adding-visual-studio-commands-to-a-start-page.md)です。  
  
     次の例は、空白のスタート ページの .xaml ファイル内のマークアップを示します。 ユーザー設定のコンテンツは、内側のべき<xref:System.Windows.Controls.Grid>要素。  
  
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
  
6.  空にコントロールを追加\<UserControl > 要素のカスタム スタート ページを埋めるためにします。 Visual Studio に固有の機能を追加する方法については、次を参照してください。[スタート ページを Visual Studio のコマンドを追加する](../extensibility/adding-visual-studio-commands-to-a-start-page.md)です。  
  
## <a name="testing-and-applying-the-custom-start-page"></a>カスタム スタート ページのテストと適用  
 Visual Studio がクラッシュしないことを確認するまで、カスタム スタート ページを実行する Visual Studio のプライマリ インスタンスを設定しないでください。 代わりに、実験用インスタンスでテストします。  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>手動で作成したカスタム スタート ページをテストするには  
  
1.  XAML ファイル、および、サポート テキスト ファイルやマークアップ ファイルにコピー、 **%USERPROFILE%\My documents \visual Studio 2015 \startpages\\** フォルダーです。  
  
2.  スタート ページが、コントロールや Visual Studio がインストールされていないアセンブリ内の型を参照する場合、アセンブリをコピーしでそれらを貼り付け * Visual Studio インストール フォルダー ***\Common7\IDE\PrivateAssemblies\\** .  
  
3.  Visual Studio コマンド プロンプトで「 **devenv/rootsuffix Exp**を Visual Studio の実験用インスタンスを開きます。  
  
4.  実験用インスタンスに移動、**ツール/オプション/環境/スタートアップ**ページの XAML ファイルをクリックし、**スタート ページのカスタマイズ**ドロップダウンします。  
  
5.  **[表示]** メニューの **[スタート ページ]** をクリックします。  
  
     カスタム スタート ページが表示されます。 ファイルを変更する場合は、する必要がありますの実験用インスタンスを閉じて、変更、コピー貼り付け、変更されたファイルを開き直します実験用インスタンスの変更を表示します。  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Visual Studio のプライマリ インスタンスで、カスタム スタート ページを適用  
  
-   スタート ページをテストし、安定していることを検出された後、使用、**スタート ページのカスタマイズ**オプション、**オプション**Visual Studio のプライマリ インスタンスのスタート ページとして選択するダイアログ ボックス  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: カスタム XAML をスタート ページに追加します。](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [スタート ページにユーザー コントロールを追加します。](../extensibility/adding-user-control-to-the-start-page.md)   
 [Visual Studio のコマンドをスタート ページに追加します。](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [チュートリアル: スタート ページ上のユーザー設定の保存](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [カスタム スタート ページのデプロイ](../extensibility/deploying-custom-start-pages.md)