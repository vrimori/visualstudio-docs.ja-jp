---
title: "オプション ページを作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[ツール オプション] ページ [Visual Studio SDK]、作成"
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
caps.handback.revision: 62
ms.author: "gregvanl"
manager: "ghogen"
---
# オプション ページを作成します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルでは、プロパティ グリッドを使用して確認し、プロパティを設定する単純なツール\/オプション ページを作成します。  
  
 これらのプロパティを保存して、設定ファイルからの復元、次の手順に従ってし、しを参照してください [設定のカテゴリを作成します。](../extensibility/creating-a-settings-category.md)します。  
  
 MPF ツール オプション ページを作成するために 2 つのクラスを提供する、 <xref:Microsoft.VisualStudio.Shell.Package> クラスおよび <xref:Microsoft.VisualStudio.Shell.DialogPage> クラスです。 パッケージ クラスをサブクラス化して、これらのページのコンテナーを提供する VSPackage を作成します。 各ツール オプション ページを作成するには、DialogPage クラスから派生します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## ツール オプションのグリッド ページを作成します。  
 このセクションでは、単純なツールのオプションのプロパティ グリッドを作成します。 表示し、プロパティの値を変更するには、このグリッドを使用します。  
  
#### VSIX プロジェクトを作成し、VSPackage を追加するには  
  
1.  すべての Visual Studio 拡張機能は、拡張機能の資産を格納する VSIX 配置プロジェクトから開始します。 作成、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] という名前の VSIX プロジェクト `MyToolsOptionsExtension`します。 VSIX プロジェクトのテンプレートを見つけることができます、 **新しいプロジェクト** \] ダイアログ ボックス \[ **Visual c\#\/機能拡張**します。  
  
2.  VSPackage をという名前の Visual Studio パッケージ項目テンプレートを追加することによって追加 `MyToolsOptionsPackage`します。**ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。**新しい項目の追加\] ダイアログ ボックス**, には、 **Visual c\# アイテム\/機能拡張** 選択 **Visual Studio パッケージ**します。**名** ダイアログの下部にあるフィールドに、ファイルの名前を変更する `MyToolsOptionsPackage.cs`です。 VSPackage を作成する方法の詳細については、次を参照してください。 [VSPackage で拡張機能を作成します。](../extensibility/creating-an-extension-with-a-vspackage.md)します。  
  
#### ツール オプションのプロパティ グリッドを作成するには  
  
1.  コード エディターで MyToolsOptionsPackage ファイルを開きます。  
  
2.  次の追加ステートメントを使用します。  
  
    ```c#  
    using System.ComponentModel;  
    ```  
  
3.  OptionPageGrid クラスを宣言してから派生 <xref:Microsoft.VisualStudio.Shell.DialogPage>します。  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  適用、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> VSPackage クラス オプションのカテゴリと、OptionPageGrid のオプション ページ名をクラスに割り当てるためにします。 結果は、次のようになります。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  追加、 `OptionInteger` プロパティを `OptionPageGrid` クラスです。  
  
    -   適用、 <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> プロパティに割り当てる、プロパティ グリッドのカテゴリ。  
  
    -   適用、 <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> プロパティの名前を指定します。  
  
    -   適用、 <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> プロパティに割り当てる、説明します。  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  既定の実装 <xref:Microsoft.VisualStudio.Shell.DialogPage> 適切なコンバーターがあるか、構造体または適切なコンバーターのプロパティに展開可能な配列にあるプロパティがサポートされます。 コンバーターの一覧は、次を参照してください。、 <xref:System.ComponentModel> 名前空間。  
  
6.  プロジェクトをビルドし、デバッグを開始します。  
  
7.  Visual Studio の実験用インスタンスで、 **ツール** ボタンをクリックし **オプション**します。  
  
     左側のペインで確認する必要があります **My Category**します。 \(オプション カテゴリはため、表示されるはずの途中で一覧の下にアルファベット順にで表示されるされます\)。 開いている **My Category** \] をクリックし、 **個人用のグリッド ページ**します。右側のウィンドウで、オプションのグリッドが表示されます。 プロパティのカテゴリは **My Options**, 、プロパティの名前と **マイ整数オプション**します。 プロパティの説明、 **マイ整数オプション**, 、ウィンドウの下部に表示されます。 値を 256 の初期値から別のものに変更します。 をクリックして **OK**, を閉じて再度開く **個人用のグリッド ページ**します。 新しい値が引き続き発生することを確認できます。  
  
     オプション ページも Visual Studio のサイド リンク バーを使用できます。 IDE の右上隅の \[クイック起動\] ウィンドウで次のように入力します。 **My Category** され表示されます。 **My Category 個人用のグリッド ページをポイントする** 、ドロップダウン リストに表示します。  
  
## ツール オプションのカスタム作成\] ページ  
 このセクションでは、ui をカスタム ツール オプション ページを作成します。 表示し、プロパティの値を変更するには、このページを使用できます。  
  
1.  コード エディターで MyToolsOptionsPackage ファイルを開きます。  
  
2.  次の追加ステートメントを使用します。  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  追加、 `OptionPageCustom` クラス、直前に、 `OptionPageGrid` クラスです。 新しいクラスを派生 `DialogPage`します。  
  
    ```c#  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4.  GUID 属性を追加します。 なければプロパティを追加します。  
  
    ```c#  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5.  1 秒あたりの適用 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> VSPackage クラスにします。 この属性は、オプションのカテゴリとオプションのページ名に、クラスを割り当てます。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6.  新しい **ユーザー コントロール** MyUserControl をプロジェクトにという名前です。  
  
7.  追加、 **TextBox** ユーザー コントロールのコントロールにします。  
  
     **プロパティ** ウィンドウで、ツールバーのをクリックして、 **イベント** \] ボタンをクリックし、ダブルクリック、 **のままにして** イベントです。 新しいイベント ハンドラーは、MyUserControl.cs コードに表示されます。  
  
8.  追加パブリック `OptionsPage` フィールドで、 `Initialize` コントロール クラスと、イベント ハンドラー オプションを設定する値のテキスト ボックスの内容を更新する方法。  
  
    ```c#  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     `optionsPage` フィールドは、親への参照を保持して `OptionPageCustom` インスタンス。`Initialize` メソッドが表示されます `OptionString` で、 **TextBox**します。 イベント ハンドラーの現在の値を書き込みます、 **TextBox** に、 `OptionString` とリーフを集中、 **\] テキスト ボックス**します。  
  
9. パッケージのコード ファイル内の上書きを追加、 `OptionPageCustom.Window` OptionPageCustom クラスの作成、初期化、およびインスタンスを返すプロパティ `MyUserControl`します。 クラスは、次のようになります。  
  
    ```c#  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. プロジェクトをビルドして実行します。  
  
11. 実験用インスタンスで、クリックして **ツール\/オプション**します。  
  
12. 検索 **マイ カテゴリ** し **、カスタム ページ**します。  
  
13. 値を変更 **なければ**します。 をクリックして **OK**, を閉じて再度開く **個人用ページのカスタム**します。 新しい値が保持されたことを確認できます。  
  
## オプションにアクセスします。  
 このセクションでは、関連付けられたツール オプション ページをホストしている VSPackage のオプションの値を取得できます。 パブリック プロパティの値を取得する、同じ手法を使用できます。  
  
1.  パッケージのコード ファイルでというパブリック プロパティを追加 **OptionInteger** に、 **MyToolsOptionsPackage** クラスです。  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     このコードは呼び出し <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 作成または取得する、 `OptionPageGrid` インスタンス。`OptionPageGrid` 呼び出し <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> 、オプションでは、パブリック プロパティを読み込めません。  
  
2.  という名前のカスタム コマンド項目テンプレートを今すぐ追加 **MyToolsOptionsCommand** 値を表示します。**新しい項目の追加** ダイアログ ボックスに移動 **Visual c\#\/機能拡張** を選択して **にカスタム コマンド**します。**名** ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する **MyToolsOptionsCommand.cs**します。  
  
3.  MyToolsOptionsCommand ファイル内のコマンドの本文を置き換える `ShowMessageBox` を次のメソッド。  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  プロジェクトをビルドし、デバッグを開始します。  
  
5.  実験用インスタンスで、 **ツール** \] メニューのをクリックして **呼び出す MyToolsOptionsCommand**します。  
  
     メッセージ ボックスの現在の値を表示する `OptionInteger`です。  
  
## 参照  
 [オプションと \[オプション\] ページ](../Topic/Options%20and%20Options%20Pages.md)