---
title: "チュートリアル: シグニチャ ヘルプの表示 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] 新しい - 署名ヘルプ/パラメーター ヒント"
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# チュートリアル: シグニチャ ヘルプの表示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

シグニチャ ヘルプ \(とも呼ばれます *パラメーター ヒント*\)、ユーザーがパラメーター リストの先頭文字 \(通常、開きかっこ\) を入力すると、ツールヒントに、メソッドのシグネチャを表示します。 パラメーターとパラメーター区切り記号 \(コンマ\) を入力すると、次のパラメーターを太字で表示するツールヒントが更新されます。 シグネチャ ヘルプを定義する言語サービスのコンテキストでまたは独自ファイル名拡張子とコンテンツ タイプを定義し、その型だけのシグネチャ ヘルプを表示できます。 または署名のヘルプを表示、既存のコンテンツ タイプ \(たとえば、"text"\) のです。 このチュートリアルでは、"text"コンテンツ型のシグネチャ ヘルプを表示する方法を示します。  
  
 シグニチャ ヘルプは、通常、特定の文字を入力してトリガー"\("\(かっこ\) し、別の文字を入力して"\)"\(閉じかっこ\)。 キー入力のコマンド ハンドラーを使用して文字を入力することによってトリガーされる IntelliSense 機能を実装することができます \(、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイス\) およびハンドラー プロバイダーを実装する、 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> インターフェイスです。 シグネチャ ヘルプに参加している署名の一覧では、シグネチャ ヘルプ ソースを作成するには、実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> インターフェイスと同期元プロバイダーを実装する、 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> インターフェイスです。 プロバイダーは、Managed Extensibility Framework \(MEF\) コンポーネントの部分とのサービスとブローカー、たとえば、ソースとコント ローラー クラスをエクスポートおよびインポートを担当する、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, 、テキスト バッファー内を移動することができますし、 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, 、シグネチャ ヘルプ セッションをトリガーします。  
  
 このチュートリアルでは、シグネチャ ヘルプ、ハード コーディングされた一連の識別子を実装する方法を示します。 完全な実装で、言語は、そのコンテンツを提供する責任です。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## MEF プロジェクトを作成します。  
  
#### MEF プロジェクトを作成するには  
  
1.  C\# の場合は、VSIX プロジェクトを作成します。 \(で、 **新しいプロジェクト** ダイアログで、 **Visual c\#\/機能拡張**, 、し **VSIX プロジェクト**.\) ソリューションの名前 `SignatureHelpTest`します。  
  
2.  エディターの分類子の項目テンプレートをプロジェクトに追加します。 詳細については、「[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)」を参照してください。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  プロジェクトに次の参照を追加し、確認 **CopyLocal** に設定されている `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## 署名を実装する署名とパラメーターのヘルプ  
 実装する署名に基づいてシグネチャ ヘルプ ソース <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, を実装するパラメーターを含む <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>します。 完全な実装では、この情報は、language のドキュメントから取得するが、この例では、署名は、ハード コーディングされました。  
  
#### 署名のシグネチャ ヘルプ、パラメーターを実施するには  
  
1.  クラス ファイルを追加し、名前 `SignatureHelpSource`します。  
  
2.  次の imports を追加します。  
  
     [!CODE [VSSDKSignatureHelpTest#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#1)]  
  
3.  という名前のクラスを追加 `TestParameter` を実装する <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>です。  
  
     [!CODE [VSSDKSignatureHelpTest#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#2)]  
  
4.  すべてのプロパティを設定するコンス トラクターを追加します。  
  
     [!CODE [VSSDKSignatureHelpTest#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#3)]  
  
5.  プロパティを追加 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>します。  
  
     [!CODE [VSSDKSignatureHelpTest#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#4)]  
  
6.  という名前のクラスを追加 `TestSignature` を実装する <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>です。  
  
     [!CODE [VSSDKSignatureHelpTest#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#5)]  
  
7.  いくつかのプライベート フィールドを追加します。  
  
     [!CODE [VSSDKSignatureHelpTest#6](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#6)]  
  
8.  フィールドを設定し、サブスクライブするコンス トラクターを追加、 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> イベントです。  
  
     [!CODE [VSSDKSignatureHelpTest#7](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#7)]  
  
9. 宣言、 `CurrentParameterChanged` イベントです。 シグネチャ内のパラメーターのいずれかで、ユーザーが入力すると、このイベントが発生します。  
  
     [!CODE [VSSDKSignatureHelpTest#8](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#8)]  
  
10. 実装、 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> it を発生させるためのプロパティ、 `CurrentParameterChanged` プロパティ値が変更されたときにイベントです。  
  
     [!CODE [VSSDKSignatureHelpTest#9](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#9)]  
  
11. 生成するメソッドを追加、 `CurrentParameterChanged` イベントです。  
  
     [!CODE [VSSDKSignatureHelpTest#10](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#10)]  
  
12. 内のコンマの数を比較することによって、現在のパラメーターを計算するメソッドを追加、 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 署名内のコンマの数にします。  
  
     [!CODE [VSSDKSignatureHelpTest#11](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#11)]  
  
13. イベント ハンドラーを追加、 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> を呼び出すイベント、 `ComputeCurrentParameter()` メソッドです。  
  
     [!CODE [VSSDKSignatureHelpTest#12](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#12)]  
  
14. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> プロパティを実装します。 このプロパティは保持、 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 署名を適用するバッファー内のテキストの範囲に対応します。  
  
     [!CODE [VSSDKSignatureHelpTest#13](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#13)]  
  
15. その他のパラメーターを実装します。  
  
     [!CODE [VSSDKSignatureHelpTest#14](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#14)]  
  
## 署名ヘルプ ソースの実装  
 シグネチャ ヘルプ ソースは、一連の情報を提供するシグネチャです。  
  
#### シグネチャ ヘルプ ソースを実装するには  
  
1.  という名前のクラスを追加 `TestSignatureHelpSource` を実装する <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>です。  
  
     [!CODE [VSSDKSignatureHelpTest#15](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#15)]  
  
2.  テキスト バッファーへの参照を追加します。  
  
     [!CODE [VSSDKSignatureHelpTest#16](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#16)]  
  
3.  テキスト バッファーと、シグネチャ ヘルプ ソース プロバイダーを設定するコンス トラクターを追加します。  
  
     [!CODE [VSSDKSignatureHelpTest#17](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#17)]  
  
4.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> メソッドを実装します。 この例では、署名は、ハードコードが、完全な実装では、language のドキュメントからこの情報を取得します。  
  
     [!CODE [VSSDKSignatureHelpTest#18](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#18)]  
  
5.  ヘルパー メソッド `CreateSignature()` 図のためだけに用意されています。  
  
     [!CODE [VSSDKSignatureHelpTest#19](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#19)]  
  
6.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> メソッドを実装します。 この例では、それぞれが 2 つのパラメーターを持つ 2 つの署名があります。 そのため、このメソッドは必要ありません。 シグネチャ ヘルプの 1 つ以上のソースで使用可能な詳細な実装はこのメソッドを使用して、一致するシグネチャが最も高い優先順位シグネチャ ヘルプ ソースから供給するかどうかを決定します。 できない場合は、このメソッドは null を返し、次に最も高い優先順位のソースが一致するものを指定するように求めします。  
  
     [!CODE [VSSDKSignatureHelpTest#20](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#20)]  
  
7.  Dispose\(\) メソッドを実装します。  
  
     [!CODE [VSSDKSignatureHelpTest#21](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#21)]  
  
## シグネチャ ヘルプ ソースのプロバイダーを実装します。  
 シグネチャ ヘルプ ソース プロバイダーでは、Managed Extensibility Framework \(MEF\) コンポーネントの一部をエクスポートして、シグネチャ ヘルプ ソースのインスタンスを作成する責任者です。  
  
#### プロバイダーを実装する、シグネチャ ヘルプ ソース  
  
1.  という名前のクラスを追加 `TestSignatureHelpSourceProvider` を実装する <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, 、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, 、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"のおよび <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> の前に"default"を \= です。  
  
     [!CODE [VSSDKSignatureHelpTest#22](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#22)]  
  
2.  実装 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> をインスタンス化して、 `TestSignatureHelpSource`です。  
  
     [!CODE [VSSDKSignatureHelpTest#23](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#23)]  
  
## コマンド ハンドラーを実装します。  
 シグニチャ ヘルプは、通常トリガー、\(文字とによって無視された、\) 文字です。 これらのキー入力を処理するには、実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> を受信すると、シグネチャ ヘルプ セッションがトリガーされるよう、\(文字の前に、既知のメソッド名と受信すると、セッションを閉じる、\) 文字です。  
  
#### コマンド ハンドラーを実装するには  
  
1.  という名前のクラスを追加 `TestSignatureHelpCommand` を実装する <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>です。  
  
     [!CODE [VSSDKSignatureHelpTest#24](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#24)]  
  
2.  プライベート フィールドを追加、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> \(アダプターがチェーンのコマンド ハンドラーをコマンド ハンドラーを追加できます\)、テキスト ビュー、シグネチャ ヘルプ ブローカーおよびセッション、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, と次の <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>です。  
  
     [!CODE [VSSDKSignatureHelpTest#25](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#25)]  
  
3.  これらのフィールドを初期化し、チェーンのコマンドのフィルターにコマンドのフィルターを追加するには、コンス トラクターを追加します。  
  
     [!CODE [VSSDKSignatureHelpTest#26](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#26)]  
  
4.  実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> コマンドのフィルターを受信すると、シグネチャ ヘルプ セッションを開始する方法、\(を受信すると、セッションを閉じると既知のメソッド名のいずれかの後に文字、\)、セッションがアクティブな状態の文字します。 どのケースでも、コマンドは転送されます。  
  
     [!CODE [VSSDKSignatureHelpTest#27](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#27)]  
  
5.  実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> メソッドことは、コマンドを常に転送します。  
  
     [!CODE [VSSDKSignatureHelpTest#28](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#28)]  
  
## シグネチャ ヘルプ コマンド プロバイダーを実装します。  
 実装することによって、シグネチャ ヘルプ コマンドを指定することができます、 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> テキスト ビューが作成されると、コマンド ハンドラーのインスタンスを作成します。  
  
#### プロバイダーを実装する、シグネチャ ヘルプ コマンド  
  
1.  という名前のクラスを追加 `TestSignatureHelpController` を実装する <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> にエクスポートし、 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, 、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, 、および <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>です。  
  
     [!CODE [VSSDKSignatureHelpTest#29](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#29)]  
  
2.  インポート、 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> \(を取得するために使用、 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, 、指定された、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> オブジェクト\)、 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> \(現在の単語を検索に使用\)、および <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> \(をトリガーする、シグネチャ ヘルプ セッション\)。  
  
     [!CODE [VSSDKSignatureHelpTest#30](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#30)]  
  
3.  実装、 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> メソッドをインスタンス化して、 `TestSignatureCommandHandler`です。  
  
     [!CODE [VSSDKSignatureHelpTest#31](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#31)]  
  
## コードのビルドとテスト  
 このコードをテストするには、SignatureHelpTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### ビルドし、SignatureHelpTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルとという単語を含むいくつかのテキストを「追加」の種類と、開きかっこを作成します。  
  
4.  開きかっこを入力すると後の 2 つのシグネチャの一覧を表示するツールヒントが表示されます、 `add()` メソッドです。  
  
## 参照  
 [チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)