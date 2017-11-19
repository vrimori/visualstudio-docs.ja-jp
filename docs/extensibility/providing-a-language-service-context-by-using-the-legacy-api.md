---
title: "レガシ API を使用して、言語サービス コンテキストを提供する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79f58bf66e5d0a137738d0a2cc90f67a287246dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>レガシ API を使用して、言語サービス コンテキストを提供します。
2 つのオプションを使用してユーザー コンテキストを提供する言語サービスがある、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディター: テキスト マーカーのコンテキストを指定するか、すべてのユーザー コンテキストを提供します。 それぞれの相違点は、ここで説明されています。  
  
 コンテキストを独自のエディターに接続されている言語サービスを提供する方法については、次を参照してください。[する方法: エディターのコンテキストを提供](../extensibility/how-to-provide-context-for-editors.md)です。  
  
## <a name="provide-text-marker-context-to-the-editor"></a>エディターにテキスト マーカー コンテキストを提供します。  
 テキスト マーカーで示されるコンパイラのエラーのコンテキストを提供する、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディター、実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>インターフェイスです。 このシナリオでは、言語サービスは、テキスト マーカー上にカーソルが場合にのみにコンテキストを提供します。 これにより、エディターでカーソルをキーワードを提供する、**ダイナミック ヘルプ**ウィンドウに属性がありません。  
  
## <a name="provide-all-user-context-to-the-editor"></a>エディターにすべてのユーザー コンテキストを提供します。  
 言語サービスを作成しを使用しているかどうか、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターを実装することができますし、コア、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>言語サービスのコンテキストを提供するインターフェイスです。  
  
 実装の`IVsLanguageContextProvider`、コンテキスト バッグ (コレクション) が、エディターでは、コンテキストのバッグの更新を担当に接続されています。 ときに、**ダイナミック ヘルプ**ウィンドウの呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>コンテキスト バッグ、アイドル状態の時にこのコンテキストのバッグのインターフェイスが更新プログラム用のエディターをクエリします。 エディターでは、その、エディターを更新する必要があり、コンテキスト バッグへのポインターを渡しますに言語サービスを通知します。 これは、呼び出すことで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>言語サービスに、エディターからのメソッドです。 コンテキストのバッグにポインターを使用して、言語サービス今すぐを追加したり属性とキーワードを削除します。 詳細については、「<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>」を参照してください。  
  
 実装する 2 つの方法がある`IVsLanguageContextProvider`:  
  
-   コンテキストのバッグにキーワードを指定します。  
  
     コンテキスト バッグを更新する、エディターが呼び出されると、適切なキーワードと属性に渡す、戻ります`S_OK`です。 この戻り値は、エディター コンテキスト バッグにカーソルをキーワードを指定するのではなく、キーワードと属性のコンテキストを保持するように指示します。  
  
-   カーソル位置にキーワードからキーワードを取得します。  
  
     コンテキスト バッグを更新する、エディターが呼び出されると、適切な属性で渡すし、返す`E_FAIL`です。 この戻り値では、エディター コンテキスト バッグ内の属性を保持するが、カーソル位置にキーワードを使用してコンテキスト バッグを更新するように指示します。  
  
 次の図は、言語サービスを実装するコンテキストを提供する方法を示しています`IVsLanguageContextProvider`です。  
  
 ![LangServiceImplementation2 グラフィック](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
言語サービスのコンテキスト  
  
 ダイアグラムでわかるように、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア テキスト エディターが付属しているコンテキスト バッグ。 このコンテキストのバッグが 3 つの独立したサブコンテキスト バッグを指す: 言語サービス、既定のエディター、およびテキスト マーカー。 言語サービスとテキスト マーカー サブコンテキスト バッグを含む属性とキーワードが言語サービスの場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>インターフェイスを実装すると、およびテキスト マーカー場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>インターフェイスを実装します。 これらのインターフェイスのいずれかを実装しない場合、エディターは、キーワードの既定のエディター サブコンテキスト バッグ内のカーソル位置のコンテキストを提供し、します。  
  
## <a name="context-guidelines-for-editors-and-designers"></a>エディターとデザイナーのコンテキストのガイドライン  
 デザイナーおよびエディターには、エディターまたはデザイナー ウィンドウの一般的なキーワードを指定する必要があります。 これは、できるように、ユーザーが f1 キーを押すと、デザイナーまたはエディターのジェネリックでは、適切なヘルプ トピックが表示されます。 エディター必要があります、さらに、カーソル位置の現在のキーワードを指定または現在の選択内容に基づいて、重要な用語を指定します。 これは、ユーザーが f1 キーを押したときに、表示を選択テキストや UI 要素のヘルプ トピックを指していることを確認します。 デザイナーでは、フォーム上のボタンなど、デザイナーで選択した項目のコンテキストを提供します。 エディターやデザイナー必要がありますもサービスへの接続の言語で説明したよう[レガシ言語サービス Essentials](../extensibility/internals/legacy-language-service-essentials.md)です。