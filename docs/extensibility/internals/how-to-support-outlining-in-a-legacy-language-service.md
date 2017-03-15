---
title: "方法: レガシ言語サービスでのアウトラインをサポート | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK]、[コマンドの定義に縮小します。"
  - "コマンドの定義に縮小をサポートする言語サービス"
  - "非表示のテキストの定義のコマンドに折りたたみ"
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 方法: レガシ言語サービスでのアウトラインをサポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アウトライン表示は、展開または折りたたむテキストの異なる領域に使用されます。 方法のアウトラインが使用されるさまざまな言語によって別々 に定義できます。 詳細については、「[アウトライン](../../ide/outlining.md)」を参照してください。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 アウトライン機能を実装する新しい方法の詳細については、次を参照してください。 [チュートリアル: アウトラインの中止\]](../../extensibility/walkthrough-outlining.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
 言語サービスの次のコマンドをサポートする方法を次に示します。  
  
### アウトライン表示をサポートするために  
  
1.  実装 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> 言語サービス オブジェクトにします。  
  
2.  呼び出す <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 新しいアウトライン領域を追加する現在のアウトライン セッション オブジェクトにします。  
  
## 信頼性の高いプログラミング  
 ユーザーが選択すると **定義に縮小** 上、 **アウトライン** \] メニューの \[IDE 呼び出し <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> 言語サービスにします。  
  
 このメソッドが呼び出されると、IDE に渡さ、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> \(テキスト バッファーへのポインター\) および <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> \(アウトラインの現在のセッションへのポインター\)。  
  
 呼び出すことができます、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> メソッドでこれらのリージョンを指定することによって、複数のアウトライン領域に対する、 `rgOutlnReg` パラメーター。`rgOutlnReg` パラメーターは、 <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> 構造体。 このプロセスでは、非表示の領域の特定の地域の展開または折りたたむかどうかなどのさまざまな特性を指定することができます。  
  
> [!NOTE]
>  改行文字を非表示に注意してください。 非表示のテキストが、最後に表示される新しい行の最後の文字のままのセクションで、最後の行の文字する最初の行の先頭からに拡張する必要があります。  
  
## 参照  
 [方法: レガシ言語サービスで非表示のテキストをサポート](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [方法: レガシ言語サービスでの展開のアウトライン サポートを提供](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)