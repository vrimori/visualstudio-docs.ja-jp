---
title: "チュートリアル: 候補の表示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] - 新しいステートメント入力候補"
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 36
caps.handback.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
---
# チュートリアル: 候補の表示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

入力候補を提供する識別子を定義して、入力候補のセッションをトリガーして、言語に対応したステートメント入力候補を実装できます。 言語サービスのコンテキストでステートメント入力候補を定義、独自のファイル名拡張子とコンテンツの種類を定義およびその型だけの完了を表示できますか、既存のコンテンツの種類の完了を開始することができます\-たとえば、「プレーン テキスト」です。 このチュートリアルでは、テキスト ファイルのコンテンツ タイプは、「プレーン テキスト」コンテンツ タイプの入力候補をトリガーする方法を示します。 「テキスト」コンテンツの種類は、すべての他のコンテンツの種類、コードや XML ファイルなどの先祖です。  
  
 ステートメント入力候補は、通常の特定の文字を入力してトリガー\-などによって、"using"のような識別子の先頭を入力します。 通常には選択範囲をコミットする space キーを押す、タブ、または Enter キーを押すと非表示です。 キー入力のコマンド ハンドラーを使用して文字を入力することによってトリガーされる IntelliSense 機能を実装することができます \(、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイス\) およびハンドラー プロバイダーを実装する、 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> インターフェイスです。 完了に参加している id の一覧では、入力候補のソースを作成するには、実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> インターフェイスと完了の同期元プロバイダー \(、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> インターフェイス\)。 プロバイダーは、Managed Extensibility Framework \(MEF\) コンポーネントの部分です。 サービスとブローカー、ソースおよびコント ローラー クラスをエクスポートおよびインポートを担当しているなど、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, 、テキスト バッファー内のナビゲーションを有効にして、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, 、入力候補のセッションをトリガーします。  
  
 このチュートリアルでは、ハード コーディングされた一連の識別子の入力候補を実装する方法を示します。 完全な実装で、言語サービスと language のドキュメントがそのコンテンツを提供する担当します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## MEF プロジェクトを作成します。  
  
#### MEF プロジェクトを作成するには  
  
1.  C\# の場合は、VSIX プロジェクトを作成します。 \(で、 **新しいプロジェクト** ダイアログで、 **Visual c\#\/機能拡張**, 、し **VSIX プロジェクト**.\) ソリューションの名前 `CompletionTest`します。  
  
2.  エディターの分類子の項目テンプレートをプロジェクトに追加します。 詳細については、「[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)」を参照してください。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  次の参照をプロジェクトに追加し、そのことを確認して **CopyLocal** に設定されている `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## 入力候補のソースの実装  
 入力候補のソースは、識別子のセットを収集し、ユーザーは、識別子の最初の文字などの補完トリガーを入力すると、補完ウィンドウに、コンテンツを追加します。 この例では、識別子とその説明はハード コードで、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> メソッドです。 ほとんどの実際の用途では、入力候補一覧を設定するのにトークンを取得するのに、言語のパーサーを使用します。  
  
#### 入力候補のソースを実装するには  
  
1.  クラス ファイルを追加し、名前 `TestCompletionSource`します。  
  
2.  これらのインポートを追加します。  
  
     [!code-cs[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  クラス宣言を変更して `TestCompletionSource` を実装 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-cs[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  テキスト バッファーとの一覧では、ソース プロバイダーのプライベート フィールドを追加 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> オブジェクト \(入力候補のセッションに参加する識別子に対応しています\)。  
  
     [!code-cs[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  同期元プロバイダーとバッファーを設定するコンス トラクターを追加します。`TestCompletionSourceProvider` クラスは後の手順で定義します。  
  
     [!code-cs[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> コンテキストで提供するメソッドを入力候補を含む入力候補のセットを追加しています。 各入力候補のセットには一連の <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 入力候補、補完ウィンドウのタブに対応しています。 \(Visual Basic プロジェクトでは、入力候補ウィンドウのタブの名前は **共通** と **すべて**.\) FindTokenSpanAtPosition メソッドは、次の手順で定義されます。  
  
     [!code-cs[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  次のメソッドを使用して、カーソルの位置から現在の単語を検索します。  
  
     [!code-cs[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  実装、 `Dispose()` メソッド。  
  
     [!code-cs[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## 入力候補のソースのプロバイダーを実装します。  
 入力候補のソースのプロバイダーは、入力候補のソースをインスタンス化する MEF コンポーネント部分です。  
  
#### 入力候補のソースのプロバイダーを実装するには  
  
1.  という名前のクラスを追加 `TestCompletionSourceProvider` を実装する <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>です。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 「プレーン テキスト」の <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 「テストの完了」のです。  
  
     [!code-cs[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  インポート、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, を使用して、入力候補のソースの現在の単語を検索します。  
  
     [!code-cs[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> 入力候補のソースをインスタンス化するメソッドです。  
  
     [!code-cs[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## 完了コマンド ハンドラーのプロバイダーを実装します。  
 完了コマンド ハンドラーのプロバイダーがから派生した、 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, 、テキスト ビューの作成イベントをリスンし、ビューに変換する、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>\-Visual Studio シェルのコマンドのチェーンをコマンドの追加を有効にする: に、 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。 このクラスは、MEF エクスポートであるためには、コマンド ハンドラー自体が必要とするサービスをインポートするのにも使用できます。  
  
#### 完了コマンド ハンドラーのプロバイダーを実装するには  
  
1.  という名前のファイルを追加 `TestCompletionCommandHandler`します。  
  
2.  次の using ステートメントを追加します。  
  
     [!code-cs[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  という名前のクラスを追加 `TestCompletionHandlerProvider` を実装する <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>です。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 「トークンの完了ハンドラー」の <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 「プレーン テキスト」の <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> の <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>です。  
  
     [!code-cs[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  インポート、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, からの変換を有効にする、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> に、 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, 、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, 、および <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> Visual Studio の標準のサービスにアクセスできるようにします。  
  
     [!code-cs[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  実装、 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> コマンド ハンドラーのインスタンスを作成する方法です。  
  
     [!code-cs[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## コマンドの完了ハンドラーを実装します。  
 実装する必要がありますので、ステートメント入力候補がキーストロークによってトリガーされると、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスを受け取り、トリガー、コミット、および入力候補のセッションを破棄するキーボード操作を処理します。  
  
#### コマンドの完了ハンドラーを実装するには  
  
1.  という名前のクラスを追加 `TestCompletionCommandHandler` を実装する <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-cs[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  次のコマンド ハンドラーが \(これに合格するコマンドは、\)、テキスト ビュー、\(これにより、さまざまなサービスへのアクセス\)、コマンド ハンドラー プロバイダーには、プライベート フィールドを追加し、入力候補セッション。  
  
     [!code-cs[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  テキスト ビューとプロバイダーのフィールドを設定し、コマンドのチェーンにコマンドを追加するコンス トラクターを追加します。  
  
     [!code-cs[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> に沿ってコマンドを渡すことによってメソッド。  
  
     [!code-cs[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドを実装します。 このメソッドは、キー入力を受け取る、次のいずれかにください。  
  
    -   文字バッファーに書き込まれると、トリガー、または完了をフィルター処理を許可します。 \(印刷文字実行します。\)  
  
    -   完了すると、コミットしますが、バッファーに書き込まれる文字を許可されていません。 \(空白、タブ、および Enter そうときに入力候補のセッションが表示されます。\)  
  
    -   次のハンドラー渡されるコマンドを許可します。 \(その他のコマンドです。\)  
  
     このメソッドが UI を表示するために呼び出す <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> automation コンテキストで呼び出されていないことを確認します。  
  
     [!code-cs[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  このコードは、入力候補のセッションをトリガーするプライベート メソッドを示します。  
  
     [!code-cs[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  次の例からアンサブスク ライブするプライベート メソッド、 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> イベント。  
  
     [!code-cs[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## コードのビルドとテスト  
 このコードをテストするには、CompletionTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### ビルドし、CompletionTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、"add"という単語を含むいくつかのテキストを入力します。  
  
4.  入力すると最初に"a"とし、"d"、"addition"と「適応」を含むリストが表示されます。 加算が選択されていることに注意してください。 もう 1 つの"d"を入力すると、この一覧はのみ"addition"、現在選択されているを含める必要があります。 Space キーを押す、タブ、または Enter キーを押す"addition"をコミットまたは esc キーまたはその他の任意のキーを入力して一覧を消すことができます。  
  
## 参照  
 [チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)