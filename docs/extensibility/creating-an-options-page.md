---
title: オプション ページの作成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35845ed22fa06ca7df62c71ddea4be3629534af9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953472"
---
# <a name="create-an-options-page"></a>オプション ページを作成します。
このチュートリアルでは、プロパティ グリッドを使用して確認し、プロパティを設定する単純なツール/オプション ページを作成します。  
  
 これらのプロパティを保存して、設定ファイルからの復元、次の手順に従ってし、しを参照してください[設定カテゴリの作成](../extensibility/creating-a-settings-category.md)です。  
  
 MPF ツール オプション ページを作成するために 2 つのクラスを提供する、<xref:Microsoft.VisualStudio.Shell.Package>クラスおよび<xref:Microsoft.VisualStudio.Shell.DialogPage>クラス。 これらのページをサブクラス化して、コンテナーを提供する VSPackage を作成する、`Package`クラス。 派生することによって各ツール オプション ページを作成する、`DialogPage`クラス。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-a-tools-options-grid-page"></a>ツール オプションのグリッド ページを作成します。  
 このセクションでは、単純なツールのオプションのプロパティ グリッドを作成します。 表示し、プロパティの値を変更するには、このグリッドを使用します。  
  
### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>VSIX プロジェクトを作成し、VSPackage を追加するには  
  
1. すべての Visual Studio 拡張機能は、拡張機能資産が含まれる VSIX 配置プロジェクトで開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`MyToolsOptionsExtension`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#** > **Extensibility**します。  
  
2. という名前の Visual Studio パッケージ項目テンプレートを追加することで、VSPackage を追加`MyToolsOptionsPackage`します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 **新しい項目の追加 ダイアログ**に移動して、 **Visual c# アイテム** > **拡張**選択**Visual Studio パッケージ**。 **名前**ダイアログの下部にあるフィールドに、ファイル名を変更して`MyToolsOptionsPackage.cs`します。 VSPackage を作成する方法の詳細については、次を参照してください。 [VSPackage を使用した拡張機能を作成する](../extensibility/creating-an-extension-with-a-vspackage.md)します。  
  
### <a name="to-create-the-tools-options-property-grid"></a>ツール オプションのプロパティ グリッドを作成するには  
  
1.  開く、 *MyToolsOptionsPackage*コード エディターでファイル。  
  
2.  次の追加ステートメントを使用します。  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  宣言、`OptionPageGrid`クラスし、派生から<xref:Microsoft.VisualStudio.Shell.DialogPage>します。  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  適用する<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>を`VSPackage`オプションのカテゴリと、OptionPageGrid のオプション ページの名前をクラスに割り当てるためのクラス。 このよう、結果になります。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  追加、`OptionInteger`プロパティを`OptionPageGrid`クラス。  
  
    -   適用する<xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName>プロパティ グリッドのカテゴリをプロパティに割り当てる。  
  
    -   適用する<xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName>プロパティに名前を指定します。  
  
    -   適用、<xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName>に割り当てるプロパティを説明します。  
  
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
    >  既定の実装<xref:Microsoft.VisualStudio.Shell.DialogPage>適切なコンバーターがあるか、構造体または適切なコンバーターのプロパティに拡張できる配列にあるプロパティがサポートされます。 コンバーターの一覧は、次を参照してください。、<xref:System.ComponentModel>名前空間。  
  
6.  プロジェクトをビルドし、デバッグを開始します。  
  
7.  Visual Studio の実験用インスタンスで、**ツール**ボタンをクリックし**オプション**します。  
  
     左側のウィンドウに表示されます**My Category**します。 (オプションのカテゴリが一覧に表示をアルファベット順に一覧の下半分について表示します。)開いている**My Category**順にクリックします**マイのグリッド ページ**します。右側のウィンドウで、オプションのグリッドが表示されます。 プロパティのカテゴリは**My Options**、プロパティ名は**マイ整数オプション**します。 プロパティの説明、**マイ整数オプション**ウィンドウの下部に表示されます。 別のものに 256 の初期値から値を変更します。 をクリックして**OK**を閉じてから開き**マイのグリッド ページ**。 新しい値が引き続き発生することを確認できます。  
  
     オプション ページも Visual Studio のクイック起動で使用できます。 IDE の右上隅の [クイック起動] ウィンドウで次のように入力します。 **My Category**とわかります**My Category に個人用のグリッド ページ]-> [** ドロップダウンに表示します。  
  
## <a name="create-a-tools-options-custom-page"></a>カスタム ツール オプション ページを作成します。  
 このセクションでは、カスタム UI を使用したツール オプション ページを作成します。 表示し、プロパティの値を変更するには、このページを使用します。  
  
1.  開く、 *MyToolsOptionsPackage*コード エディターでファイル。  
  
2.  次の追加ステートメントを使用します。  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  追加、`OptionPageCustom`クラス、直前に、`OptionPageGrid`クラス。 新しいクラスを派生`DialogPage`します。  
  
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
  
5.  2 つ目の適用<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>VSPackage クラスにします。 この属性は、オプションのカテゴリとオプションのページ名、クラスを割り当てます。  
  
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
  
6.  新しい追加**ユーザー コントロール**MyUserControl をという名前をプロジェクトにします。  
  
7.  追加、 **TextBox**コントロールをユーザー コントロール。  
  
     **プロパティ**ウィンドウのツールバーで、をクリックして、**イベント**ボタンをクリックし、ダブルクリック、**まま**イベント。 新しいイベント ハンドラーが表示されます、 *MyUserControl.cs*コード。  
  
8.  追加パブリック`OptionsPage`フィールド、`Initialize`オプションを設定するイベント ハンドラーの値テキスト ボックスの内容を更新し、コントロール クラスにメソッド。  
  
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
  
     `optionsPage`フィールドは、親への参照を保持`OptionPageCustom`インスタンス。 `Initialize`メソッドが表示されます`OptionString`で、 **TextBox**します。 イベント ハンドラーの現在の値を書き込みます、 **テキスト ボックス**を`OptionString`リーフを集中すると、 **テキスト ボックス**です。  
  
9. パッケージのコード ファイルでのオーバーライドを追加、`OptionPageCustom.Window`プロパティを`OptionPageCustom`クラスを作成、初期化、およびのインスタンスを返す`MyUserControl`します。 クラスは、次のようになります。  
  
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
  
11. 実験用インスタンスでは、次のようにクリックします。**ツール** > **オプション**します。  
  
12. 検索**マイ カテゴリ**し **、カスタム ページ**します。  
  
13. 値を変更**なければ**します。 をクリックして**OK**を閉じてから開き**カスタム ページの マイ**。 新しい値が保存されることを確認できます。  
  
## <a name="access-options"></a>アクセス オプション  
 このセクションでは、関連付けられたツール オプション ページをホストする VSPackage からオプションの値を取得します。 任意のパブリック プロパティの値を取得する、同じ手法を使用できます。  
  
1.  パッケージのコード ファイルでというパブリック プロパティを追加**OptionInteger**を**MyToolsOptionsPackage**クラス。  
  
    ```csharp  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     このコードは呼び出して<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>を作成または取得、`OptionPageGrid`インスタンス。 `OptionPageGrid` 呼び出し<xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A>オプションでは、パブリック プロパティを読み込めません。  
  
2.  という名前のカスタム コマンド項目テンプレートを追加するようになりました**MyToolsOptionsCommand**値を表示します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#** > **機能拡張**選択と**カスタム コマンド**。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名を変更して*MyToolsOptionsCommand.cs*します。  
  
3.  *MyToolsOptionsCommand*ファイルで、コマンドの本文を置換`ShowMessageBox`を次のメソッド。  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  プロジェクトをビルドし、デバッグを開始します。  
  
5.  実験用インスタンスでは、上、**ツール** メニューのをクリックして**呼び出す MyToolsOptionsCommand**します。  
  
     メッセージ ボックスの現在の値を表示する`OptionInteger`します。  
  
## <a name="see-also"></a>関連項目  
 [オプションと [オプション] ページ](../extensibility/internals/options-and-options-pages.md)
