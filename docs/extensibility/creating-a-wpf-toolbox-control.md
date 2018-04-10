---
title: WPF ツールボックス コントロールの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
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
caps.latest.revision: 16
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c1a8338f0ebd964e5d039ffa8dff000a441523f8
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="creating-a-wpf-toolbox-control"></a>WPF ツールボックス コントロールの作成
WPF (Windows Presentation Framework) ツールボックス コントロール テンプレートを使用に自動的に追加されている WPF コントロールを作成する、**ツールボックス**拡張機能がインストールされている場合。 このトピックは、テンプレートを使用して作成する方法を示しています、**ツールボックス**コントロールを他のユーザーに配布することができます。  
  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-wpf-toolbox-control"></a>WPF ツールボックス コントロールの作成  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF ツールボックス コントロールでの拡張機能を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`MyToolboxControl`です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  プロジェクトを開いたら、追加、 **WPF ツールボックス コントロール**という名前の項目テンプレート`MyToolboxControl`です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択**WPF ツールボックス コントロール**です。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名に変更`MyToolboxControl.cs`です。  
  
     ソリューションには、ユーザー コントロールが含まれるようになりました、 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>にコントロールを追加する、**ツールボックス**、および**Microsoft.VisualStudio.ToolboxControl** VSIX マニフェストにアセット エントリ 展開します。  
  
#### <a name="to-create-the-control-ui"></a>コントロール UI を作成するには  
  
1.  MyToolboxControl.xaml をデザイナーで開きます。  
  
     デザイナーの表示、<xref:System.Windows.Controls.Grid>が含まれるコントロール、<xref:System.Windows.Controls.Button>コントロール。  
  
2.  グリッド レイアウトを調整します。 選択した場合、<xref:System.Windows.Controls.Grid>を制御するグリッドの左上隅に青のコントロール バーを表示します。 バーをクリックして、グリッドに行と列を追加できます。  
  
3.  子コントロールをグリッドに追加します。 ドラッグしてから、子コントロールを配置することができます、**ツールボックス**かを設定して、グリッドのセクションにその`Grid.Row`と`Grid.Column`XAML 内の属性です。 次の例では、グリッドとボタンを 2 番目の行の先頭行に 2 つのラベルを追加します。  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>コントロールの名前変更  
 既定では、コントロールに表示されます、**ツールボックス**として**MyToolboxControl**という名前のグループで**MyToolboxControl.MyToolboxControl**です。 MyToolboxControl.xaml.cs ファイルでこれらの名前を変更することができます。  
  
1.  MyToolboxControl.xaml.cs をコード ビューで開きます。  
  
2.  MyToolboxControl クラスを検索しに変更します。 (これを行う最も簡単な方法は、クラスの名前を変更するを選択し、**の名前を変更**コンテキスト メニューから、手順に従います。 (詳細については、**の名前を変更**コマンドを参照してください[名前の変更リファクタリング (c#)](../ide/reference/rename.md))。
  
3.  移動して、`ProvideToolboxControl`属性への最初のパラメーターの値を変更して**テスト**です。 これでコントロールを配置するグループの名前、**ツールボックス**です。  
  
     結果のコードは、次のようになります。  
  
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
 プロジェクトをデバッグするときにインストールされているコントロールを検索する必要があります、**ツールボックス**Visual Studio の実験用インスタンスのです。  
  
#### <a name="to-build-and-test-the-control"></a>コントロールをビルドおよびテストするには  
  
1.  プロジェクトをリビルドし、デバッグを開始します。  
  
2.  Visual Studio の新しいインスタンスで、WPF アプリケーション プロジェクトを作成します。 XAML デザイナーが開いていることを確認してください。  
  
3.  **[ツールボックス]** で対象のコントロールを見つけて、デザイン画面にドラッグします。  
  
4.  WPF アプリケーションのデバッグを開始します。  
  
5.  コントロールが表示されることを確認します。  
  
#### <a name="to-deploy-the-control"></a>コントロールを配置するには  
  
1.  テスト対象のプロジェクトをビルドした後、プロジェクトの \bin\debug\ フォルダーで探し、.vsix ファイルが表示されます。  
  
2.  ローカル コンピューター上、.vsix ファイルをダブルクリックし、インストール手順に従い、それをインストールできます。 コントロールをアンインストールするには**ツール/拡張機能と更新**コントロール拡張機能を検索し、**アンインストール**です。  
  
3.  .vsix ファイルをネットワークまたは Web サイトにアップロードします。  
  
     ファイルをアップロードする場合、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト、その他のユーザーが使用できる**ツール/拡張機能と更新プログラム**Visual studio オンライン コントロールを見つけて、インストールにします。