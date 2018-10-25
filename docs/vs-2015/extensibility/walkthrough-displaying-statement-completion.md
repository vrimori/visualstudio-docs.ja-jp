---
title: 'チュートリアル: 候補の表示 |Microsoft Docs'
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
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f26f37a945ce9ec665e924662d117f43e49ab77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839337"
---
# <a name="walkthrough-displaying-statement-completion"></a>チュートリアル: 入力候補の表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

入力候補を提供する識別子を定義し、補完セッションをトリガーし、言語ベースのステートメント入力候補を実装できます。 言語サービスのコンテキストでステートメント入力候補を定義する、独自のファイル名拡張子とコンテンツの種類を定義および補完機能をその型だけを表示し、または既存のコンテンツ タイプの完了をトリガーする — たとえば、「プレーン テキスト」。 このチュートリアルでは、「プレーン テキスト」コンテンツ タイプ、テキスト ファイルのコンテンツの種類の入力候補をトリガーする方法を示します。 「テキスト」コンテンツの種類は、すべての他のコンテンツの種類のコードと XML ファイルを含む先祖です。  
  
 ステートメント入力候補が特定の文字の入力によってトリガーされる通常、"using"などの識別子の先頭を入力してなど。 これが通常選択をコミットする space キー、タブ、または Enter キーを押しても閉じられます。 キーストロークのコマンド ハンドラーを使用して文字を入力することによってトリガーされる IntelliSense 機能を実装することができます (、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス)、および実装するハンドラー プロバイダー、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>インターフェイス。 完了に参加している識別子のリストである、入力候補のソースを作成するには、実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>インターフェイスと完了のソース プロバイダー (、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>インターフェイス)。 プロバイダーは、Managed Extensibility Framework (MEF) コンポーネント パーツです。 サービスとブローカー、ソースおよびコント ローラー クラスをエクスポートおよびインポートを担います — など、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、テキスト バッファー内のナビゲーションを有効にして<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>、完了セッションが開始します。  
  
 このチュートリアルでは、ハード コーディングされた一連の識別子の入力候補を実装する方法を示します。 完全な実装で、言語サービスと言語のドキュメントはそのコンテンツを提供する責任を負います。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `CompletionTest`の名前を指定します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  以下の参照をプロジェクトに追加し、ことを確認します**CopyLocal**に設定されている`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>入力候補のソースの実装  
 入力候補のソースは、識別子のセットを収集し、ユーザー識別子の最初の文字などの完了トリガーすると、完了ウィンドウにコンテンツを追加します。 この例で、識別子とその説明にハード コーディングされて、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>メソッド。 ほとんどの実際の使用では、入力候補一覧を設定するのにトークンを取得するのに、言語のパーサーを使用します。  
  
#### <a name="to-implement-the-completion-source"></a>入力候補のソースを実装するには  
  
1.  クラス ファイルを追加し、その名前を `TestCompletionSource`にします。  
  
2.  これらのインポートを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3.  クラス宣言を変更`TestCompletionSource`実装できるように<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4.  同期元プロバイダー、テキスト バッファー、および一連のプライベート フィールドを追加<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>(オブジェクトを補完セッションに参加する識別子に対応しています)。  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5.  ソース プロバイダーとバッファーを設定するコンス トラクターを追加します。 `TestCompletionSourceProvider`クラスは、後の手順で定義されます。  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>コンテキストで提供するメソッドは、入力候補を含む入力候補セットを追加します。 各入力候補のセットは、一連の<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>入力候補、補完ウィンドウのタブに対応しています。 (Visual Basic プロジェクトでは、入力候補ウィンドウ タブの名前は**共通**と**すべて**)。FindTokenSpanAtPosition メソッドは、次の手順で定義されます。  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7.  次のメソッドを使用して、カーソルの位置から現在の単語を検索します。  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8.  実装、`Dispose()`メソッド。  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>入力候補のソース プロバイダーを実装します。  
 入力候補のソース プロバイダーは、入力候補のソースをインスタンス化する MEF コンポーネント パーツです。  
  
#### <a name="to-implement-the-completion-source-provider"></a>入力候補のソース プロバイダーを実装するには  
  
1.  という名前のクラスを追加`TestCompletionSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>します。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 「プレーン テキスト」の<xref:Microsoft.VisualStudio.Utilities.NameAttribute>「テスト完了」のです。  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2.  インポート、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>を使用して、入力候補のソースの現在の単語を検索します。  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A>入力候補のソースをインスタンス化するメソッド。  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>完了コマンド ハンドラーのプロバイダーを実装します。  
 完了コマンド ハンドラーのプロバイダーがから派生した、 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>、テキスト ビューの作成イベントをリッスンしからビューに変換する、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>-Visual Studio シェルのコマンドのチェーンにコマンドを追加できます:、に<xref:Microsoft.VisualStudio.Text.Editor.ITextView>. このクラスは、MEF エクスポートであるためには、コマンド ハンドラー自体に必要なサービスをインポートするのにことも使用できます。  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>完了コマンド ハンドラーのプロバイダーを実装するには  
  
1.  という名前のファイルを追加`TestCompletionCommandHandler`します。  
  
2.  次の using ステートメントを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3.  という名前のクラスを追加`TestCompletionHandlerProvider`を実装する<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>します。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 「トークンの完了ハンドラー」の<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>「プレーン テキスト」の<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>の<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>します。  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4.  インポート、<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>から変換できる、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>を<xref:Microsoft.VisualStudio.Text.Editor.ITextView>、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>、および<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>標準の Visual Studio services にアクセスできるようにします。  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5.  実装、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>コマンド ハンドラーをインスタンス化するメソッド。  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>完了コマンド ハンドラーの実装  
 実装する必要がありますので、ステートメント入力候補がキーストロークによってトリガーされる、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスを受信し、トリガー、コミット、および完了セッションを消去するキーストロークを処理します。  
  
#### <a name="to-implement-the-completion-command-handler"></a>完了コマンド ハンドラーを実装するには  
  
1. という名前のクラスを追加`TestCompletionCommandHandler`を実装する<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. 次のコマンド ハンドラー (に渡すコマンド)、テキスト ビュー、(これにより、さまざまなサービスへのアクセス)、コマンド ハンドラー プロバイダーには、プライベート フィールドを追加し、補完セッション。  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. テキスト ビューとプロバイダーのフィールドを設定し、コマンドのチェーンにコマンドを追加するコンス トラクターを追加します。  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. 実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>に沿ってコマンドを渡すことによってメソッド。  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドを実装します。 このメソッドは、キーストロークを受信すると、次のいずれかが行う必要があります。  
  
   - 文字、バッファーに書き込むと、トリガー、または完了をフィルター処理を許可します。 (印刷文字そいます。)  
  
   - 完了すると、コミットしますが、バッファーに書き込まれる文字を許可しません。 (空白、タブ、および Enter これは、完了セッションが表示されるときにします。)  
  
   - 次のハンドラー渡されるコマンドを使用できます。 (その他のコマンドです。)  
  
     このメソッドは、UI を表示可能性があります、ために、呼び出す<xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A>automation コンテキストで呼び出されるしないことを確認します。  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. このコード補完セッションをトリガーするプライベート メソッドを示します。  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. 次の例は、プライベート メソッドからアンサブスク ライブする、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed>イベント。  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、CompletionTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>ビルドして CompletionTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、"add"という単語を含むいくつかのテキストを入力します。  
  
4.  を入力すると最初に、"a"と"d"、"addition"と「適応」を含む一覧が表示されます。 加算が選択されていることに注意してください。 別の"d"を入力すると、一覧は、のみ"addition"、現在選択されているを含める必要があります。 Space キー、タブ、または Enter キーを押す"addition"をコミットまたは esc キーまたはその他の任意のキーを入力して、一覧を無視できます。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

