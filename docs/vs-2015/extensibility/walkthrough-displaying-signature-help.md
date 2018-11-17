---
title: 'チュートリアル: シグネチャ ヘルプの表示 |Microsoft Docs'
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
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a3b902c32563da6bc21778a09b4aeaebaeabeaa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734638"
---
# <a name="walkthrough-displaying-signature-help"></a>チュートリアル: シグネチャ ヘルプの表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

シグネチャ ヘルプ (とも呼ばれます*パラメーター ヒント*)、ユーザーがパラメーター リストの開始文字 (通常、開きかっこを入力) を入力すると、ツールヒントに、メソッドのシグネチャを表示します。 パラメーターとパラメーターの区切り記号 (コンマ) を入力すると、次のパラメーターを太字で表示するツールヒントが更新されます。 シグネチャ ヘルプを定義の言語サービスのコンテキストでまたは独自ファイル名拡張子とコンテンツ タイプを定義し、その型だけのシグネチャ ヘルプを表示できますかシグネチャ ヘルプを表示の既存のコンテンツ タイプ (たとえば、"text")。 このチュートリアルでは、「テキスト」コンテンツ タイプのシグネチャ ヘルプを表示する方法を示します。  
  
 たとえば、特定の文字を入力してシグネチャ ヘルプがトリガーされる通常"("(かっこ) し、もう 1 つの文字を入力して")"(閉じかっこ)。 キーストロークのコマンド ハンドラーを使用して文字を入力することによってトリガーされる IntelliSense 機能を実装することができます (、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス)、および実装するハンドラー プロバイダー、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>インターフェイス。 署名のために使用される署名の一覧には、シグネチャ ヘルプ ソースを作成するには、実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>インターフェイスおよび実装するソース プロバイダー、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>インターフェイス。 プロバイダーは、Managed Extensibility Framework (MEF) コンポーネントの部分とはサービスとブローカー、たとえば、ソースとコント ローラー クラスをエクスポートおよびインポートを担当、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、テキスト バッファーに移動することができます、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>、シグネチャ ヘルプのセッションが開始します。  
  
 このチュートリアルでは、ハード コーディングされた一連の識別子のシグネチャ ヘルプを実装する方法を示します。 完全な実装で言語がそのコンテンツを提供する責任を負います。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
#### <a name="to-create-a-mef-project"></a>MEF プロジェクトを作成するには  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `SignatureHelpTest`の名前を指定します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  プロジェクトに次の参照を追加し、確認**CopyLocal**に設定されている`false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>署名を実装する署名とパラメーターのヘルプ  
 実装シグネチャに基づいてシグネチャ ヘルプ ソース<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>を実装するパラメーターを含む<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>します。 完全な実装でこの情報は、言語のドキュメントから取得するが、署名がハード コードされたは、この例では。  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>シグネチャ ヘルプの署名とパラメーターを実装するには  
  
1.  クラス ファイルを追加し、その名前を `SignatureHelpSource`にします。  
  
2.  次の imports を追加します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3.  という名前のクラスを追加`TestParameter`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4.  すべてのプロパティを設定するコンス トラクターを追加します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5.  プロパティを追加<xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6.  という名前のクラスを追加`TestSignature`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7.  いくつかのプライベート フィールドを追加します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8.  フィールドを設定し、サブスクライブするコンス トラクターを追加、<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベント。  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. 宣言を`CurrentParameterChanged`イベント。 シグネチャのパラメーターのいずれかで、ユーザーが入力するときは、このイベントが発生します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. 実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A>プロパティを発生させるため、`CurrentParameterChanged`イベント プロパティの値が変更されたときにします。  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. 発生させるメソッドを追加、`CurrentParameterChanged`イベント。  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. 内のコンマの数を比較することによって、現在のパラメーターを計算するメソッドを追加、<xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>署名内のコンマの数。  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. イベント ハンドラーを追加、<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベントを呼び出す、`ComputeCurrentParameter()`メソッド。  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> プロパティを実装します。 このプロパティは保持、<xref:Microsoft.VisualStudio.Text.ITrackingSpan>署名を適用するバッファー内のテキストの範囲に対応します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. その他のパラメーターを実装します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>シグネチャ ヘルプのソースの実装  
 シグネチャ ヘルプ ソースは、一連のシグネチャ情報を提供します。  
  
#### <a name="to-implement-the-signature-help-source"></a>シグネチャ ヘルプ ソースを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpSource`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2.  テキスト バッファーへの参照を追加します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3.  テキスト バッファーとシグネチャ ヘルプ ソース プロバイダーを設定するコンス トラクターを追加します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> メソッドを実装します。 この例では、署名は、ハードコーディングしますが、完全な実装では、言語のドキュメントからこの情報を取得します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5.  ヘルパー メソッド`CreateSignature()`図のためだけに用意されています。  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> メソッドを実装します。 この例では、それぞれが 2 つのパラメーターを持つ 2 つの署名です。 そのため、このメソッドは必要ありません。 シグネチャ ヘルプは、複数のソースで使用可能な完全な実装では、このメソッドが最も高い優先順位のシグネチャ ヘルプ ソースが一致するシグネチャを指定できるかどうかを決定する使用されます。 できない場合は、メソッドは null を返し、[次へ] の最高優先順位のソースが一致するものを提供するよう要求します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7.  Dispose() メソッドを実装します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>シグネチャ ヘルプ ソースのプロバイダーを実装します。  
 シグネチャ ヘルプのソース プロバイダーは Managed Extensibility Framework (MEF) コンポーネントの一部をエクスポートおよびシグネチャ ヘルプ ソースをインスタンス化します。  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>シグネチャ ヘルプのソース プロバイダーを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpSourceProvider`を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>でエクスポート、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"、および<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>の Before ="default"。  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2.  実装<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>をインスタンス化して、`TestSignatureHelpSource`します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>コマンド ハンドラーの実装  
 シグネチャ ヘルプがによってトリガーされる通常の (文字と、消去された、) 文字。 これらのキー入力を処理するには、実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>を受信するとシグネチャ ヘルプのセッションがトリガーされるよう、(文字の前に既知のメソッド名、および受信すると、セッションを閉じる、) 文字。  
  
#### <a name="to-implement-the-command-handler"></a>コマンド ハンドラーを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpCommand`を実装する<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2.  用のプライベート フィールドを追加、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> (アダプターがチェーンのコマンド ハンドラーにコマンド ハンドラーを追加することができます)、テキスト ビュー、ブローカーのシグネチャ ヘルプ、セッション、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>、次へ<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3.  これらのフィールドを初期化するために、およびコマンド フィルター チェーンのコマンドのフィルターを追加するには、コンス トラクターを追加します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4.  実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>コマンド フィルターを受信するとシグネチャ ヘルプのセッションをトリガーするメソッドを (1 つを受信すると、セッションを閉じると、既知のメソッド名の後に文字を)、セッションがアクティブな状態の文字します。 すべてのケースでは、コマンドは転送されます。  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5.  実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドを常に、コマンドを転送します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>シグネチャ ヘルプのコマンドのプロバイダーを実装します。  
 シグネチャ ヘルプ コマンドを実装することによって行うことができます、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>テキスト ビューが作成されたときに、コマンド ハンドラーのインスタンスを作成します。  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>コマンドのシグネチャ ヘルプ プロバイダーを実装するには  
  
1.  という名前のクラスを追加`TestSignatureHelpController`を実装する<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>でエクスポートし、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>、および<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2.  インポート、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (を取得するために使用、<xref:Microsoft.VisualStudio.Text.Editor.ITextView>を指定、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクト)、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (現在の単語の検索に使用)、および<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>(トリガーする、シグネチャ ヘルプのセッション)。  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3.  実装、<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>メソッドをインスタンス化して、`TestSignatureCommandHandler`します。  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、SignatureHelpTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>ビルドして SignatureHelpTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルと"add"という単語を含むいくつかのテキストの種類およびかっこを作成します。  
  
4.  かっこを入力すると後の 2 つの署名の一覧を表示するツールヒントが表示されます、`add()`メソッド。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

