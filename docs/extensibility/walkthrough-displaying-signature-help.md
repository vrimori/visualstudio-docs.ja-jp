---
title: 'チュートリアル: 署名のヘルプの表示 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a714fdb268f44fd2a65d04184d899ced3de53bb9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-displaying-signature-help"></a>チュートリアル: 署名のヘルプを表示します。
署名のヘルプ (とも呼ばれる*パラメーター ヒント*)、ユーザーがパラメーター リストの開始文字 (通常、始めかっこを入力) を入力すると、ツールヒントに、メソッドのシグネチャを表示します。 パラメーターとパラメーター区切り記号 (コンマ) を入力すると、次のパラメーターを太字で表示するツールヒントが更新されます。 シグネチャ ヘルプを定義、言語サービスのコンテキストでまたは独自ファイル名拡張子とコンテンツの種類を定義してその型のシグネチャのヘルプを表示または署名のヘルプを表示の既存のコンテンツ タイプ (たとえば、"text") です。 このチュートリアルでは、"text"コンテンツ タイプの署名のヘルプを表示する方法を示します。  
  
 たとえば、特定の文字を入力して署名のヘルプがトリガーされる通常"("(かっこ) し、別の文字を入力して")"(終わりかっこ)。 キーストロークのコマンド ハンドラーを使用して文字を入力するによってトリガーされる IntelliSense 機能を実装することができます (、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス) およびハンドラー プロバイダーを実装する、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>インターフェイスです。 ソースを作成する、シグネチャ ヘルプ、シグネチャ ヘルプに参加している署名の一覧には、実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>インターフェイスを実装するソース プロバイダー、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>インターフェイスです。 プロバイダーは、Managed Extensibility Framework (MEF) コンポーネント パーツ、サービスとブローカーなど、ソースおよびコント ローラー クラスをエクスポートおよびインポートを担当する、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、テキスト バッファーに移動することができます、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>、シグネチャ ヘルプ セッションをトリガーします。  
  
 このチュートリアルでは、シグネチャ ヘルプ、ハード コーディングされた一連の識別子を実装する方法を示します。 完全な実装に、言語は、そのコンテンツを提供する責任です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を付けます`SignatureHelpTest`です。  
  
2.  エディター分類子項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  プロジェクトに次の参照を追加し、確認**CopyLocal**に設定されている`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>署名を実装する署名とパラメーターのヘルプ  
 実装する署名に基づいて、シグネチャ ヘルプ ソース<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>を実装するパラメーターを含む各<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>です。 完全な実装でこの情報は、言語のドキュメントから取得するけれども、この例では、署名がハードコーディング  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>署名のための署名とパラメーターを実装するには  
  
1.  クラス ファイルを追加し、名前を付けます`SignatureHelpSource`です。  
  
2.  次の imports を追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  という名前のクラスを追加`TestParameter`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>です。  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  すべてのプロパティを設定するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  プロパティを追加<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>です。  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  という名前のクラスを追加`TestSignature`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>です。  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  いくつかのプライベート フィールドを追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  フィールドを設定しをサブスクライブするコンス トラクターを追加、<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベント。  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. 宣言、`CurrentParameterChanged`イベント。 このイベントはシグネチャ内のパラメーターのいずれかで、ユーザーが入力するときに発生します。  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. 実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>プロパティを発生させるため、`CurrentParameterChanged`イベント プロパティの値が変更されたときにします。  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. 生成するメソッドを追加、`CurrentParameterChanged`イベント。  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. コンマの数を比較することによって、現在のパラメーターを計算するメソッドを追加、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>シグネチャでコンマの数。  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. イベント ハンドラーを追加、<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>を呼び出すイベント、`ComputeCurrentParameter()`メソッドです。  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> プロパティを実装します。 このプロパティは、保持、<xref:Microsoft.VisualStudio.Text.ITrackingSpan>署名を適用するバッファー内のテキストの範囲に対応します。  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. その他のパラメーターを実装します。  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>署名ヘルプ ソースの実装  
 シグネチャ ヘルプ ソースが一連の署名情報を提供します。  
  
#### <a name="to-implement-the-signature-help-source"></a>シグネチャ ヘルプ ソースを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpSource`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>です。  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  テキスト バッファーへの参照を追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  テキスト バッファーと、シグネチャ ヘルプ ソース プロバイダーを設定するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> メソッドを実装します。 この例では、署名は、ハードコードしますが、完全な実装では、言語のドキュメントからこの情報を取得します。  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  ヘルパー メソッド`CreateSignature()`図のためだけに用意されています。  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> メソッドを実装します。 この例では、それぞれが 2 つのパラメーターを持つ 2 つの署名があります。 そのため、このメソッドは必要ありません。 複数のシグネチャ ヘルプ ソースで使用可能な詳細な実装はこのメソッドを使用して、優先度が高いシグネチャ ヘルプ ソースが、一致するシグネチャを指定できるかどうかを決定します。 できない場合は、メソッドは null を返し、次の優先度が高いソースは、一致を指定を求められます。  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Dispose() メソッドを実装します。  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>署名ヘルプ ソース プロバイダーの実装  
 シグネチャ ヘルプ ソース プロバイダーは、Managed Extensibility Framework (MEF) コンポーネント部分をエクスポートするため、シグネチャ ヘルプ ソースをインスタンス化するためです。  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>プロバイダーを実装する、シグネチャ ヘルプ ソース  
  
1.  という名前のクラスを追加`TestSignatureHelpSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>でエクスポートし、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"、および<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>の Before ="default"です。  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  実装<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>をインスタンス化して、`TestSignatureHelpSource`です。  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>コマンド ハンドラーの実装  
 署名のヘルプがによってトリガーされる通常、(文字とによって無視された、) 文字です。 これらのキー入力を処理するには、実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>受信すると、署名のためのセッションが開始されるよう、(文字の前に、既知のメソッド名と受信すると、セッションを閉じる、) 文字です。  
  
#### <a name="to-implement-the-command-handler"></a>コマンド ハンドラーを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpCommand`を実装する<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>です。  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  プライベート フィールドを追加、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> (アダプターが、チェーンのコマンド ハンドラーにコマンド ハンドラーを追加できます)、テキスト ビュー、ブローカーのシグネチャ ヘルプ、セッション、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>、し、次へ<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>です。  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  これらのフィールドを初期化し、チェーンのコマンドのフィルターにコマンドのフィルターを追加するには、コンス トラクターを追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>コマンド フィルターが受信すると、シグネチャ ヘルプ セッションをトリガーするメソッド、(文字を 1 つ、既知のメソッド名を受信すると、セッションを解除した後、) 文字のセッションがアクティブな状態です。 すべてのケースでは、コマンドは転送されます。  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドことが常に、コマンドを転送するようにします。  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>署名ヘルプ コマンド プロバイダーの実装  
 実装することによって、シグネチャ ヘルプ コマンドを指定することができます、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>テキスト ビューの作成時にコマンド ハンドラーのインスタンスを作成します。  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>プロバイダーを実装する、シグネチャ ヘルプ コマンド  
  
1.  という名前のクラスを追加`TestSignatureHelpController`を実装する<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>でエクスポートし、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>、および<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>です。  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  インポート、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (を取得するために使用、 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>、指定された、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクト)、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (現在の単語の検索に使用)、および<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>(トリガーする、シグネチャ ヘルプ セッション)。  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  実装、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>をインスタンス化することによって、`TestSignatureCommandHandler`です。  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、SignatureHelpTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>ビルドし、SignatureHelpTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルおよびという単語を含むいくつかのテキストを「追加」の種類のほか、始めかっこを作成します。  
  
4.  始めかっこを入力すると後の 2 つの署名の一覧を表示するツールヒントが表示されます、`add()`メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)