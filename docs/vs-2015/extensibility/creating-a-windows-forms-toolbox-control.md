---
title: ツールボックス コントロールをフォーム、Windows の作成 |Microsoft Docs
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
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 371fd4269cee5918bd0d0b623eb49e1f709a311d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781713"
---
# <a name="creating-a-windows-forms-toolbox-control"></a>Windows フォーム ツールボックス コントロールの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 機能拡張ツール (VS SDK) に含まれている Windows フォーム ツールボックス コントロールの項目テンプレートが自動的に追加するコントロールを作成できます。、**ツールボックス**、拡張機能がインストールされている場合。 このトピックでは、他のユーザーに配布できる単純なカウンター コントロールを作成するテンプレートを使用する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Windows フォーム ツールボックス コントロールの作成  
 Windows フォーム ツールボックス コントロール テンプレートは、未定義のユーザー コントロールを作成し、すべてのコントロールを追加するために必要な機能を提供、**ツールボックス**します。  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Windows フォーム ツールボックス コントロールでの拡張機能を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`MyWinFormsControl`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  プロジェクトが開いたら、追加、 **Windows フォーム ツールボックス コントロール**という名前の項目テンプレート`Counter`します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択**Windows フォーム ツールボックス コントロール**  
  
3.  ユーザー コントロールが追加されます、 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>にコントロールを配置する、**ツールボックス**、および**Microsoft.VisualStudio.ToolboxControl**展開用の VSIX マニフェストでアセット エントリ。  
  
### <a name="building-a-user-interface-for-the-control"></a>コントロールのユーザー インターフェイスの構築  
 `Counter`コントロールには、2 つの子コントロールが必要です。<xref:System.Windows.Forms.Label>現在のカウントを表示して、<xref:System.Windows.Forms.Button>カウントを 0 にリセットします。 その他の子コントロールは必要ありませんので、呼び出し元プログラムで、カウンターをインクリメントします。  
  
##### <a name="to-build-the-user-interface"></a>ユーザー インターフェイスを作成するには  
  
1.  **ソリューション エクスプ ローラー**デザイナーで開く Counter.cs をダブルクリックします。  
  
2.  "Click Here!"を削除します。 **ボタン**Windows フォーム ツールボックス コントロールの項目テンプレートを追加するときに既定で含まれています。  
  
3.  **ツールボックス**、ドラッグ、`Label`コントロールをクリックし、`Button`下にあるコントロールをデザイン画面。  
  
4.  150 に全体的なユーザー コントロールのサイズ、50 の (ピクセル単位) とサイズ変更、ボタン コントロール、50 を 20 ピクセルです。  
  
5.  **プロパティ**ウィンドウ、デザイン サーフェイス上のコントロールの次の値を設定します。  
  
    |コントロール|プロパティ|[値]|  
    |-------------|--------------|-----------|  
    |`Label1`|**[テキスト]**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**[テキスト]**|リセット|  
  
### <a name="coding-the-user-control"></a>ユーザー コントロールのコーディング  
 `Counter` コントロールは、カウンターをインクリメントするメソッド、カウンターがインクリメントされると発生するイベント、および `Reset` ボタンを公開します。また、現在のカウント、表示テキスト、および `Reset` ボタンの表示または非表示の状態を格納するための、3 つのプロパティも公開します。 `ProvideToolboxControl` 属性は、 **[ツールボックス]** のどの場所に `Counter` コントロールが表示されるかを判断します。  
  
##### <a name="to-code-the-user-control"></a>ユーザー コントロールをコーディングするには  
  
1.  コード ウィンドウで開き、その load イベント ハンドラーにフォームをダブルクリックします。  
  
2.  イベント ハンドラー メソッドの上のコントロール クラスで、カウンターの値と、次の例に示すように表示されるテキストを格納する文字列を格納する整数を作成します。  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3.  次のパブリック プロパティの宣言を作成します。  
  
    ```csharp  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     呼び出し元はこれらのプロパティを取得および設定、カウンターの表示テキスト、または非表示にアクセスできる、`Reset`ボタンをクリックします。 呼び出し元が読み取り専用の現在の値を取得できます`Value`プロパティが直接設定できない値。  
  
4.  次のコードを配置、`Load`コントロールのイベント。  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     設定、**ラベル**内のテキスト、<xref:System.Windows.Forms.UserControl.Load>イベントには、その値が適用される前にターゲット プロパティが有効になります。 設定、**ラベル**コンス トラクター内のテキストが空になる**ラベル**します。  
  
5.  カウンターをインクリメントする次のパブリック メソッドを作成します。  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  宣言を追加、`Incremented`コントロール クラスにイベント。  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     呼び出し元は、カウンターの値の変更に応答するには、このイベントにハンドラーを追加することができます。  
  
7.  ダブルクリックしてデザイン ビューに戻り、`Reset`を生成するボタン、`btnReset_Click`イベント ハンドラーをクリックし、次の例に示すように入力します。  
  
    ```csharp  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  すぐに、クラス定義の上、 `ProvideToolboxControl` 属性の宣言内で、最初のパラメーターの値を `"MyWinFormsControl.Counter"` から `"General"`に変更します。 これにより、 **[ツールボックス]** のコントロールをホストする項目グループの名前が設定されます。  
  
     次の例では、 `ProvideToolboxControl` の属性と、調整されたクラス定義を示しています。  
  
    ```csharp  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>コントロールのテスト  
 テストする、**ツールボックス**制御、まず開発環境でテストし、コンパイル済みのアプリケーションでテストします。  
  
##### <a name="to-test-the-control"></a>コントロールをテストするには  
  
1.  F5 キーを押します。  
  
     これは、プロジェクトをビルドし、インストールされているコントロールが Visual Studio の 2 つ目の実験用インスタンスを開きます。  
  
2.  Visual Studio の実験用インスタンスを作成、 **Windows フォーム アプリケーション**プロジェクト。  
  
3.  **ソリューション エクスプ ローラー**Form1.cs がまだ開いていない場合、デザイナーで開く をダブルクリックします。  
  
4.  **ツールボックス**、`Counter`でコントロールを表示するか、**全般**セクション。  
  
5.  ドラッグ、`Counter`をフォームに制御し、それを選択します。 `Value`、 `Message`、および`ShowReset`でプロパティが表示されます、**プロパティ**ウィンドウから継承されるプロパティと共に<xref:System.Windows.Forms.UserControl>します。  
  
6.  `Message` プロパティを `Count:`に設定します。  
  
7.  ドラッグ、<xref:System.Windows.Forms.Button>をフォームに制御し、ボタンの名前とテキストのプロパティを設定し、`Test`します。  
  
8.  コード ビューで Form1.cs を開き、クリック ハンドラーを作成するボタンをダブルクリックします。  
  
9. クリック ハンドラーに、呼び出す`counter1.Increment()`します。  
  
10. コンス トラクター関数の呼び出しの後で`InitializeComponent`、型`counter1``.``Incremented +=`とタブを 2 回押します。  
  
     Visual Studio フォーム レベルのハンドラーの生成、`counter1.Incremented`イベント。  
  
11. 強調表示、`Throw`ステートメント型、イベント ハンドラーで`mbox`、し、tab キーを押してセットアップ コード スニペットからメッセージ ボックスを生成するには、2 回です。  
  
12. 次の行に次のコードを追加`if` / `else`ブロックの表示を設定する、`Reset`ボタンをクリックします。  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. F5 キーを押します。  
  
     フォームを開きます。 `Counter`コントロールは、次のテキストを表示します。  
  
     **数: 0**  
  
14. **[テスト]** をクリックします。  
  
     カウンターがインクリメントされると Visual Studio には、メッセージ ボックスが表示されます。  
  
15. メッセージ ボックスを閉じます。  
  
     **リセット**ボタンは表示されなくなります。  
  
16. クリックして**テスト**カウンターに到達するまで**5**たびにボックス、メッセージを閉じるします。  
  
     **リセット**が再度表示されるボタンをクリックします。  
  
17. **[リセット]** をクリックします。  
  
     カウンターをリセットする**0**します。  
  
## <a name="next-steps"></a>次の手順  
 **[ツールボックス]** のコントロールを構築すると、Visual Studio によって、プロジェクトの \bin\debug\ フォルダーに *プロジェクト名*.vsix という名前のファイルが作成されます。 コントロールは、.vsix ファイルをネットワークや Web サイトにアップロードすることで展開できます。 コントロールがインストールされ、Visual Studio に追加ユーザーは、.vsix ファイルを開いたら、**ツールボックス**ユーザーのコンピューターにします。 または、.vsix ファイルをアップロードできます、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトのユーザーがで参照して検索できるように、**ツール/拡張機能と更新**ダイアログ。  
  
## <a name="see-also"></a>関連項目  
 [ツールボックスの拡張](../misc/extending-the-toolbox.md)   
 [WPF ツールボックス コントロールの作成](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Windows フォーム コントロール開発の基本概念](http://msdn.microsoft.com/library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)

