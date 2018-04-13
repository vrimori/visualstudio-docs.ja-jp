---
title: オプション ページを作成する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d0888a584e31c26c9f64cdcff70cc2f5dc8a1453
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="creating-an-options-page"></a>オプション ページを作成します。
このチュートリアルでは、プロパティ グリッドを使用して確認し、プロパティを設定する単純なツール/オプション ページを作成します。  
  
 これらのプロパティを保存して、設定ファイルからの復元、以下の手順としを参照してください[、設定のカテゴリを作成する](../extensibility/creating-a-settings-category.md)です。  
  
 MPF ツール オプション ページを作成するために 2 つのクラスを提供する、<xref:Microsoft.VisualStudio.Shell.Package>クラスおよび<xref:Microsoft.VisualStudio.Shell.DialogPage>クラスです。 パッケージ クラスをサブクラス化して、これらのページのコンテナーを提供する VSPackage を作成します。 各ツール オプション ページを作成するには、DialogPage クラスから派生します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-tools-options-grid-page"></a>ツール オプションのグリッド ページを作成します。  
 このセクションでは、単純なツールのオプションのプロパティ グリッドを作成します。 このグリッドを使用して、表示し、プロパティの値を変更します。  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>VSIX プロジェクトを作成し、VSPackage を追加するには  
  
1.  すべての Visual Studio 拡張機能は、資産を拡張機能を含んでいる VSIX 配置プロジェクトを開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`MyToolsOptionsExtension`です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  という名前の Visual Studio パッケージ項目テンプレートを追加することで、VSPackage を追加`MyToolsOptionsPackage`です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加 ダイアログ**に進み、 **Visual c# アイテム/機能拡張**選択と**Visual Studio パッケージ**です。 **名前**ダイアログの下部にあるフィールドに、ファイル名に変更`MyToolsOptionsPackage.cs`です。 VSPackage を作成する方法の詳細については、次を参照してください。 [VSPackage で拡張機能を作成する](../extensibility/creating-an-extension-with-a-vspackage.md)です。  
  
#### <a name="to-create-the-tools-options-property-grid"></a>ツール オプションのプロパティ グリッドを作成するには  
  
1.  MyToolsOptionsPackage ファイル、コード エディターで開きます。  
  
2.  次の追加ステートメントを使用します。  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  OptionPageGrid クラスを宣言してから派生<xref:Microsoft.VisualStudio.Shell.DialogPage>です。  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  適用、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> VSPackage クラス オプションのカテゴリと、OptionPageGrid のオプションのページ名をクラスに割り当てるためにします。 結果は、次のようになります。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  追加、`OptionInteger`プロパティを`OptionPageGrid`クラスです。  
  
    -   適用、<xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName>プロパティに割り当てる、プロパティ グリッドのカテゴリ。  
  
    -   適用、<xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName>名プロパティに割り当てる。  
  
    -   適用、<xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName>プロパティに割り当てる、説明します。  
  
    ```csharp  
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
    >  既定の実装<xref:Microsoft.VisualStudio.Shell.DialogPage>適切なコンバーターがあるか、構造体や配列を適切なコンバーターのプロパティを展開するプロパティをサポートします。 コンバーターの一覧は、次を参照してください。、<xref:System.ComponentModel>名前空間。  
  
6.  プロジェクトをビルドし、デバッグを開始します。  
  
7.  Visual Studio の実験用インスタンスで、**ツール**ボタンをクリックし**オプション**です。  
  
     左側のウィンドウで表示されるはず**マイ カテゴリ**です。 (オプションのカテゴリが表示されます、アルファベット順に表示されるはずの途中で、一覧に表示するようにします。)開いている**マイ カテゴリ** をクリックし、**個人用のグリッド ページ**です。右側のウィンドウで、オプションのグリッドが表示されます。 プロパティのカテゴリは**My Options**、プロパティの名前と**マイ整数オプション**です。 プロパティの説明、 **My 整数オプション**ウィンドウの下部に表示されます。 別のものを 256 の初期値から値を変更します。 をクリックして**OK**を閉じてから開き**個人用のグリッド ページ**です。 新しい値が引き続き発生することを確認できます。  
  
     オプション ページも Visual Studio の クイック起動で使用できます。 IDE の右上隅の [クイック起動] ウィンドウで次のように入力します。**マイ カテゴリ**と表示されます**マイ カテゴリには個人用のグリッド ページ]-> [** 、ドロップダウン リストに表示します。  
  
## <a name="creating-a-tools-options-custom-page"></a>ツール オプションのカスタムの作成 ページ  
 このセクションでは、カスタム UI を使用したツール オプション ページを作成します。 このページを使用して、表示し、プロパティの値を変更します。  
  
1.  MyToolsOptionsPackage ファイル、コード エディターで開きます。  
  
2.  次の追加ステートメントを使用します。  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  追加、`OptionPageCustom`クラス、直前に、`OptionPageGrid`クラスです。 新しいクラスを派生`DialogPage`です。  
  
    ```csharp  
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
  
    ```csharp  
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
  
5.  1 秒あたりの適用<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>VSPackage クラスにします。 この属性は、オプションのカテゴリとオプションのページ名、クラスを割り当てます。  
  
    ```csharp  
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
  
6.  新しい**ユーザー コントロール**MyUserControl をプロジェクトにという名前です。  
  
7.  追加、 **TextBox**コントロールをユーザー コントロールです。  
  
     **プロパティ**ウィンドウ、ツールバーで、をクリックして、**イベント**ボタンをクリックし、ダブルクリック、**のままにして**イベント。 MyUserControl.cs コードに、新しいイベント ハンドラーが表示されます。  
  
8.  追加パブリック`OptionsPage`フィールド、`Initialize`コントロール クラス、およびオプションの設定に、イベント ハンドラーの値、テキスト ボックスの内容を更新する方法。  
  
    ```csharp  
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
  
     `optionsPage`フィールドは、親への参照を保持`OptionPageCustom`インスタンス。 `Initialize`メソッドが表示されます`OptionString`で、 **TextBox**です。 イベント ハンドラーの現在の値を書き込みます、 **テキスト ボックス**を`OptionString`リーフを集中すると、 **テキスト ボックス**です。  
  
9. パッケージのコード ファイル内の上書きを追加、`OptionPageCustom.Window`プロパティを作成、初期化、およびのインスタンスを返す OptionPageCustom クラスを`MyUserControl`です。 クラスは、次のようになります。  
  
    ```csharp  
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
  
11. 実験用インスタンスのをクリックして**ツール/オプション**です。  
  
12. 検索**My カテゴリ**し**My Custom ページ**です。  
  
13. 値を変更**なければ**です。 をクリックして**OK**を閉じてから開き**マイ カスタム ページ**です。 新しい値が保存されることを確認できます。  
  
## <a name="accessing-options"></a>オプションにアクセスします。  
 このセクションでは、関連付けられたツール オプション ページをホストする VSPackage からオプションの値を取得します。 任意のパブリック プロパティの値を取得すると同じ手法を使用できます。  
  
1.  パッケージのコード ファイルでというパブリック プロパティを追加**OptionInteger**を**MyToolsOptionsPackage**クラスです。  
  
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
  
     このコードを呼び出す<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>作成または取得する、`OptionPageGrid`インスタンス。 `OptionPageGrid` 呼び出し<xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A>オプションでは、パブリック プロパティを読み込めません。  
  
2.  という名前のカスタム コマンド項目テンプレートを追加するようになりました**MyToolsOptionsCommand**値を表示します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**にカスタム コマンド**です。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する**MyToolsOptionsCommand.cs**です。  
  
3.  MyToolsOptionsCommand ファイル内のコマンドの本文を置換`ShowMessageBox`を次のメソッド。  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  プロジェクトをビルドし、デバッグを開始します。  
  
5.  実験用インスタンスの上、**ツール** メニューのをクリックして**呼び出す MyToolsOptionsCommand**です。  
  
     メッセージ ボックスには、現在の値が表示されます。`OptionInteger`です。  
  
## <a name="see-also"></a>関連項目  
 [オプションとオプション ページ](../extensibility/internals/options-and-options-pages.md)