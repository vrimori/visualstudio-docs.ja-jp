---
title: "チュートリアル: ステートメント入力候補の表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d9c3b44bd46c34a864896cbf1002505085be5143
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-statement-completion"></a>チュートリアル: ステートメント入力候補を表示します。
入力候補を提供する識別子を定義して、入力候補のセッションをトリガーして、言語に対応したステートメント入力候補を実装できます。 言語サービスのコンテキストでステートメントの完了を定義、独自のファイル名拡張子とコンテンツの種類を定義してその種類の入力候補を表示したり、既存のコンテンツの種類の完了をトリガーすることができます: たとえば、「プレーン テキスト」です。 このチュートリアルでは、「プレーン テキスト」コンテンツ タイプ、テキスト ファイルのコンテンツの種類の入力候補をトリガーする方法を示します。 「テキスト」コンテンツの種類は、すべての他のコンテンツの種類、コードや XML ファイルなどの先祖です。  
  
 ステートメント入力候補が特定の文字を入力することによってトリガーされる通常 — などによって、"using"など、識別子の先頭を入力します。 通常非表示に選択範囲をコミットする、space キーを押し、タブ、または Enter キーを押します。 文字を入力するキーストロークのコマンド ハンドラーを使用してによってトリガーされる IntelliSense 機能を実装することができます (、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス) およびハンドラー プロバイダーを実装する、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>インターフェイスです。 完了に参加している id のリストである、入力候補ソースを作成するには、実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>インターフェイスと完了のソース プロバイダー (、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>インターフェイス)。 プロバイダーは、Managed Extensibility Framework (MEF) コンポーネント パーツです。 サービスとブローカー、ソースおよびコント ローラー クラスをエクスポートおよびインポートを担当している — など、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、テキスト バッファー内のナビゲーションを有効にして、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>、入力候補のセッションをトリガーします。  
  
 このチュートリアルでは、識別子のハードコーディング セットの入力候補を実装する方法を示します。 完全な実装に、言語サービスと言語のドキュメントはそのコンテンツを提供する担当します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を付けます`CompletionTest`です。  
  
2.  エディター分類子項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  次の参照をプロジェクトに追加し、ことを確認して**CopyLocal**に設定されている`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>入力候補のソースの実装  
 入力候補のソースは、識別子のセットを収集し、ユーザーは、識別子の最初の文字などの補完トリガーを入力すると、編集ウィンドウに、コンテンツの追加を担当します。 この例では、識別子とその説明がハードコーディングで、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>メソッドです。 ほとんどの実際の用途では、入力候補一覧を作成するのにトークンの取得を言語のパーサーを使用します。  
  
#### <a name="to-implement-the-completion-source"></a>入力候補のソースを実装するには  
  
1.  クラス ファイルを追加し、名前を付けます`TestCompletionSource`です。  
  
2.  これらのインポートを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  クラス宣言を変更`TestCompletionSource`を実装できるように<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  テキスト バッファーとの一覧では、ソース プロバイダーのプライベート フィールドを追加<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>オブジェクト (入力候補のセッションに参加する識別子に対応しています)。  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  同期元プロバイダーとバッファーを設定するコンス トラクターを追加します。 `TestCompletionSourceProvider`後の手順でクラスを定義します。  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>コンテキストで指定する場合、入力候補を含む入力候補のセットを追加して、メソッドです。 各入力候補のセットは、一連の<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>入力候補、補完ウィンドウのタブに対応しています。 (Visual Basic プロジェクトで、入力候補ウィンドウ タブ名は**共通**と**すべて**)。FindTokenSpanAtPosition メソッドは、次の手順で定義されます。  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  次のメソッドを使用して、カーソルの位置から現在の単語の検索します。  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  実装、`Dispose()`メソッド。  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implementing-the-completion-source-provider"></a>入力候補のソース プロバイダーを実装します。  
 入力候補のソース プロバイダーは、入力候補のソースをインスタンス化する MEF コンポーネント パーツです。  
  
#### <a name="to-implement-the-completion-source-provider"></a>入力候補のソース プロバイダーを実装するには  
  
1.  という名前のクラスを追加`TestCompletionSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>です。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 「プレーン テキスト」のおよび<xref:Microsoft.VisualStudio.Utilities.NameAttribute>「テスト完了」のです。  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  インポート、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、入力候補のソースの現在の単語を検索に使用されます。  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A>完了ソースをインスタンス化するメソッド。  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>コマンドの完了ハンドラー プロバイダーの実装  
 完了コマンド ハンドラーのプロバイダーはから派生、 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>、テキスト ビューの作成イベントをリッスンしからビューに変換する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>: Visual Studio シェルのコマンドがチェーンして、コマンドの追加を有効にする —、に<xref:Microsoft.VisualStudio.Text.Editor.ITextView>. このクラスは、MEF エクスポートであるためには、コマンド ハンドラー自体に必要なサービスをインポートするのにも使用できます。  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>完了コマンド ハンドラーのプロバイダーを実装するには  
  
1.  という名前のファイルを追加`TestCompletionCommandHandler`です。  
  
2.  ステートメントを使用して、これらを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  という名前のクラスを追加`TestCompletionHandlerProvider`を実装する<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>です。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 「トークンの完了ハンドラー」の<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>「プレーン テキスト」のおよび<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>の<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>します。  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  インポート、<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>からの変換を有効にする、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>を<xref:Microsoft.VisualStudio.Text.Editor.ITextView>、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>、および<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>標準の Visual Studio サービスへのアクセスを有効にします。  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  実装、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>コマンド ハンドラーのインスタンスを作成するメソッド。  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implementing-the-completion-command-handler"></a>完了コマンド ハンドラーの実装  
 実装する必要がありますので、ステートメント入力候補がキーボード操作によってトリガーされると、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスを受け取り、トリガー、コミット、および完了セッションを破棄するキーストロークを処理します。  
  
#### <a name="to-implement-the-completion-command-handler"></a>完了コマンド ハンドラーを実装するには  
  
1.  という名前のクラスを追加`TestCompletionCommandHandler`を実装する<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  (これに合格するコマンドは、) 次のコマンド ハンドラー、テキスト ビュー、コマンド ハンドラー プロバイダー (さまざまなサービスへのアクセスを有効)、プライベート フィールドを追加し、入力候補セッション。  
  
     [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  テキスト ビューとプロバイダー フィールドを設定し、コマンドのチェーンにコマンドを追加するコンス トラクターを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>に沿ってコマンドを渡すことによってメソッド。  
  
     [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドを実装します。 このメソッドは、キー入力を受け取る、次のいずれかにください。  
  
    -   文字バッファーに書き込まれると、トリガー、または完了をフィルター処理できるようにします。 (印刷文字、この処理します。)  
  
    -   完了すると、コミットしますが、バッファーに書き込まれる文字を許可しません。 (空白、タブ、および Enter 場合完了セッションが表示されます。)  
  
    -   次のハンドラー渡されるコマンドを許可します。 (その他のコマンドです。)  
  
     このメソッドは、UI を表示可能性があります、ために、呼び出す<xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A>オートメーション コンテキストで呼び出されていないことを確認します。  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  このコードは、入力候補のセッションをトリガーするプライベート メソッドを示します。  
  
     [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  次の例はからアンサブスク ライブするプライベート メソッド、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed>イベント。  
  
     [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、CompletionTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>ビルドし、CompletionTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、"add"という単語を含むいくつかのテキストを入力します。  
  
4.  入力と最初に"a"とし、"d"、"addition"と「対応」を含む一覧が表示されます。 加算が選択されていることに注意してください。 別の"d"を入力すると、一覧は、のみ"addition"、現在選択されているを含める必要があります。 Space キーを押し、タブ、または Enter キーを押す"addition"をコミットまたは esc キーまたはその他の任意のキーを入力して一覧を消去できます。  
  
## <a name="see-also"></a>参照  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)