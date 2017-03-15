---
title: "チュートリアル: WPF ツールボックス コントロールの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "toolbox"
  - "WPF"
ms.assetid: 8223c06e-f327-4778-8709-e0cc7eae2c78
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# チュートリアル: WPF ツールボックス コントロールの作成
Visual Studio SDK に含まれている WPF ツールボックス コントロールのテンプレートでは、Windows Presentation Foundation \(WPF\) コントロールを作成できます。このコントロールは、拡張機能をインストールするときに、自動的に **\[ツールボックス\]** に追加されます。 このチュートリアルでは、他のユーザーに配布できるカウンター コントロールを、テンプレートを使用して作成する方法について説明します。  
  
## 必須コンポーネント  
 このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## Visual Studio の WPF ツールボックス コントロール テンプレートの検索  
 WPF ツールボックス コントロール テンプレートは、**\[新しいプロジェクト\]** ダイアログ ボックスの **\[Visual Studio にインストールされたテンプレート\]** にある、次の場所で使用できます。  
  
-   **\[Visual Basic\]** の **\[拡張機能\]**。 プロジェクト言語は Visual Basic です。  
  
-   **\[Visual C\#\]** の **\[拡張機能\]**。 プロジェクト言語は C\# です。  
  
## WPF ツールボックス コントロール プロジェクトの作成  
 WPF ツールボックス コントロール テンプレートでは、未定義のユーザー コントロールを作成できます。また、**\[ツールボックス\]** にコントロールを追加するために必要な機能が、すべて備えられています。  
  
#### プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[Visual Studio にインストールされたテンプレート\]** で、使用するプログラミング言語のノードをクリックして、**\[拡張機能\]** を選択します。 プロジェクトの種類の一覧で、**\[WPF ツールボックス コントロール\]** を選択します。  
  
3.  **\[名前\]** ボックスに、プロジェクトの名前を入力します。 \(このチュートリアルでは、名前 `Counter` を使用します\)。**\[OK\]** をクリックします。  
  
     これは、ユーザー コントロール、**\[ツールボックス\]** にコントロールを配置する属性、および展開用の VSIX マニフェストを含むソリューションを作成します。**\[名前\]** ボックスでは、ソリューションの名前と名前空間の名前を設定しますが、**\[ツールボックス\]** に表示されるコントロールの名前は設定しません。 この名前は、チュートリアルの後半で設定します。  
  
### コントロールのユーザー インターフェイスの構築  
 `Counter` コントロールには、3 つの子コントロールが必要になります。テキストと現在のカウントを表示する、2 つの <xref:System.Windows.Controls.Label> コントロールと、カウントを 0 にリセットする <xref:System.Windows.Controls.Button> コントロールです。 ホスト アプリケーションがプログラムでカウンターをインクリメントするため、これら以外の子コントロールは必要ありません。  
  
##### ユーザー インターフェイスを作成するには  
  
1.  **\[ソリューション エクスプローラー\]** で ToolboxControl.cs をダブル クリックします。ToolboxControl.cs がデザイナーで開きます。  
  
     デザイナーに、<xref:System.Windows.Controls.Button> コントロールを含む <xref:System.Windows.Controls.Grid> コントロールが表示されます。  
  
2.  <xref:System.Windows.Controls.Grid> コントロールを選択し、グリッドの上部と左側に表示される青いバーをクリックして、グリッドを 2 行と 2 列に分割します。  
  
3.  グリッド上部の行の各セルへ、**\[ツールボックス\]** から <xref:System.Windows.Controls.Label> コントロールをドラッグします。  
  
     この時点で、グリッド上に要素を配置してコントロールのレイアウトを設定できます。 代わりに、テキストに合わせてコントロールのサイズが動的に変わるように、Extensible Application Markup Language \(XAML\) を直接編集することもできます。  
  
4.  **\[XAML\]** ウィンドウで、`RowDefinition` 要素の高さと `ColumnDefinition` 要素の幅を `"auto"` に設定します。  
  
5.  次の例のように、ボタンと 2 個のラベルのマークアップを編集します。  
  
     [!code-xml[ToolboxControlWPF#11](../misc/codesnippet/Xaml/walkthrough-creating-a-wpf-toolbox-control_1.xaml)]  
  
     `Grid.Row` 属性と `Grid.Column` 属性は、グリッド上の要素の位置を設定します。 ボタンの `Grid.ColumnSpan` 属性は、最初の列がボタンの幅とは関係なくサイズ変更できるようにします。  
  
     `{Binding}` 構文を使用して、ラベルの `Content` 属性をプロパティにバインドします。このプロパティは、このチュートリアルの後半で定義します。  
  
### ユーザー コントロールのコーディング  
 `Counter` コントロールは、カウンターをインクリメントするメソッド、カウンターがインクリメントされると発生するイベント、および `Reset` ボタンを公開します。また、現在のカウント、表示テキスト、および `Reset` ボタンの表示または非表示の状態を格納するための、3 つのプロパティも公開します。`ProvideTolboxControl` 属性は、**\[ツールボックス\]** のどの場所に `Counter` コントロールが表示されるかを判断します。  
  
 このコントロールは、Windows フォーム コントロールの記述と同じ方法、つまり、イベント ハンドラーとパブリック メソッドを使用して、ラベルのコンテンツを設定する方法で記述できます。 ただし WPF では、コード内で XAML 要素の属性をプロパティに直接バインドするように、コントロールのデータ コンテキストを設定できます。 このモデルは、コア機能をコントロールのユーザー インターフェイス \(UI\) から分離するための、抽象化のレイヤーも提供します。  
  
 このチュートリアルでは、データ モデルのクラスを作成する方法と、コントロールのデータ コンテキストをデータ モデルにバインドする方法を示します。  
  
##### データ モデルを作成するには  
  
1.  ボタンをダブルクリックしてコード ウィンドウを開きます。  
  
2.  ファイルの先頭に、<xref:System.ComponentModel> 名前空間の `using` ディレクティブを追加します。  
  
3.  クラスの生成後に、パブリック クラスを作成して、データ コンテキストを定義します。  
  
     [!code-cs[ToolboxControlWPF#01](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_2.cs)]  
  
     このクラスは、XAML 要素を定義されたプロパティにバインドする <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装します。  
  
4.  <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスの宣言を右クリックし、**\[インターフェイスの実装\]** をクリックして、**\[インターフェイスの実装\]** を再度クリックします。  
  
     Visual Studio により、`PropertyChanged` イベントが宣言されます。  
  
5.  イベントの宣言後に、次に示すプライベート メソッドを作成して、イベントを発生させます。  
  
     [!code-cs[ToolboxControlWPF#02](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_3.cs)]  
  
6.  コントロールの 2 つのラベルの値を保持するために、次に示すプライベート フィールドとパブリック プロパティを作成します。  
  
     [!code-cs[ToolboxControlWPF#03](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_4.cs)]  
  
     `PropertyChanged` イベントが発生することにより、バインドされたコントロールのコンテンツを更新する XAML バインディングが起きます。 プロパティを `public` に設定すると、設定されたプロパティはデザイナーで使用できますが、このデータ コンテキストにバインドされない限り、そのプロパティを他のプログラムで使用することはできません。  
  
 データ モデルの作成が終了すると、コントロールの分離コード機能を実装できます。  
  
##### コントロールを実装するには  
  
1.  コントロールを実装する部分クラスの定義でクラス名を右クリックし、**\[リファクター\]**、**\[名前の変更\]** の順にクリックして、クラス名を `Counter` に変更します。 この名前は、拡張機能がインストールされると **\[ツールボックス\]** に表示される名前です。  
  
2.  すぐに、クラス定義の上、`ProvideToolboxControl` 属性の宣言内で、最初のパラメーターの値を `"Counter"` から `"General"` に変更します。 これにより、**\[ツールボックス\]** のコントロールをホストする項目グループの名前が設定されます。  
  
     次の例では、`ProvideToolboxControl` の属性と、調整されたクラス定義を示しています。  
  
     [!code-cs[ToolboxControlWPF#04](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_5.cs)]  
  
3.  コントロールのデータ コンテキストを保持するプライベート フィールドを作成し、次の例に示すように、コンストラクターでデータ コンテキストを `MyDataModel` クラスに割り当てます。  
  
     [!code-cs[ToolboxControlWPF#05](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_6.cs)]  
  
4.  次のパブリック プロパティを作成して、`Text` プロパティと `Count` プロパティをデータ コンテキストからミラー化します。  
  
     [!code-cs[ToolboxControlWPF#06](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_7.cs)]  
  
     これらのプロパティは、コントロールを含むすべてのアプリケーションでデータ コンテキストからのコンテンツを使用できるようにします。  
  
5.  カウンターをインクリメントするパブリック メソッドを作成し、ホストするアプリケーションを通知するイベントを作成します。  
  
     [!code-cs[ToolboxControlWPF#07](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_8.cs)]  
  
6.  次に示すように、`Reset` ボタンのクリック ハンドラーを実装します。  
  
     [!code-cs[ToolboxControlWPF#08](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_9.cs)]  
  
7.  次のパブリック プロパティを追加して、`Reset` ボタンを表示または非表示にします。  
  
     [!code-cs[ToolboxControlWPF#09](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_10.cs)]  
  
## コントロールのテスト  
 **\[ツールボックス\]** のコントロールをテストする場合は、まず開発環境でコントロールをテストし、その後で、ホストするアプリケーションでテストします。  
  
#### コントロールをテストするには  
  
1.  F5 キーを押します。  
  
     これはプロジェクトを構築し、コントロールがインストールされた Visual Studio の 2 つ目のインスタンスを開きます。  
  
2.  Visual Studio の新しいインスタンスで、WPF アプリケーション プロジェクトを作成します。  
  
3.  **\[ソリューション エクスプローラー\]** で MainWindow.xaml をダブル クリックします。MainWindow.xaml がデザイナーで開きます。  
  
4.  **\[ツールボックス\]** の **\[全般\]** セクションから、**Counter** コントロールをフォームにドラッグして選択します。  
  
     `Text` プロパティと `ShowReset` プロパティが、<xref:System.Windows.Controls.UserControl> から継承されたその他のプロパティと一緒に、**\[プロパティ\]** ウィンドウに表示されます。`Count` プロパティは読み取り専用のため、表示されません。  
  
5.  `Text` プロパティの値を変更します。  
  
     デザイナーに表示されるラベルのテキストを変更します。  
  
6.  `ShowReset` プロパティを `Hidden` に設定し、次に設定を `Visible` に戻します。  
  
     コントロール上の `Reset` ボタンが非表示になり、再度表示されます。  
  
7.  <xref:System.Windows.Controls.Button> コントロールをフォームにドラッグし、このコントロールの `Content``` 属性を `Test` に設定します。次に、ボタンをダブルクリックして、そのクリック ハンドラーをコード ビューで開きます。  
  
8.  クリック ハンドラーを実装して、コントロールの `Increment` メソッドを呼び出します。  
  
     [!code-cs[ToolboxControlWPF#21](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_11.cs)]  
  
9. コンストラクター関数内で、`InitializeComponent` の呼び出しの後に `counter1.Implemented +=` と記述し、TAB キーを 2 回押して `Counter.Incremented` イベントのハンドラーを生成します。  
  
10. 次の例に示すように、新しいハンドラーを実装します。  
  
     [!code-cs[ToolboxControlWPF#22](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_12.cs)]  
  
11. F5 キーを押します。  
  
     WPF アプリケーションが開きます。  
  
12. **\[テスト\]** をクリックします。  
  
     カウンターがインクリメントし、ボタンの色が少し薄くなります。  
  
13. さらに 4 回、**\[テスト\]** をクリックします。  
  
     カウンターがインクリメントします。ボタンの色はさらに薄くなり、やがて表示が消えます。 ボタンのあった場所をクリックし続けると、カウンターはインクリメントし続けます。  
  
14. **\[リセット\]** をクリックします。  
  
     カウンターが **0** にリセットされます。  
  
## 次の手順  
 **\[ツールボックス\]** のコントロールを構築すると、Visual Studio によって、プロジェクトの \\bin\\debug\\ フォルダーに *プロジェクト名*.vsix という名前のファイルが作成されます。 コントロールは、.vsix ファイルをネットワークや Web サイトにアップロードすることで展開できます。 この .vsix ファイルをユーザーが開くと、コントロールがインストールされ、Visual Studio の **\[ツールボックス\]** に追加されます。 また、[Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトに .vsix ファイルをアップロードした場合も、ユーザーは**拡張機能マネージャー**で参照して、.vsix ファイルを見つけることができます。  
  
## 参照  
 [ツールボックスの拡張](../misc/extending-the-toolbox.md)   
 [Windows フォームのツールボックス コントロールの作成](../extensibility/creating-a-windows-forms-toolbox-control.md)   
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)   
 [WPF デザイナーでのコントロールの操作](http://msdn.microsoft.com/ja-jp/c6235492-b10d-4c3c-ba67-6b6a545faee1)   
 [コントロールの作成の概要](../Topic/Control%20Authoring%20Overview.md)