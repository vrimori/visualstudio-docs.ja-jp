---
title: 'チュートリアル: 候補の表示 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c91f9aec4bd3db9a9495b2a05ce5153bf45f2f52
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009766"
---
# <a name="walkthrough-display-statement-completion"></a>チュートリアル: ステートメント入力候補を表示します。
入力候補を提供する識別子を定義し、補完セッションをトリガーし、言語ベースのステートメント入力候補を実装できます。 言語サービスのコンテキストでステートメント入力候補を定義、ファイル名拡張子とコンテンツの種類を定義し、補完機能をその型だけを表示できます。 または、既存のコンテンツ タイプの完了をトリガーする — たとえば、「プレーン テキスト」。 このチュートリアルでは、「プレーン テキスト」コンテンツ タイプ、テキスト ファイルのコンテンツの種類の入力候補をトリガーする方法を示します。 「テキスト」コンテンツの種類は、すべての他のコンテンツの種類のコードと XML ファイルを含む先祖です。  
  
 ステートメント入力候補が特定の文字の入力によってトリガーされる通常、"using"などの識別子の先頭を入力してなど。 キーを押してを閉じる通常、 **space キーを押す**、**タブ**、または **」と入力**選択をコミットするキー。 キーストロークのコマンド ハンドラーを使用して文字を入力するときにトリガーする IntelliSense 機能を実装することができます (、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス)、および実装するハンドラー プロバイダー、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>インターフェイス。 完了に参加している識別子のリストである、入力候補のソースを作成するには、実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>インターフェイスと完了のソース プロバイダー (、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>インターフェイス)。 プロバイダーは、Managed Extensibility Framework (MEF) コンポーネント パーツです。 サービスとブローカー、ソースおよびコント ローラー クラスをエクスポートおよびインポートを行います: など、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、テキスト バッファー内のナビゲーションを有効にして<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>、完了セッションが開始します。  
  
 このチュートリアルでは、ハード コーディングされた一連の識別子の入力候補を実装する方法を示します。 完全な実装で、言語サービスと言語のドキュメントはそのコンテンツを提供する責任を負います。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-a-mef-project"></a>MEF プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `CompletionTest`の名前を指定します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  以下の参照をプロジェクトに追加し、ことを確認します**CopyLocal**に設定されている`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implement-the-completion-source"></a>入力候補のソースを実装します。  
 入力候補のソースは、識別子のセットを収集し、ユーザー識別子の最初の文字などの完了トリガーすると、完了ウィンドウにコンテンツを追加します。 この例で、識別子とその説明にハード コーディングされて、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>メソッド。 ほとんどの実際の使用では、入力候補一覧を設定するのにトークンを取得するのに、言語のパーサーを使用します。  
  
### <a name="to-implement-the-completion-source"></a>入力候補のソースを実装するには  
  
1.  クラス ファイルを追加し、その名前を `TestCompletionSource`にします。  
  
2.  これらのインポートを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  クラス宣言を変更`TestCompletionSource`実装できるように<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  同期元プロバイダー、テキスト バッファー、および一連のプライベート フィールドを追加<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>(オブジェクトを補完セッションに参加する識別子に対応しています)。  
  
     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  ソース プロバイダーとバッファーを設定するコンス トラクターを追加します。 `TestCompletionSourceProvider`クラスは、後の手順で定義されます。  
  
     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>コンテキストで提供するメソッドは、入力候補を含む入力候補セットを追加します。 各入力候補のセットは、一連の<xref:Microsoft.VisualStudio.Language.Intellisense.Completion>入力候補、補完ウィンドウのタブに対応しています。 (Visual Basic プロジェクトでは、入力候補ウィンドウ タブの名前は**共通**と**すべて**)。`FindTokenSpanAtPosition` メソッドは、次の手順で定義します。  
  
     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  次のメソッドを使用して、カーソルの位置から現在の単語を検索します。  
  
     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  実装、`Dispose()`メソッド。  
  
     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## <a name="implement-the-completion-source-provider"></a>入力候補のソース プロバイダーを実装します。  
 入力候補のソース プロバイダーは、入力候補のソースをインスタンス化する MEF コンポーネント パーツです。  
  
### <a name="to-implement-the-completion-source-provider"></a>入力候補のソース プロバイダーを実装するには  
  
1.  という名前のクラスを追加`TestCompletionSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>します。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 「プレーン テキスト」の<xref:Microsoft.VisualStudio.Utilities.NameAttribute>「テスト完了」のです。  
  
     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  インポート、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、入力候補のソースの現在の単語を検索します。  
  
     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A>入力候補のソースをインスタンス化するメソッド。  
  
     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## <a name="implement-the-completion-command-handler-provider"></a>コマンドの完了ハンドラー プロバイダーを実装します。  
 完了コマンド ハンドラーのプロバイダーがから派生した、 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>、テキスト ビューの作成イベントをリッスンしからビューに変換する、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>-Visual Studio シェルのコマンドのチェーンにコマンドを追加できます:、に<xref:Microsoft.VisualStudio.Text.Editor.ITextView>. このクラスは、MEF エクスポートであるためには、コマンド ハンドラー自体に必要なサービスをインポートするのにことも使用できます。  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>完了コマンド ハンドラーのプロバイダーを実装するには  
  
1.  という名前のファイルを追加`TestCompletionCommandHandler`します。  
  
2.  次の using ステートメントを追加します。  
  
     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  という名前のクラスを追加`TestCompletionHandlerProvider`を実装する<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>します。 このクラスをエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 「トークンの完了ハンドラー」の<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>「プレーン テキスト」の<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>の<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>します。  
  
     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  インポート、<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>から変換できる、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>を<xref:Microsoft.VisualStudio.Text.Editor.ITextView>、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>、および<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>標準の Visual Studio services にアクセスできるようにします。  
  
     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  実装、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>コマンド ハンドラーをインスタンス化するメソッド。  
  
     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## <a name="implement-the-completion-command-handler"></a>完了コマンド ハンドラーを実装します。  
 実装する必要がありますので、ステートメント入力候補がキーストロークによってトリガーされる、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスを受信し、トリガー、コミット、および完了セッションを消去するキーストロークを処理します。  
  
#### <a name="to-implement-the-completion-command-handler"></a>完了コマンド ハンドラーを実装するには  
  
1. という名前のクラスを追加`TestCompletionCommandHandler`を実装する<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2. 次のコマンド ハンドラー (に渡すコマンド)、テキスト ビュー、(これにより、さまざまなサービスへのアクセス)、コマンド ハンドラー プロバイダーには、プライベート フィールドを追加し、補完セッション。  
  
    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3. テキスト ビューとプロバイダーのフィールドを設定し、コマンドのチェーンにコマンドを追加するコンス トラクターを追加します。  
  
    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4. 実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>に沿ってコマンドを渡すことによってメソッド。  
  
    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> メソッドを実装します。 このメソッドは、キーストロークを受信すると、次のいずれかが行う必要があります。  
  
   - 文字、バッファーに書き込むと、トリガー、または完了をフィルター処理を許可します。 (印刷文字そいます。)  
  
   - 完了すると、コミットしますが、バッファーに書き込まれる文字を許可しません。 (空白、**タブ**、および **」と入力**完了セッションが表示されるときにこの操作を行います)。  
  
   - 次のハンドラー渡されるコマンドを使用できます。 (その他のコマンドです。)  
  
     このメソッドは、UI を表示可能性があります、ために、呼び出す<xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A>automation コンテキストで呼び出されるしないことを確認します。  
  
     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6. このコード補完セッションをトリガーするプライベート メソッドを示します。  
  
    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7. 次の例は、プライベート メソッドからアンサブスク ライブする、<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed>イベント。  
  
    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## <a name="build-and-test-the-code"></a>ビルドし、コードのテスト  
 このコードをテストするには、CompletionTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>ビルドして CompletionTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行する場合は、Visual Studio の 2 番目のインスタンスが開始します。  
  
3.  テキスト ファイルを作成し、"add"という単語を含むいくつかのテキストを入力します。  
  
4.  を入力すると最初に、"a"と"d"、"addition"と「適応」を含む一覧が表示されます。 加算が選択されていることに注意してください。 別の"d"を入力すると、一覧は、のみ"addition"、現在選択されているを含める必要があります。 "Addition"をコミットするにはキーを押して、 **space キーを押す**、**タブ**、または **」と入力**キーまたは esc キーまたはその他の任意のキーを入力して、一覧を無視します。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類をファイル名拡張子にリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)