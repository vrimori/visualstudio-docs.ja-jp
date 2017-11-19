---
title: "レガシ言語サービス インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 925b504d8cba4813631d4f8ba6f7dbd9750f5eae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-interfaces"></a>レガシ言語サービス インターフェイス
特定のプログラミング言語のことができますがある言語サービスのインスタンスを 1 つだけ、一度にです。 ただし、1 つの言語サービスは、1 つ以上のエディターを使用できます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]特定のエディターで、言語サービスは関連付けません。 そのため、言語サービス操作を要求するときに、パラメーターとして適切なエディターを識別する必要があります。  
  
## <a name="common-interfaces-associated-with-language-services"></a>言語サービスに関連付けられている共通のインターフェイス  
 エディターを呼び出すことによって、言語サービスを取得<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>を適切な VSPackage にします。 ID (SID) がこの呼び出しで渡されて、サービスでは、要求されている言語サービスを識別します。  
  
 別のクラスの数にかかわらず、コア言語サービス インターフェイスを実装できます。 ただし、一般的な方法は、1 つのクラスで、次のインターフェイスを実装するのには。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (省略可能)  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>言語のすべてのサービスでインターフェイスを実装する必要があります。 言語、言語サービスと、colorizer を取得する方法に関連付けられているファイル名拡張子のローカライズされた名前など、言語サービスに関する情報を提供します。  
  
## <a name="additional-language-service-interfaces"></a>追加の言語サービス インターフェイス  
 言語サービスとその他のインターフェイスを提供できます。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]これらのインターフェイスのテキスト バッファーのインスタンスごとに個別のインスタンスを要求します。 そのため、独自のオブジェクトの各インターフェイスを実装する必要があります。 テキスト バッファーのインスタンスごとに 1 つのインスタンスを必要とするインターフェイスを次の表に示します。  
  
|インターフェイス|説明|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|ドロップダウン バーなどのコード ウィンドウの修飾を管理します。 使用してこのインターフェイスを取得することができます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>メソッドです。 1 つを使用する必要がある<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>コード ウィンドウごとです。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|言語のキーワードと区切り記号の色を付けます。 使用してこのインターフェイスを取得することができます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>メソッドです。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>描画時に呼び出されます。 内の計算負荷の高い処理を回避する<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>パフォーマンスが低下する可能性がありますか。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense パラメーター ヒントを提供します。 言語サービスは、そのメソッドのデータを示す文字にする必要がありますを認識すると、かっこなど、表示が呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>にテキストを通知する方法を表示する言語サービスがパラメーター ヒントを表示する準備ができます。 テキスト ビューし、コールバックによって言語サービスのメソッドを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>ツールヒントを表示する、必要な情報を取得するインターフェイスです。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense 入力候補を提供します。 呼び出しが言語サービスの入力候補一覧を表示する準備ができたら、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>テキスト ビューでのメソッドです。 テキスト ビュー、コールバックによって言語サービスにメソッドを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>オブジェクト。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|コマンド ハンドラーを使用して、テキスト ビューの変更が可能です。 実装するクラス、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>インターフェイスを実装する必要がありますも、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスです。 テキスト ビューを取得、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>オブジェクト クエリを実行して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>に渡されるオブジェクト、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッドです。 1 つあります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>各ビューのオブジェクト。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|ユーザーがコード ウィンドウに入力するコマンドを受け取ります。 出力を監視、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>カスタム完了の情報を提供し、変更の表示の実装<br /><br /> 渡す、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>呼び出しのテキスト ビュー オブジェクト<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>です。|  
  
## <a name="see-also"></a>関連項目  
 [レガシ言語サービスの開発](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [チェック リスト: 従来の言語サービスの作成](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)