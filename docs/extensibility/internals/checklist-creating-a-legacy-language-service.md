---
title: 'チェックリスト: 従来の言語サービスを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ba21cf1830f389acbcd72d5e10a688f009871b25
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510297"
---
# <a name="checklist-create-a-legacy-language-service"></a>チェックリスト: 従来の言語サービスを作成します。
基本的な手順の言語サービスを作成するために行う必要がありますが、次のチェックリストにまとめたものです、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]のコア エディター。 言語サービスに統合する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグの式エバリュエーターを作成する必要があります。 詳細については、次を参照してください。 [CLR の式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)で、 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)します。  
  
## <a name="steps-to-create-a-language-service"></a>言語サービスを作成する手順  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> インターフェイスを実装します。  
  
    -   VSPackage、実装、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>言語サービスを提供するインターフェイス。  
  
    -   言語サービスを統合開発環境 (IDE) で使用できるように、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>実装します。  
  
2.  実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>主要言語サービス クラスのインターフェイス。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイスは、コア エディターと言語サービスの間の相互作用の開始ポイントです。  
  
### <a name="optional-features"></a>省略可能な機能  
 次の機能は、省略可能な任意の順序で実装することができます。 これらの機能では、言語サービスの機能が向上します。  
  
-   構文の色分け表示  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> インターフェイスを実装します。 このインターフェイスの実装では、パーサーについては、適切な色の情報を返す必要があります。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>メソッドが返す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイス。 実装する必要があるため各テキスト バッファーの個別 colorizer インスタンスが作成された、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイスとは別にします。 詳細については、次を参照してください。[構文の色分け、従来の言語サービス](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)します。  
  
-   コード ウィンドウ  
  
     実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>新しい code ウィンドウが作成されたときの通知を受け取る言語サービスを有効にするインターフェイス。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>メソッドが返す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>インターフェイス。 言語サービスでのコード ウィンドウに特別な UI を追加できます<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>します。 言語サービスは内のテキスト ビュー フィルターの追加など、特別な処理を行うことができますも<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>します。  
  
-   テキスト ビュー フィルター  
  
     言語サービスでの IntelliSense ステートメント入力候補を提供するには、テキスト ビューの処理とそれ以外の場合、コマンドの一部をインターセプトする必要があります。 これらのコマンドを受信するには、次の手順を完了します。  
  
    -   実装<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド チェーンとハンドルのエディター コマンドに参加します。  
  
    -   呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッドを渡します、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>実装します。  
  
    -   呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>メソッドいるため、これらのコマンドに渡す不要になったビューからデタッチするとします。  
   
    処理する必要がありますコマンドは、提供されているサービスによって異なります。 詳細については、次を参照してください。[言語の重要なコマンド サービス フィルター](../../extensibility/internals/important-commands-for-language-service-filters.md)します。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>と同じオブジェクトでインターフェイスを実装する必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。  
  
-   入力候補  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> インターフェイスを実装します。  
  
     ステートメント入力候補のコマンドをサポートして (つまり、 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) を呼び出すと、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>渡すインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>インターフェイス。 詳細については、次を参照してください。[従来の言語サービスで入力候補](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)します。  
  
-   メソッドのヒント  
  
     実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>メソッドのヒント ウィンドウのデータを提供するインターフェイス。  
  
     メソッドのデータ ヒント ウィンドウを表示するタイミングを把握するようにコマンドを適切に処理するために、テキスト ビューのフィルターをインストールします。 詳細については、次を参照してください。[従来の言語サービスのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)します。  
  
-   エラーのマーカー  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> インターフェイスを実装します。  
  
     実装するオブジェクトをマーカーを作成するには、エラー、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>インターフェイスと呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>渡して、メソッド、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>エラー マーカー オブジェクトのインターフェイス。  
  
     通常各エラーのマーカーは、タスク一覧 ウィンドウ内の項目を管理します。  
  
-   タスク一覧の項目  
  
     提供する作業アイテム クラスを実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem>インターフェイス。  
  
     提供するタスク プロバイダー クラスを実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider>インターフェイスと<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>インターフェイス。  
  
     提供するタスク列挙子クラスを実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>インターフェイス。  
  
     タスク一覧のタスク プロバイダーを登録<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>メソッド。  
  
     取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>サービス GUID と、言語サービスのサービス プロバイダーを呼び出すことによってインターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>します。  
  
     作業項目のオブジェクトと呼び出しを作成、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A>メソッドで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>インターフェイスの新しいがある場合またはタスクを更新します。  
  
-   コメント タスク項目  
  
     使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>インターフェイスと<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>コメント タスクのトークンを取得するインターフェイス。  
  
     取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>からインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>サービス。  
  
     取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>からインターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A>メソッド。  
  
     実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>トークン リスト に変更をリッスンするインターフェイス。  
  
-   アウトライン  
  
     アウトライン表示をサポートするためのいくつかのオプションがあります。 たとえば、サポート、**定義に折りたたむ**コマンド、エディター コントロールのアウトライン領域、またはクライアントによって制御された領域をサポートします。 詳細については、次を参照してください。[方法: 従来の言語サービスでのアウトラインの拡張のサポートを提供](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)します。  
  
-   言語サービスの登録  
  
     言語サービスを登録する方法の詳細については、次を参照してください。[従来の言語サービスの登録](../../extensibility/internals/registering-a-legacy-language-service2.md)と[管理 Vspackage](../../extensibility/managing-vspackages.md)します。  
  
-   状況依存のヘルプ  
  
     次の方法のいずれかで、エディターにコンテキストを提供します。  
  
    -   テキスト マーカーのコンテキストを提供するを実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>インターフェイス。  
  
    -   すべてのユーザー コンテキストを提供するを実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>インターフェイス。  
   
## <a name="see-also"></a>関連項目  
 [従来の言語サービスを開発します。](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [CLR の式エバリュエーターを書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)