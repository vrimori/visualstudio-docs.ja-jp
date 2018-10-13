---
title: WPF ツールボックス コントロールの作成 |Microsoft Docs
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
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a521566d25509750334e4f1202699787c3343ca6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225616"
---
# <a name="creating-a-wpf-toolbox-control"></a>WPF ツールボックス コントロールの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WPF (Windows Presentation Framework) ツールボックス コントロール テンプレートは自動的に追加する WPF コントロールを作成することができます、**ツールボックス**拡張機能がインストールされている場合。 このトピックでは、テンプレートを使用して作成する方法、**ツールボックス**コントロールを他のユーザーに配布することができます。  
  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-wpf-toolbox-control"></a>WPF ツールボックス コントロールの作成  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF ツールボックス コントロールでの拡張機能を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`MyToolboxControl`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  プロジェクトが開いたら、追加、 **WPF ツールボックス コントロール**という名前の項目テンプレート`MyToolboxControl`します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**WPF ツールボックス コントロール**します。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名を変更して`MyToolboxControl.cs`します。  
  
     ソリューションには、ユーザー コントロールが含まれるようになりました、 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>にコントロールを追加する、**ツールボックス**、および**Microsoft.VisualStudio.ToolboxControl**の VSIX マニフェストでアセット エントリ 展開します。  
  
#### <a name="to-create-the-control-ui"></a>コントロール UI を作成するには  
  
1.  MyToolboxControl.xaml をデザイナーで開きます。  
  
     デザイナーに、<xref:System.Windows.Controls.Button> コントロールを含む <xref:System.Windows.Controls.Grid> コントロールが表示されます。  
  
2.  グリッド レイアウトを調整します。 選択すると、<xref:System.Windows.Controls.Grid>制御、グリッドの左上隅に青のコントロール バーを表示します。 横棒をクリックして、グリッドに行と列を追加できます。  
  
3.  子コントロールをグリッドに追加します。 ドラッグして子コントロールを配置することができます、**ツールボックス**かを設定して、グリッドのセクションにその`Grid.Row`と`Grid.Column`XAML 内の属性。 次の例では、グリッドと 2 行目のボタンの上の行で 2 つのラベルを追加します。  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>コントロールの名前変更  
 既定では、コントロールに表示されます、**ツールボックス**として**MyToolboxControl**という名前のグループで**MyToolboxControl.MyToolboxControl**します。 MyToolboxControl.xaml.cs ファイルでこれらの名前を変更することができます。  
  
1.  MyToolboxControl.xaml.cs をコード ビューで開きます。  
  
2.  MyToolboxControl クラスを見つけてに変更します。 (これを行う最も簡単な方法が、クラスの名前を変更するには、選択**の名前を変更**コンテキスト メニューから、手順を実行します。 (の詳細については、**の名前を変更**コマンドを参照してください[名前の変更リファクタリング (c#)](../csharp-ide/rename-refactoring-csharp.md))。  
  
3.  移動して、`ProvideToolboxControl`属性し、最初のパラメーターの値を変更**テスト**します。 これは、内のコントロールを含むグループの名前、**ツールボックス**します。  
  
     結果として得られるコードは次のようになります。  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>ビルド、テスト、展開  
 プロジェクトをデバッグするときにインストールされているコントロールを検索する必要があります、**ツールボックス**の Visual Studio の実験用インスタンス。  
  
#### <a name="to-build-and-test-the-control"></a>コントロールをビルドおよびテストするには  
  
1.  プロジェクトをリビルドし、デバッグを開始します。  
  
2.  Visual Studio の新しいインスタンスで、WPF アプリケーション プロジェクトを作成します。 XAML デザイナーが開いていることを確認します。  
  
3.  **[ツールボックス]** で対象のコントロールを見つけて、デザイン画面にドラッグします。  
  
4.  WPF アプリケーションのデバッグを開始します。  
  
5.  コントロールが表示されることを確認します。  
  
#### <a name="to-deploy-the-control"></a>コントロールを配置するには  
  
1.  テスト対象のプロジェクトをビルドした後、プロジェクトの \bin\debug\ フォルダーに、.vsix ファイルが表示されます。  
  
2.  ローカル コンピューター上、.vsix ファイルをダブルクリックし、インストール手順に従い、それをインストールできます。 コントロールをアンインストールするには**ツール/拡張機能と更新**コントロール拡張機能を検索し、**アンインストール**します。  
  
3.  .vsix ファイルをネットワークまたは Web サイトにアップロードします。  
  
     ファイルをアップロードする場合、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト、他のユーザーが使用できる**ツール/拡張機能と更新**で Visual Studio online のコントロールを検索してインストールします。

