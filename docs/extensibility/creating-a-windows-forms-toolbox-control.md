---
title: "ツールボックス コントロールをフォーム、Windows の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 770963e06655c0d4da2946fa7981fd1e4496b7f0
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-windows-forms-toolbox-control"></a>Windows フォームのツールボックス コントロールの作成
Visual Studio 機能拡張ツール (VS SDK) に含まれている Windows フォームのツールボックス コントロールの項目テンプレートを使用して、自動的に追加するコントロールを作成できる、**ツールボックス**拡張機能がインストールされている場合。 このトピックでは、テンプレートを使用して、他のユーザーに配布できる単純なカウンター コントロールを作成する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Windows フォームのツールボックス コントロールの作成  
 Windows フォームのツールボックス コントロールのテンプレートが定義されていないユーザー コントロールを作成し、すべてのコントロールを追加するために必要な機能を提供、**ツールボックス**します。  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Windows フォームのツールボックス コントロールでの拡張機能を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`MyWinFormsControl`です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  プロジェクトを開いたら、追加、 **Windows フォームのツールボックス コントロール**という名前の項目テンプレート`Counter`します。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックして、選択**追加/新しい項目の**です。 **新しい項目の追加**ダイアログ ボックスに移動**Visual c#/機能拡張**選択**Windows フォームのツールボックス コントロール**  
  
3.  ユーザー コントロールを追加、 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>でコントロールを配置する、**ツールボックス**、および**Microsoft.VisualStudio.ToolboxControl**で配置の VSIX マニフェスト アセット エントリ</xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>。  
  
### <a name="building-a-user-interface-for-the-control"></a>コントロールのユーザー インターフェイスの構築  
 `Counter`コントロールが 2 つの子コントロールが必要です。<xref:System.Windows.Forms.Label>を現在の数を表示して、<xref:System.Windows.Forms.Button>カウントを 0 にリセットする</xref:System.Windows.Forms.Button></xref:System.Windows.Forms.Label>。 その他の子コントロールは必要ありませんので、呼び出し元プログラムを使用して、カウンターをインクリメントします。  
  
##### <a name="to-build-the-user-interface"></a>ユーザー インターフェイスを作成するには  
  
1.  **ソリューション エクスプ ローラー**Counter.cs をデザイナーで開く をダブルクリックします。  
  
2.  "Click Here!"を削除します。 **ボタン**Windows フォームのツールボックス コントロールの項目テンプレートを追加するときに既定で含まれています。  
  
3.  **ツールボックス**、ドラッグ、`Label`制御し、`Button`下にあるコントロールのデザイン画面にします。  
  
4.  150 に全体的なユーザー コントロールのサイズを 50 (ピクセル単位)、サイズ変更、ボタンを 50 に制御が 20 ピクセルです。  
  
5.  **プロパティ**ウィンドウでは、デザイン サーフェイス上のコントロールの次の値を設定します。  
  
    |コントロール|プロパティ|値|  
    |-------------|--------------|-----------|  
    |`Label1`|**テキスト**|""|  
    |`Button1`|**名前**|btnReset|  
    |`Button1`|**テキスト**|リセット|  
  
### <a name="coding-the-user-control"></a>ユーザー コントロールのコーディング  
 `Counter` コントロールは、カウンターをインクリメントするメソッド、カウンターがインクリメントされると発生するイベント、および `Reset` ボタンを公開します。また、現在のカウント、表示テキスト、および `Reset` ボタンの表示または非表示の状態を格納するための、3 つのプロパティも公開します。 `ProvideToolboxControl`属性内の場所を決定する、**ツールボックス**、`Counter`コントロールが表示されます。  
  
##### <a name="to-code-the-user-control"></a>ユーザー コントロールをコーディングするには  
  
1.  フォームをダブルクリックしてコード ウィンドウで、load イベント ハンドラーを開きます。  
  
2.  イベントのハンドラー メソッドの上のコントロール クラスでカウンターの値と、次の例で示すように表示するテキストを格納する文字列を格納する整数を作成します。  
  
    ```c#  
    int currentValue;  
    string displayText;  
    ```  
  
3.  次のパブリック プロパティの宣言を作成します。  
  
    ```c#  
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
  
     呼び出し元がこれらのプロパティを取得およびカウンターの表示テキストを設定しを表示または非表示にアクセスできる、 `Reset`  ボタンをクリックします。 呼び出し元は、読み取り専用の現在の値を取得できる`Value`ですが、値を直接設定できません。  
  
4.  次のコードを配置、`Load`コントロールのイベントです。  
  
    ```c#  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     設定、**ラベル**内のテキスト、<xref:System.Windows.Forms.UserControl.Load>イベントにより、ターゲットのプロパティの値が適用される前に読み込めません</xref:System.Windows.Forms.UserControl.Load>。 設定、**ラベル**コンス トラクター内のテキストは、空になる**ラベル**します。  
  
5.  カウンターをインクリメントする次のパブリック メソッドを作成します。  
  
    ```c#  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  宣言を追加、`Incremented`コントロール クラスにイベントです。  
  
    ```c#  
    public event EventHandler Incremented;  
    ```  
  
     呼び出し元は、カウンターの値の変化に対応するこのイベントにハンドラーを追加することができます。  
  
7.  ダブルクリックしてデザイン ビューに戻り、`Reset`を生成する ボタン、`btnReset_Click`イベント ハンドラーし、次の例に示すように入力します。  
  
    ```c#  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  クラス定義のすぐ上で、`ProvideToolboxControl`属性宣言から最初のパラメーターの値を変更`"MyWinFormsControl.Counter"`に`"General"`します。 これにより、 **[ツールボックス]**のコントロールをホストする項目グループの名前が設定されます。  
  
     次の例では、 `ProvideToolboxControl` の属性と、調整されたクラス定義を示しています。  
  
    ```c#  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>コントロールのテスト  
 テストする、**ツールボックス**、管理、開発環境でこれをテストや、コンパイル済みのアプリケーションでテストします。  
  
##### <a name="to-test-the-control"></a>コントロールをテストするには  
  
1.  F5 キーを押します。  
  
     プロジェクトがビルドされ、インストールされているコントロールを含む Visual Studio の&2; つ目の実験用インスタンスを開きます。  
  
2.  Visual Studio の実験用インスタンスの作成、 **Windows フォーム アプリケーション**プロジェクトです。  
  
3.  **ソリューション エクスプ ローラー**が開いていない場合は、デザイナーで開く Form1.cs をダブルクリックします。  
  
4.  **ツールボックス**、`Counter`にコントロールを表示するか、**全般**セクションです。  
  
5.  ドラッグ、`Counter`コントロールがフォーム、および、それを選択します。 `Value`、 `Message`、および`ShowReset`でプロパティが表示されます、**プロパティ** <xref:System.Windows.Forms.UserControl>.</xref:System.Windows.Forms.UserControl>から継承されたプロパティと共にのウィンドウ  
  
6.  `Message` プロパティを `Count:` に設定します。  
  
7.  ドラッグ、<xref:System.Windows.Forms.Button>をフォームに制御し、ボタンの名前とテキストのプロパティを設定`Test`</xref:System.Windows.Forms.Button>。  
  
8.  コード ビューで Form1.cs を開き、クリック ハンドラーを作成する ボタンをダブルクリックします。  
  
9. クリック ハンドラーを呼び出して`counter1.Increment()`します。  
  
10. コンス トラクター関数の呼び出しの後に`InitializeComponent`、型`counter1``.``Incremented +=`し、tab を&2; 回クリックします。  
  
     Visual Studio のフォーム レベルのハンドラーを生成する、`counter1.Incremented`イベントです。  
  
11. 強調表示、`Throw`イベント ハンドラーの種類のステートメント`mbox`、し、tab キーを押してセットアップ コード スニペットからメッセージ ボックスを生成するには、2 回クリックします。  
  
12. 次の行には、次のコードを追加`if` / `else`ブロックの表示を設定する、 `Reset`  ボタンをクリックします。  
  
    ```c#  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. F5 キーを押します。  
  
     フォームを開きます。 `Counter`コントロールは、次のテキストを表示します。  
  
     **カウント: 0**  
  
14. **[テスト]**をクリックします。  
  
     カウンターがインクリメントされるおよび Visual Studio には、メッセージ ボックスが表示されます。  
  
15. メッセージ ボックスを閉じます。  
  
     **リセット**ボタンは表示されなくなります。  
  
16. クリックして**テスト**カウンターに到達するまで**5**たびに、メッセージを閉じるボックスします。  
  
     **リセット**が再度表示されるボタンをクリックします。  
  
17. **[リセット]**をクリックします。  
  
     カウンターがリセット**0**です。  
  
## <a name="next-steps"></a>次の手順  
 **[ツールボックス]** のコントロールを構築すると、Visual Studio によって、プロジェクトの \bin\debug\ フォルダーに *プロジェクト名*.vsix という名前のファイルが作成されます。 コントロールは、.vsix ファイルをネットワークや Web サイトにアップロードすることで展開できます。 コントロールがインストールされているし、Visual Studio に追加されたユーザーは、.vsix ファイルを開いたら、**ツールボックス**ユーザーのコンピューターにします。 .Vsix ファイルをアップロードする代わりに、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトのユーザーが参照によって検出できるように、**ツール/拡張機能と更新プログラム**ダイアログ。  
  
## <a name="see-also"></a>関連項目  
 [ツールボックスを拡張します。](../misc/extending-the-toolbox.md)   
 [WPF ツールボックス コントロールを作成します。](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Windows フォーム コントロール開発の基本概念](http://msdn.microsoft.com/Library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)
