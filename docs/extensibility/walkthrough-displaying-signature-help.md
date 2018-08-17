---
title: 'チュートリアル: シグネチャ ヘルプの表示 |Microsoft Docs'
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
ms.openlocfilehash: cc260fe45bf4c6cf801718c2f4c3bbaa98842dd6
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498906"
---
# <a name="walkthrough-display-signature-help"></a>チュートリアル: シグネチャ ヘルプを表示します。
シグネチャ ヘルプ (とも呼ばれます*パラメーター ヒント*)、ユーザーがパラメーター リストの開始文字 (通常、開きかっこを入力) を入力すると、ツールヒントに、メソッドのシグネチャを表示します。 パラメーターとパラメーターの区切り記号 (コンマ) を入力すると、次のパラメーターを太字で表示するツールヒントが更新されます。 シグネチャ ヘルプを定義で、次の方法: 言語サービスのコンテキストで、独自のファイル名拡張子とコンテンツの種類を定義し、その型シグネチャ ヘルプを表示または既存のコンテンツ タイプ (たとえば、"text") のシグネチャ ヘルプを表示します。 このチュートリアルでは、「テキスト」コンテンツ タイプのシグネチャ ヘルプを表示する方法を示します。  
  
 たとえば、特定の文字を入力してシグネチャ ヘルプがトリガーされる通常"("(かっこ) し、もう 1 つの文字を入力して")"(閉じかっこ)。 キーストロークのコマンド ハンドラーを使用して文字を入力することによってトリガーされる IntelliSense 機能を実装することができます (、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス)、および実装するハンドラー プロバイダー、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>インターフェイス。 署名のために使用される署名の一覧には、シグネチャ ヘルプ ソースを作成するには、実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>インターフェイス、および実行するソース プロバイダー、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>インターフェイス。 プロバイダーは、Managed Extensibility Framework (MEF) コンポーネントの部分とはサービスとブローカー、たとえば、ソースとコント ローラー クラスをエクスポートおよびインポートを担当、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、テキスト バッファーに移動することができます、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>、シグネチャ ヘルプのセッションが開始します。  
  
 このチュートリアルでは、ハード コーディングされた一連の識別子のシグネチャ ヘルプを設定する方法を示します。 完全な実装で言語がそのコンテンツを提供する責任を負います。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を`SignatureHelpTest`します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  プロジェクトに次の参照を追加し、確認**CopyLocal**に設定されている`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implement-signature-help-signatures-and-parameters"></a>シグネチャ ヘルプの署名とパラメーターを実装します。  
 実装シグネチャに基づいてシグネチャ ヘルプ ソース<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>を実装するパラメーターを含む<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>します。 完全な実装でこの情報は、言語のドキュメントから取得するが、署名がハード コードされたは、この例では。  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>シグネチャ ヘルプの署名とパラメーターを実装するには  
  
1.  クラス ファイルを追加し、名前`SignatureHelpSource`します。  
  
2.  次の imports を追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  という名前のクラスを追加`TestParameter`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>します。  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  すべてのプロパティを設定するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  プロパティを追加<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>します。  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  という名前のクラスを追加`TestSignature`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>します。  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  いくつかのプライベート フィールドを追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  フィールドを設定し、サブスクライブするコンス トラクターを追加、<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベント。  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. 宣言を`CurrentParameterChanged`イベント。 シグネチャのパラメーターのいずれかで、ユーザーが入力するときは、このイベントが発生します。  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. 実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>プロパティを発生させるため、`CurrentParameterChanged`イベント プロパティの値が変更されたときにします。  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. 発生させるメソッドを追加、`CurrentParameterChanged`イベント。  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. 内のコンマの数を比較することによって、現在のパラメーターを計算するメソッドを追加、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>署名内のコンマの数。  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. イベント ハンドラーを追加、<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベントを呼び出す、`ComputeCurrentParameter()`メソッド。  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> プロパティを実装します。 このプロパティは保持、<xref:Microsoft.VisualStudio.Text.ITrackingSpan>署名を適用するバッファー内のテキストの範囲に対応します。  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. その他のパラメーターを実装します。  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implement-the-signature-help-source"></a>シグネチャ ヘルプ ソースを実装します。  
 シグネチャ ヘルプ ソースは、一連のシグネチャ情報を提供します。  
  
#### <a name="to-implement-the-signature-help-source"></a>シグネチャ ヘルプ ソースを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpSource`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>します。  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  テキスト バッファーへの参照を追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  テキスト バッファーとシグネチャ ヘルプ ソース プロバイダーを設定するコンス トラクターを追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> メソッドを実装します。 この例では、署名は、ハードコーディングしますが、完全な実装では、言語のドキュメントからこの情報を取得します。  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  ヘルパー メソッド`CreateSignature()`図のためだけに用意されています。  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> メソッドを実装します。 この例では、それぞれが 2 つのパラメーターを持つ 2 つの署名です。 そのため、このメソッドは必要ありません。 シグネチャ ヘルプは、複数のソースで使用可能な完全な実装では、このメソッドが最も高い優先順位のシグネチャ ヘルプ ソースが一致するシグネチャを指定できるかどうかを決定する使用されます。 できない場合は、メソッドは null を返し、[次へ] の最高優先順位のソースが一致するものを提供するよう要求します。  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  実装、`Dispose()`メソッド。  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implement-the-signature-help-source-provider"></a>シグネチャ ヘルプ ソース プロバイダーを実装します。  
 シグネチャ ヘルプのソース プロバイダーは Managed Extensibility Framework (MEF) コンポーネントの一部をエクスポートおよびシグネチャ ヘルプ ソースをインスタンス化します。  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>シグネチャ ヘルプのソース プロバイダーを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>でエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"、および<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>の Before ="default"。  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  実装<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>をインスタンス化して、`TestSignatureHelpSource`します。  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implement-the-command-handler"></a>コマンド ハンドラーを実装します。  
 シグネチャ ヘルプがかっこによってトリガーされる通常「("文字と終わりかっこの入力に消去された」)"の文字。 これらのキー入力を処理するには、実行されている、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>開始を受信するとシグネチャ ヘルプのセッションがトリガーされるようかっこ文字の前に既知のメソッド名、および終了を受信すると、セッションを閉じるかっこ文字。  
  
#### <a name="to-implement-the-command-handler"></a>コマンド ハンドラーを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpCommand`を実装する<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>します。  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  用のプライベート フィールドを追加、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> (アダプターがチェーンのコマンド ハンドラーにコマンド ハンドラーを追加することができます)、テキスト ビュー、ブローカーのシグネチャ ヘルプ、セッション、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>、次へ<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>します。  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  これらのフィールドを初期化するために、およびコマンド フィルター チェーンのコマンドのフィルターを追加するには、コンス トラクターを追加します。  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>コマンド フィルターがかっこを受信するとシグネチャ ヘルプのセッションをトリガーする方法」(「文字、終わりかっこを受信すると、セッションを消去して、既知のメソッド名のいずれかの後に」)"の文字セッションがアクティブな状態です。 すべてのケースでは、コマンドは転送されます。  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドを常に、コマンドを転送します。  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implement-the-signature-help-command-provider"></a>シグネチャ ヘルプ コマンド プロバイダーを実装します。  
 シグネチャ ヘルプ コマンドを実装することによって行うことができます、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>テキスト ビューが作成されたときに、コマンド ハンドラーのインスタンスを作成します。  
  
### <a name="to-implement-the-signature-help-command-provider"></a>コマンドのシグネチャ ヘルプ プロバイダーを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpController`を実装する<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>でエクスポートし、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>、および<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>します。  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  インポート、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (を取得するために使用、<xref:Microsoft.VisualStudio.Text.Editor.ITextView>を指定、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクト)、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (現在の単語の検索に使用)、および<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>(トリガーする、シグネチャ ヘルプのセッション)。  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  実装、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>メソッドをインスタンス化して、`TestSignatureCommandHandler`します。  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="build-and-test-the-code"></a>ビルドし、コードのテスト  
 このコードをテストするには、SignatureHelpTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>ビルドして SignatureHelpTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行する場合は、Visual Studio の 2 番目のインスタンスが開始します。  
  
3.  テキスト ファイルと"add"という単語を含むいくつかのテキストの種類およびかっこを作成します。  
  
4.  かっこを入力すると後の 2 つの署名の一覧を表示するツールヒントが表示されます、`add()`メソッド。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類をファイル名拡張子にリンクします。](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)