---
title: "チェックリスト: 従来の言語サービスを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b09176efca3a8839d5e6a741a1e161ff61cdc7ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="checklist-creating-a-legacy-language-service"></a>チェックリスト: 従来の言語サービスを作成します。
次のチェックリストは、言語サービスを作成するために行う必要がありますの基本的な手順をまとめたもの、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コア エディターです。 言語サービスに統合する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグの式エバリュエーターを作成する必要があります。 詳細については、次を参照してください。 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)で、 [Visual Studio デバッガーの機能拡張](../../extensibility/debugger/visual-studio-debugger-extensibility.md)です。  
  
## <a name="steps-for-creating-a-language-service"></a>言語サービスを作成するための手順  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> インターフェイスを実装します。  
  
    -   VSPackage、実装、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>言語サービスを提供するインターフェイスです。  
  
    -   言語サービスを統合開発環境 (IDE) で使用できるように、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>実装します。  
  
2.  実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>メイン言語サービス クラスのインターフェイスです。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイスは、コア エディターと、言語サービス間の相互作用の開始点です。  
  
### <a name="optional-features"></a>省略可能な機能  
 次の機能は、省略可能な任意の順序で実装することができます。 これらの機能は、言語サービスの機能を拡張します。  
  
-   構文の色分け表示  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> インターフェイスを実装します。 このインターフェイスの実装では、パーサーについては、適切な色の情報を返す必要があります。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>メソッドを返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイスです。 実装する必要がありますので、各テキスト バッファーごとに個別 colorizer インスタンスが作成は、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイスとは別にします。 詳細については、次を参照してください。[レガシ言語サービスで構文の色分け](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)です。  
  
-   コード ウィンドウ  
  
     実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>インターフェイスの新しいコード ウィンドウの作成時に通知を受信する言語サービスを有効にします。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>メソッドを返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>インターフェイスです。 言語サービスのコード ウィンドウに特殊な UI を追加できます<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>です。 言語サービスは、内のテキスト ビュー フィルターの追加などの特殊な処理を行うことも<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>します。  
  
-   テキスト ビュー フィルター  
  
     言語サービスで IntelliSense 入力候補を提供するには、テキスト ビューの処理とそれ以外の場合、コマンドの一部をインターセプトする必要があります。 これらのコマンドをインターセプトするには、次の手順を実行します。  
  
    -   実装<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド チェーンとハンドルのエディター コマンドに含めるようにします。  
  
    -   呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッドを渡します、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>実装します。  
  
    -   呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>メソッドいるため、これらのコマンドに渡す不要になったビューからデタッチするとします。  
  
     処理する必要があるコマンドは、提供されるサービスによって異なります。 詳細については、次を参照してください。[言語サービスのフィルターの重要なコマンド](../../extensibility/internals/important-commands-for-language-service-filters.md)です。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>と同じオブジェクトのインターフェイスを実装する必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスです。  
  
-   入力候補  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> インターフェイスを実装します。  
  
     ステートメント入力候補 コマンドをサポート (つまり、 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) を呼び出すと、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>渡すインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>インターフェイスです。 詳細については、次を参照してください。[レガシ言語サービスで入力候補](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)です。  
  
-   メソッドのヒント  
  
     実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>メソッド ヒント ウィンドウのデータを提供するインターフェイスです。  
  
     メソッドのデータ ヒント ウィンドウを表示するタイミングを知ることは、コマンドを適切に処理するテキスト ビュー フィルターをインストールします。 詳細については、次を参照してください。[レガシ言語サービスでのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)です。  
  
-   エラー マーカー  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> インターフェイスを実装します。  
  
     エラーを実装するマーカーのオブジェクトを作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイスを呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>渡してメソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>エラー マーカー オブジェクトのインターフェイスです。  
  
     通常の各エラー マーカーは、タスク一覧 ウィンドウ内の項目を管理します。  
  
-   タスク一覧の項目  
  
     提供する作業アイテム クラスを実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem>インターフェイスです。  
  
     提供するタスク プロバイダー クラスを実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider>インターフェイスおよび<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>インターフェイスです。  
  
     提供するタスク列挙子クラスを実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>インターフェイスです。  
  
     タスク一覧のタスク プロバイダーを登録<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>メソッドです。  
  
     取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>サービス GUID と、言語サービスのサービス プロバイダーを呼び出すことによってインターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>です。  
  
     作業項目のオブジェクトと呼び出しを作成、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A>メソッドで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>インターフェイスの新しいがある場合またはタスクを更新します。  
  
-   コメント タスク項目  
  
     使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>インターフェイスおよび<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>コメント タスクのトークンを取得するインターフェイスです。  
  
     取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>からインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>サービス。  
  
     取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>からインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A>メソッドです。  
  
     実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>トークン リスト に変更をリッスンするインターフェイスです。  
  
-   アウトライン  
  
     アウトライン表示をサポートするためのいくつかのオプションがあります。 たとえば、サポート、**定義に縮小**コマンドをエディター コントロールのアウトライン領域を指定するかクライアント管理の対象領域をサポートします。 詳細については、次を参照してください。[する方法: レガシ言語サービスでのアウトライン表示の拡張サポートを提供](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)です。  
  
-   言語サービスの登録  
  
     言語サービスを登録する方法の詳細については、次を参照してください。[レガシ言語サービスを登録する](../../extensibility/internals/registering-a-legacy-language-service2.md)と[を管理する Vspackage](../../extensibility/managing-vspackages.md)です。  
  
-   状況依存のヘルプ  
  
     エディターに、次の方法のいずれかでコンテキストを提供します。  
  
    -   実装することによってテキスト マーカーにコンテキストを提供、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>インターフェイスです。  
  
 すべてのユーザー コンテキストを提供するを実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>インターフェイスです。  
  
## <a name="see-also"></a>参照  
 [レガシ言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)