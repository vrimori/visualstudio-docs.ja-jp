---
title: "チェックリスト: 従来の言語サービスを作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "言語サービス"
  - "言語サービスでは、ネイティブ コード"
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# チェックリスト: 従来の言語サービスを作成します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次のチェック リストは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のコア エディターの言語サービスを作成するための必要がある基本的な手順を示します。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]言語サービスを統合するにはデバッガーの式エバリュエーターを作成する必要があります。  詳細については[Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md) の [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) を参照してください。  
  
## 言語サービスの作成手順  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> インターフェイスを実装します。  
  
    -   VSPackage では言語サービスを提供するために <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>インターフェイスを実装します。  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> の実装の統合開発環境に \(IDE\) 言語サービスを使用できるようにします。  
  
2.  主要な言語サービス クラスの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイスを実装します。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> のインターフェイスはコア エディターと言語サービスとのやり取りの開始点です。  
  
### オプションの機能  
 次の機能は省略可能で任意の順序で実行できます。  これらの機能は言語サービスの機能を拡張します。  
  
-   構文の色指定  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> インターフェイスを実装します。  パーサーのある情報が適切な色の情報を返す場合このインターフェイスを実装します。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> のメソッド <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> のインターフェイス。  別の colorizer のインスタンスはテキスト バッファーに対して作成されるため<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> のインターフェイスを実行する必要があります。  詳細については、「[構文の色分けで従来の言語サービス](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)」を参照してください。  
  
-   コード ウィンドウ  
  
     新しいコード ウィンドウが作成されると言語サービスが通知を受け取るように <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>インターフェイスを実装します。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> のメソッド <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> のインターフェイス。  言語サービスのコードは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> ウィンドウに特別な UI を追加できます。  言語サービスは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> のテキスト ビュー フィルターの追加など特別な処理を行うことができます。  
  
-   テキスト ビュー フィルター  
  
     言語サービスの IntelliSense のステートメント入力候補機能を提供するにはテキスト ビューが以外の場合は処理するコマンドの一部を傍受する必要があります。  これらのコマンドを受け取るには次の手順を実行します :  
  
    -   司令チェーンに参加するエディター コマンドを処理する <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> を実行します。  
  
    -   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> のメソッドを呼び出し<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> の実装を渡します。  
  
    -   これらのコマンドがによって渡されないようにから切り離したとき <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> のメソッドを呼び出します。  
  
     扱うコマンドで提供されるサービスによって異なります。  詳細については、「[言語サービスのフィルターの重要なコマンド](../../extensibility/internals/important-commands-for-language-service-filters.md)」を参照してください。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> のインターフェイスは <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> のインターフェイスと同じオブジェクトで実行する必要があります。  
  
-   ステートメント入力候補  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> インターフェイスを実装します。  
  
     ステートメント入力候補のコマンド \(つまり<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>\) をサポートし<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> のインターフェイスを渡す <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> のインターフェイス <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> のメソッドを呼び出します。  詳細については、「[従来の言語サービスでのステートメント入力候補](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)」を参照してください。  
  
-   メソッドのヒント  
  
     メソッドの情報ペインにデータを提供する <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>インターフェイスを実装します。  
  
     メソッドのデータヒント\] ウィンドウに表示するかを確認するようにコマンドを適切に処理するテキスト ビューのフィルターをインストールします。  詳細については、「[従来の言語サービスでパラメーター情報](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)」を参照してください。  
  
-   エラーのマーカー  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> インターフェイスを実装します。  
  
     エラーのマーカーを取得します。<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイスを実装し<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> のメソッドを呼び出す作成しエラーのマーカーのオブジェクトの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイスを渡します。  
  
     通常各エラーのマーカーはタスク一覧\] ウィンドウ内の項目を管理します。  
  
-   タスク一覧の項目  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> のインターフェイスを提供するタスク項目のクラスを実装します。  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> の <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> インターフェイスとインターフェイスを使用してタスクのプロバイダー クラスを実装します。  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> インターフェイスを使用してタスクの列挙子のクラスを実装します。  
  
     タスク一覧の <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> のメソッドのタスクのプロバイダーを登録します。  
  
     サービスの GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> の言語サービス プロバイダーを呼び出して <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> のインターフェイスを取得します。  
  
     新しいユーザー要求や更新されたタスクがある場合はタスク項目オブジェクトを作成して <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> のインターフェイス <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> のメソッドを呼び出します。  
  
-   コメント タスク項目  
  
     コメント タスク トークンを取得するために <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>インターフェイスおよび <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> のインターフェイスを使用します。  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> サービスから <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> のインターフェイスを取得します。  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> のメソッドから <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> のインターフェイスを取得します。  
  
     トークン リストの変更をリッスンするに <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>インターフェイスを実装します。  
  
-   アウトライン  
  
     サポートにアウトライン表示の方法はいくつかあります。  たとえば **定義に折りたたむ**  のコマンドをサポートする場合はエディター コントロールのアウトライン領域を提供したりコントロールのクライアント領域をサポートできます。  詳細については、「[方法: レガシ言語サービスでの展開のアウトライン サポートを提供](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)」を参照してください。  
  
-   言語サービスの登録  
  
     言語サービスを登録する方法の詳細については[従来の言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service2.md) と [Vspackage を管理します。](../../extensibility/managing-vspackages.md) を参照してください。  
  
-   状況依存のヘルプ  
  
     次の 1 種類のエディターのコンテキストを用意する :  
  
    -   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> インターフェイスの実装によってテキスト マーカーのコンテキストを提供します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> インターフェイスの実装によってすべてのユーザー コンテキストを指定します。  
  
## 参照  
 [言語サービスを開発します。](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)