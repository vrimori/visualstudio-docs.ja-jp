---
title: Windows を作成するフォームのツールボックス コントロール |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a7d5bae07d3596902f94417cda20c3d40feed2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-windows-forms-toolbox-control"></a>Windows フォームのツールボックス コントロールの作成
Visual Studio 機能拡張ツール (VS SDK) に含まれている Windows フォームのツールボックス コントロールの項目テンプレートが自動的に追加するコントロールを作成することができます、**ツールボックス**拡張機能がインストールされている場合。 このトピックでは、他のユーザーに配布できるカウンターの単純なコントロールを作成するテンプレートを使用する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Windows フォームのツールボックス コントロールの作成  
 Windows フォームのツールボックス コントロール テンプレートが定義されていないユーザー コントロールを作成し、すべてのコントロールを追加する必要がある機能を提供、**ツールボックス**です。  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Windows フォームのツールボックス コントロールでの拡張機能を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`MyWinFormsControl`です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  プロジェクトを開いたら、追加、 **Windows フォームのツールボックス コントロール**という名前の項目テンプレート`Counter`です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択**Windows フォームのツールボックス コントロール**  
  
3.  ユーザー コントロールを追加、 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>でコントロールを配置する、**ツールボックス**、および**Microsoft.VisualStudio.ToolboxControl** VSIX マニフェストの展開のアセット エントリです。  
  
### <a name="building-a-user-interface-for-the-control"></a>コントロールのユーザー インターフェイスの構築  
 `Counter`コントロールには、次の 2 つの子コントロールが必要です。<xref:System.Windows.Forms.Label>を現在の数を表示して、<xref:System.Windows.Forms.Button>カウントを 0 にリセットします。 他の子コントロールは必要ありませんので、呼び出し元プログラムでカウンターをインクリメントします。  
  
##### <a name="to-build-the-user-interface"></a>ユーザー インターフェイスを作成するには  
  
1.  **ソリューション エクスプ ローラー**Counter.cs をデザイナーで開く をダブルクリックします。  
  
2.  削除、「ここをクリックしてください。」 **ボタン**Windows フォームのツールボックス コントロールの項目テンプレートを追加するときに既定で含まれています。  
  
3.  **ツールボックス**、ドラッグ、`Label`制御し、`Button`コントロールの下にあるデザイン画面。  
  
4.  150 に全体的なユーザー コントロールのサイズ、50、50 の (ピクセル単位) と、ボタンのサイズ変更コントロール 20 ピクセルです。  
  
5.  **プロパティ**ウィンドウでは、デザイン画面上のコントロールに次の値を設定します。  
  
    |コントロール|プロパティ|[値]|  
    |-------------|--------------|-----------|  
    |`Label1`|**[テキスト]**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**[テキスト]**|リセット|  
  
### <a name="coding-the-user-control"></a>ユーザー コントロールのコーディング  
 `Counter` コントロールは、カウンターをインクリメントするメソッド、カウンターがインクリメントされると発生するイベント、および `Reset` ボタンを公開します。また、現在のカウント、表示テキスト、および `Reset` ボタンの表示または非表示の状態を格納するための、3 つのプロパティも公開します。 `ProvideToolboxControl`属性内の場所を決定する、**ツールボックス**、`Counter`コントロールが表示されます。  
  
##### <a name="to-code-the-user-control"></a>ユーザー コントロールをコーディングするには  
  
1.  フォームをダブルクリックしてコード ウィンドウで、load イベント ハンドラーを開きます。  
  
2.  イベント ハンドラー メソッドの上のコントロールのクラスに、カウンターの値と、次の例で示すように表示するテキストを格納する文字列を格納する整数を作成します。  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3.  次のパブリック プロパティの宣言を作成します。  
  
    ```csharp  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     呼び出し元がこれらのプロパティを取得し、カウンターの表示テキストを設定しを表示または非表示にアクセスできる、`Reset`ボタンをクリックします。 呼び出し元は、読み取り専用の現在の値を取得できます`Value`プロパティが値を直接設定できません。  
  
4.  次のコードを配置、`Load`コントロールのイベントです。  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     設定、**ラベル**内のテキスト、<xref:System.Windows.Forms.UserControl.Load>イベントには、その値が適用される前に、読み込むターゲット プロパティが有効になります。 設定、**ラベル**コンス トラクター内のテキストは、空になる**ラベル**です。  
  
5.  カウンターをインクリメントするパブリック メソッドを作成します。  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  宣言を追加、`Incremented`コントロール クラスにイベント。  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     呼び出し元は、カウンターの値の変更に応答するには、このイベントにハンドラーを追加することができます。  
  
7.  ダブルクリックしてデザイン ビューに戻り、`Reset`を生成するボタン、`btnReset_Click`イベント ハンドラー、し、次の例で示すように入力します。  
  
    ```csharp  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  クラス定義のすぐ上に、`ProvideToolboxControl`属性の宣言から最初のパラメーターの値を変更`"MyWinFormsControl.Counter"`に`"General"`です。 これにより、 **[ツールボックス]**のコントロールをホストする項目グループの名前が設定されます。  
  
     次の例では、 `ProvideToolboxControl` の属性と、調整されたクラス定義を示しています。  
  
    ```csharp  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>コントロールのテスト  
 テストする、**ツールボックス**制御、まず開発環境でテストし、コンパイル済みのアプリケーションでテストします。  
  
##### <a name="to-test-the-control"></a>コントロールをテストするには  
  
1.  F5 キーを押します。  
  
     これは、プロジェクトをビルドし、インストールされているコントロールが Visual Studio の 2 番目の実験用インスタンスを開きます。  
  
2.  Visual Studio の実験用インスタンスの作成、 **Windows フォーム アプリケーション**プロジェクト。  
  
3.  **ソリューション エクスプ ローラー**がまだ開いていない場合、デザイナーで開くには、[form1.cs] をダブルクリックします。  
  
4.  **ツールボックス**、`Counter`でコントロールを表示するか、**全般**セクションです。  
  
5.  ドラッグ、`Counter`をフォームに制御し、それを選択します。 `Value`、 `Message`、および`ShowReset`でプロパティが表示されます、**プロパティ**ウィンドウとそのプロパティから継承されている<xref:System.Windows.Forms.UserControl>です。  
  
6.  `Message` プロパティを `Count:` に設定します。  
  
7.  ドラッグ、<xref:System.Windows.Forms.Button>コントロールをフォームとボタンの名前、およびテキストのプロパティを設定して`Test`です。  
  
8.  コード ビューで form1.cs を開き、クリック ハンドラーを作成する ボタンをダブルクリックします。  
  
9. クリック ハンドラーを呼び出して`counter1.Increment()`です。  
  
10. 呼び出しの後に、コンス トラクター関数`InitializeComponent`、型`counter1``.``Incremented +=`タブを 2 回押します。  
  
     Visual Studio でのフォーム レベル ハンドラーを生成、`counter1.Incremented`イベント。  
  
11. 強調表示、`Throw`ステートメント型、イベント ハンドラーで`mbox`、し、メールボックスのコード スニペットからメッセージ ボックスを生成するには、2 回 TAB キーを押します。  
  
12. 次の行では、次の追加`if` / `else`ブロックの表示設定を`Reset`ボタンをクリックします。  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. F5 キーを押します。  
  
     フォームを開きます。 `Counter`コントロールには、次のテキストが表示されます。  
  
     **カウント: 0**  
  
14. **[テスト]**をクリックします。  
  
     カウンターがインクリメントされると Visual Studio は、メッセージ ボックスを表示します。  
  
15. メッセージ ボックスを閉じます。  
  
     **リセット**ボタンは表示されなくなります。  
  
16. をクリックして**テスト**カウンターに到達するまで**5**たびに、メッセージを閉じてボックスします。  
  
     **リセット**が再度表示されるボタンをクリックします。  
  
17. **[リセット]**をクリックします。  
  
     カウンターをリセットする**0**します。  
  
## <a name="next-steps"></a>次の手順  
 **[ツールボックス]** のコントロールを構築すると、Visual Studio によって、プロジェクトの \bin\debug\ フォルダーに *プロジェクト名*.vsix という名前のファイルが作成されます。 コントロールは、.vsix ファイルをネットワークや Web サイトにアップロードすることで展開できます。 コントロールがインストールされ、Visual Studio に追加されたユーザーが、.vsix ファイルを開く、**ツールボックス**ユーザーのコンピューターにします。 探し、.vsix ファイルをアップロードする代わりに、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトのユーザーがで参照して検索できるように、**ツール/拡張機能と更新プログラム**ダイアログ。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [WPF ツールボックス コントロールの作成](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Windows フォーム コントロール開発の基本概念](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)