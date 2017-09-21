---
title: "WPF ツールボックス コントロールを作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ツールボックス コントロール"
  - "toolbox"
  - "WPF"
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# WPF ツールボックス コントロールを作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

WPF \(Windows Presentation Framework\) ツールボックス コントロール テンプレートを使用して、自動的に追加する WPF コントロールを作成できる、 **ツールボックス** 、拡張機能がインストールされている場合。 このトピックは、テンプレートを使用して作成する方法を示しています、 **ツールボックス** コントロールを他のユーザーに配布することができます。  
  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## WPF ツールボックス コントロールを作成します。  
  
#### WPF ツールボックス コントロールでの拡張機能を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する `MyToolboxControl`です。 VSIX プロジェクトのテンプレートを見つけることができます、 **新しいプロジェクト** \] ダイアログ ボックス \[ **Visual c\#\/機能拡張**します。  
  
2.  プロジェクトを開いたら、追加、 **WPF ツールボックス コントロール** という名前の項目テンプレート `MyToolboxControl`します。**ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。**新しい項目の追加** ダイアログ ボックスに移動 **Visual c\#\/機能拡張** を選択して **WPF ツールボックス コントロール**します。**名** ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する `MyToolboxControl.cs`です。  
  
     ソリューションがユーザー コントロールが含まれ、 `ProvideToolboxControlAttribute`<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> にコントロールを追加する、 **ツールボックス**, と **Microsoft.VisualStudio.ToolboxControl** で配置の VSIX マニフェスト アセット エントリです。  
  
#### コントロール UI を作成するには  
  
1.  デザイナーで MyToolboxControl.xaml を開きます。  
  
     デザイナーに、<xref:System.Windows.Controls.Button> コントロールを含む <xref:System.Windows.Controls.Grid> コントロールが表示されます。  
  
2.  グリッド レイアウトを調整します。 選択した場合、 <xref:System.Windows.Controls.Grid> を制御するグリッドの左上隅に青のコントロール バーを表示します。 横棒をクリックして、グリッドに行と列を追加できます。  
  
3.  子コントロールをグリッドに追加します。 ドラッグして、子コントロールを配置することができます、 **ツールボックス** を設定したり、グリッドのセクションに、 `Grid.Row` と `Grid.Column` XAML 内の属性です。 次の例では、グリッドと 2 行目のボタンの上の行で 2 つのラベルを追加します。  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## コントロールの名前変更  
 既定では、コントロールが \[に移動、 **ツールボックス** として **MyToolboxControl** という名前のグループで **MyToolboxControl.MyToolboxControl**します。 MyToolboxControl.xaml.cs ファイルでこれらの名前を変更することができます。  
  
1.  コード ビューで MyToolboxControl.xaml.cs を開きます。  
  
2.  MyToolboxControl クラスを見つけてに変更します。 \(これを行う最も簡単な方法は、クラスの名前を変更するを選択し、 **の名前を変更** 、コンテキスト メニューから手順を実行します。 \(詳細については、 **の名前を変更** コマンドを参照してください [名前の変更リファクタリング \(C\#\)](../csharp-ide/rename-refactoring-csharp.md).\)  
  
3.  移動して、 `ProvideToolboxControl` 属性し、最初のパラメーターの値を変更 **テスト**します。 これでコントロールを配置するグループの名前、 **ツールボックス**します。  
  
     その結果のコードは、次のようになります。  
  
    ```c#  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## ビルド、テスト、展開  
 プロジェクトをデバッグするときにインストールされているコントロールを検索する必要があります、 **ツールボックス** Visual Studio の実験用インスタンスのです。  
  
#### コントロールをビルドおよびテストするには  
  
1.  プロジェクトをリビルドし、デバッグを開始します。  
  
2.  Visual Studio の新しいインスタンスで、WPF アプリケーション プロジェクトを作成します。 XAML デザイナーが開いていることを確認します。  
  
3.  **\[ツールボックス\]** で対象のコントロールを見つけて、デザイン画面にドラッグします。  
  
4.  WPF アプリケーションのデバッグを開始します。  
  
5.  コントロールが表示されることを確認します。  
  
#### コントロールを配置するには  
  
1.  テスト対象のプロジェクトをビルドした後は、プロジェクトの \\bin\\debug\\ フォルダーで .vsix ファイルを確認できます。  
  
2.  ローカル コンピューター上 .vsix ファイルをダブルクリックして、インストール手順に従い、インストールすることができます。 コントロールをアンインストールするには **ツール\/拡張機能と更新プログラム** コントロール拡張機能の表示をクリックし、 **アンインストール**します。  
  
3.  .vsix ファイルをネットワークまたは Web サイトにアップロードします。  
  
     ファイルをアップロードする場合、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイト、他のユーザーが使用できる **ツール\/拡張機能と更新プログラム** Visual studio オンラインのコントロールを見つけて、インストールにします。