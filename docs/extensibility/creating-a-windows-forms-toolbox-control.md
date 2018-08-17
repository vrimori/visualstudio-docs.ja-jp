---
title: ツールボックス コントロールをフォーム、Windows の作成 |Microsoft Docs
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
ms.openlocfilehash: b4f23cae01c9356da26c42ca299a6ac6bb7c190f
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498712"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Windows フォーム ツールボックス コントロールを作成します。
Visual Studio 機能拡張ツール (VS SDK) に含まれている Windows フォーム ツールボックス コントロールの項目テンプレートが自動的に追加するコントロールを作成できます。、**ツールボックス**、拡張機能がインストールされている場合。 このトピックでは、他のユーザーに配布できる単純なカウンター コントロールを作成するテンプレートを使用する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="create-a-windows-forms-toolbox-control"></a>Windows フォーム ツールボックス コントロールを作成します。  
 Windows フォーム ツールボックス コントロール テンプレートは、未定義のユーザー コントロールを作成し、すべてのコントロールを追加するために必要な機能を提供、**ツールボックス**します。  
  
### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Windows フォーム ツールボックス コントロールでの拡張機能を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`MyWinFormsControl`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#** > **Extensibility**します。  
  
2.  プロジェクトが開いたら、追加、 **Windows フォーム ツールボックス コントロール**という名前の項目テンプレート`Counter`します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#** > **拡張**選択**Windows フォーム ツールボックス コントロール**  
  
3.  ユーザー コントロールが追加されます、 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>にコントロールを配置する、**ツールボックス**、および**Microsoft.VisualStudio.ToolboxControl**展開用の VSIX マニフェストでアセット エントリ。  
  
### <a name="build-a-user-interface-for-the-control"></a>コントロールのユーザー インターフェイスを作成します。  
 `Counter`コントロールには、2 つの子コントロールが必要です。<xref:System.Windows.Forms.Label>現在のカウントを表示して、<xref:System.Windows.Forms.Button>カウントを 0 にリセットします。 その他の子コントロールは必要ありませんので、呼び出し元プログラムで、カウンターをインクリメントします。  
  
#### <a name="to-build-the-user-interface"></a>ユーザー インターフェイスを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ダブルクリックして*Counter.cs*デザイナーで開きます。  
  
2.  削除、**ここをクリックします。** Windows フォーム ツールボックス コントロールの項目テンプレートを追加するときに、既定で含まれるボタンをクリックします。  
  
3.  **ツールボックス**、ドラッグ、`Label`コントロールをクリックし、`Button`下にあるコントロールをデザイン画面。  
  
4.  150 に全体的なユーザー コントロールのサイズ、50 の (ピクセル単位) とサイズ変更、ボタン コントロール、50 を 20 ピクセルです。  
  
5.  **プロパティ**ウィンドウ、デザイン サーフェイス上のコントロールの次の値を設定します。  
  
    |コントロール|プロパティ|[値]|  
    |-------------|--------------|-----------|  
    |`Label1`|**[テキスト]**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**[テキスト]**|リセット|  
  
### <a name="code-the-user-control"></a>ユーザー コントロールのコード  
 `Counter`コントロールは、カウンターがインクリメントされるたびに発生するイベント、カウンターをインクリメントするメソッドを公開、**リセット**ボタン、および現在のカウント、表示テキスト、および表示するかどうかを格納する 3 つのプロパティ非表示にするか、**リセット**ボタンをクリックします。 `ProvideToolboxControl`属性のどの場所を指定します、**ツールボックス**、`Counter`コントロールが表示されます。  
  
#### <a name="to-code-the-user-control"></a>ユーザー コントロールをコーディングするには  
  
1.  コード ウィンドウで開き、その load イベント ハンドラーにフォームをダブルクリックします。  
  
2.  イベント ハンドラー メソッドの上のコントロール クラスで、カウンターの値と、次の例に示すように表示されるテキストを格納する文字列を格納する整数を作成します。  
  
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
  
     呼び出し元はこれらのプロパティを取得および設定、カウンターの表示テキスト、または非表示にアクセスできる、**リセット**ボタンをクリックします。 呼び出し元が読み取り専用の現在の値を取得できます`Value`プロパティが直接設定できない値。  
  
4.  次のコードを配置、`Load`コントロールのイベント。  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     設定、**ラベル**内のテキスト、<xref:System.Windows.Forms.UserControl.Load>イベントには、その値が適用される前にターゲット プロパティが有効になります。 設定、**ラベル**コンス トラクター内のテキストが空になる**ラベル**します。  
  
5.  カウンターをインクリメントする次のパブリック メソッドを作成します。  
  
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
  
7.  ダブルクリックしてデザイン ビューに戻る、**リセット**を生成するボタン、`btnReset_Click`イベント ハンドラーをクリックし、次の例に示すように入力します。  
  
    ```csharp  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  クラスの定義のすぐ上で、`ProvideToolboxControl`属性宣言から最初のパラメーターの値を変更`"MyWinFormsControl.Counter"`に`"General"`します。 これにより、 **[ツールボックス]** のコントロールをホストする項目グループの名前が設定されます。  
  
     次の例では、 `ProvideToolboxControl` の属性と、調整されたクラス定義を示しています。  
  
    ```csharp  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="test-the-control"></a>コントロールをテストします。  
 テストする、**ツールボックス**制御、まず開発環境でテストし、コンパイル済みのアプリケーションでテストします。  
  
#### <a name="to-test-the-control"></a>コントロールをテストするには  
  
1.  **F5**キーを押します。  
  
     これは、プロジェクトをビルドし、インストールされているコントロールが Visual Studio の 2 つ目の実験用インスタンスを開きます。  
  
2.  Visual Studio の実験用インスタンスを作成、 **Windows フォーム アプリケーション**プロジェクト。  
  
3.  **ソリューション エクスプ ローラー**、ダブルクリックして*Form1.cs*がまだ開いていない場合、デザイナーで開きます。  
  
4.  **ツールボックス**、`Counter`でコントロールを表示するか、**全般**セクション。  
  
5.  ドラッグ、`Counter`をフォームに制御し、それを選択します。 `Value`、 `Message`、および`ShowReset`でプロパティが表示されます、**プロパティ**ウィンドウから継承されるプロパティと共に<xref:System.Windows.Forms.UserControl>します。  
  
6.  `Message` プロパティを `Count:` に設定します。  
  
7.  ドラッグ、<xref:System.Windows.Forms.Button>をフォームに制御し、ボタンの名前とテキストのプロパティを設定し、`Test`します。  
  
8.  ボタンをダブルクリックして開く*Form1.cs*でコード ビューとクリック ハンドラーを作成します。  
  
9. クリック ハンドラーに、呼び出す`counter1.Increment()`します。  
  
10. コンス トラクター関数の呼び出しの後で`InitializeComponent`、型`counter1``.``Incremented +=`押します**タブ**2 回です。  
  
     Visual Studio フォーム レベルのハンドラーの生成、`counter1.Incremented`イベント。  
  
11. 強調表示、`Throw`ステートメント型、イベント ハンドラーで`mbox`、しキーを押します**タブ**セットアップ コード スニペットからメッセージ ボックスを生成するには、2 回です。  
  
12. 次の行に次のコードを追加`if` / `else`ブロックの表示を設定する、**リセット**ボタンをクリックします。  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. **F5**キーを押します。  
  
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
 ビルドする場合は、**ツールボックス**コントロール、Visual Studio がという名前のファイルを作成する*ProjectName.vsix*で、* \bin\debug\*プロジェクトのフォルダー。 アップロードすることで、制御を展開することができます、 *.vsix*ファイルは、ネットワークまたは Web サイトにします。 ユーザーが開いたとき、 *.vsix*ファイル、コントロールがインストールされ、Visual Studio に追加**ツールボックス**ユーザーのコンピューターにします。 または、アップロード、 *.vsix*ファイルを[Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトのユーザーがで参照して検索できるように、**ツール** >  **拡張機能と更新**ダイアログ。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [WPF ツールボックス コントロールを作成します。](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Windows フォーム コントロール開発の基礎](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)