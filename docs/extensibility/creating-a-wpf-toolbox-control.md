---
title: WPF ツールボックス コントロールの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 43734720a4e86f9f1e214285df1873b39b67fa01
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500333"
---
# <a name="create-a-wpf-toolbox-control"></a>WPF ツールボックス コントロールを作成します。
WPF (Windows Presentation Framework) ツールボックス コントロール テンプレートは自動的に追加する WPF コントロールを作成することができます、**ツールボックス**拡張機能がインストールされている場合。 このトピックでは、テンプレートを使用して作成する方法、**ツールボックス**コントロールを他のユーザーに配布することができます。  
  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="create-a-wpf-toolbox-control"></a>WPF ツールボックス コントロールを作成します。  
  
### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF ツールボックス コントロールでの拡張機能を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`MyToolboxControl`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#** > **Extensibility**します。  
  
2.  プロジェクトが開いたら、追加、 **WPF ツールボックス コントロール**という名前の項目テンプレート`MyToolboxControl`します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#** > **拡張**選択**WPF ツールボックス コントロール**。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名を変更して*MyToolboxControl.cs*します。  
  
     ソリューションには、ユーザー コントロールが含まれるようになりました、 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>にコントロールを追加する、**ツールボックス**、および**Microsoft.VisualStudio.ToolboxControl**の VSIX マニフェストでアセット エントリ 展開します。  
  
#### <a name="to-create-the-control-ui"></a>コントロール UI を作成するには  
  
1.  開いている*MyToolboxControl.xaml*デザイナー。  
  
     デザイナーの表示、<xref:System.Windows.Controls.Grid>コントロールを含む、<xref:System.Windows.Controls.Button>コントロール。  
  
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
 既定では、コントロールに表示されます、**ツールボックス**として**MyToolboxControl**という名前のグループで**MyToolboxControl.MyToolboxControl**します。 これらの名前を変更することができます、 *MyToolboxControl.xaml.cs*ファイル。  
  
1.  開いている*MyToolboxControl.xaml.cs*コード ビューで。  
  
2.  検索、`MyToolboxControl`クラスし、名前に変更します。 (これを行う最も簡単な方法が、クラスの名前を変更するには、選択**の名前を変更**コンテキスト メニューから、手順を実行します。 (の詳細については、**の名前を変更**コマンドを参照してください[名前変更リファクタリング (c#)](../ide/reference/rename.md))。
  
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
  
## <a name="build-test-and-deployment"></a>ビルド、テスト、および展開  
 プロジェクトをデバッグするときにインストールされているコントロールを検索する必要があります、**ツールボックス**の Visual Studio の実験用インスタンス。  
  
### <a name="to-build-and-test-the-control"></a>コントロールをビルドおよびテストするには  
  
1.  プロジェクトをリビルドし、デバッグを開始します。  
  
2.  Visual Studio の新しいインスタンスで、WPF アプリケーション プロジェクトを作成します。 XAML デザイナーが開いていることを確認します。  
  
3.  **[ツールボックス]** で対象のコントロールを見つけて、デザイン画面にドラッグします。  
  
4.  WPF アプリケーションのデバッグを開始します。  
  
5.  コントロールが表示されることを確認します。  
  
### <a name="to-deploy-the-control"></a>コントロールを配置するには  
  
1.  見つかりますテスト対象のプロジェクトをビルドした後、 *.vsix*ファイルで、* \bin\debug\*プロジェクトのフォルダー。  
  
2.  ダブルクリックして、ローカル コンピューターにインストールできる、 *.vsix*ファイルとインストールの手順を実行します。 コントロールをアンインストールするには**ツール** > **拡張機能と更新**コントロール拡張機能を検索し、**アンインストール**します。  
  
3.  アップロード、 *.vsix*ファイルは、ネットワークまたは Web サイトにします。  
  
     ファイルをアップロードする場合、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト、他のユーザーが使用できる**ツール** > **拡張機能と更新**Visual Studio でのコントロールを検索するにはオンラインし、インストールします。