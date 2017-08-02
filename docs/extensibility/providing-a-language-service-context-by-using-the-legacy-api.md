---
title: "レガシ API を使用して、言語サービスのコンテキストを提供する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 10221f77e65acfb91c625c2f711b5804b64f827e
ms.lasthandoff: 02/22/2017

---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>レガシ API を使用して、言語サービスのコンテキストを提供します。
2 つのオプションを使用してユーザー コンテキストを提供する言語サービスがある、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディター: テキスト マーカーのコンテキストを指定するか、すべてのユーザー コンテキストを提供します。 それぞれの相違点が記載されています。  
  
 独自のエディターに接続されている言語サービスにコンテキストを提供する方法については、次を参照してください。[方法: エディターのコンテキストを提供](../extensibility/how-to-provide-context-for-editors.md)します。  
  
## <a name="provide-text-marker-context-to-the-editor"></a>エディターにテキスト マーカー コンテキストを提供します。  
 内のテキストのマーカーで示されたコンパイラ エラーのコンテキストを提供する、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターのコア、実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>インターフェイス</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>。 このシナリオでは、言語サービスは、カーソルがテキスト マーカーである場合にのみにコンテキストを提供します。 これにより、キーワードにカーソルの位置を提供するエディター、**ダイナミック ヘルプ**属性を持たないウィンドウです。  
  
## <a name="provide-all-user-context-to-the-editor"></a>エディターにすべてのユーザー コンテキストを提供します。  
 言語サービスを作成してを使用しているかどうか、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターを実装することができますし、コア、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>言語サービスのコンテキストを提供するインターフェイス</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>。  
  
 実装の`IVsLanguageContextProvider`、コンテキスト バッグ (コレクション) がこれをコンテキスト バッグを更新する責任は、エディターに接続されています。 ときに、**ダイナミック ヘルプ**ウィンドウの呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>コンテキスト バッグ、アイドル状態時に、このコンテキスト バッグのインターフェイスを照会、更新プログラムのエディター</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> 。 エディターでは、エディターを更新する必要があり、コンテキスト バッグにポインターを渡すことに、言語サービスを通知します。 これは、呼び出すことで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>言語サービスに、エディターからのメソッドです</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>。 コンテキスト バッグにポインターを使用して、言語サービスできるようになりました追加および削除の属性とキーワード。 詳細については、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>を参照してください。  
  
 実装する&2; つの方法がある`IVsLanguageContextProvider`:  
  
-   コンテキスト バッグにキーワードを指定します。  
  
     コンテキスト バッグを更新する、エディターが呼び出されると、適切なキーワードと属性で渡すし、返される`S_OK`です。 この戻り値では、エディター コンテキスト バッグにカーソル位置にキーワードを指定するのではなく、キーワードと属性のコンテキストを保持するように指示します。  
  
-   カーソル位置に、キーワードの from キーワードを取得します。  
  
     コンテキスト バッグを更新する、エディターが呼び出されると、適切な属性で渡すし、返される`E_FAIL`です。 この戻り値では、エディター コンテキスト バッグ内の属性を保持していますが、カーソルの位置のキーワードを使用してコンテキスト バッグを更新するように指示します。  
  
 次の図を実装する言語サービスのコンテキストを指定する方法を示しています`IVsLanguageContextProvider`します。  
  
 ![LangServiceImplementation2 グラフィック](~/docs/extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
言語サービスのコンテキスト  
  
 ダイアグラムでわかるように、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中核となるテキスト エディターが付属しているコンテキスト バッグです。 このコンテキスト バッグが&3; つの個別のサブコンテキスト バッグを指す: 言語サービス、既定のエディターとテキストのマーカー。 言語サービスとテキストのマーカーのサブコンテキスト バッグを含む属性とキーワード言語サービスの場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>インターフェイスを実装すると、およびテキスト マーカー場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>インターフェイスを実装します</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>。 これらのインターフェイスのいずれかを実装しない場合、エディターは、キーワードの既定のエディターのサブコンテキスト バッグ内のカーソル位置のコンテキストを提供し、します。  
  
## <a name="context-guidelines-for-editors-and-designers"></a>エディターやデザイナーのコンテキストのガイドライン  
 デザイナーとエディターは、エディターまたはデザイナー ウィンドウの全般的なキーワードを指定する必要があります。 これは、するため、f1 キーを押すと、デザイナーまたはエディターのジェネリックでは、適切なヘルプ トピックが表示されます。 エディター、する必要があります。 さらに、カーソル位置の現在のキーワードを指定または現在の選択に基づいて、重要な用語を指定します。 これについては、f1 キーを押したときに、表示を選択したテキストまたは UI 要素についてのヘルプ トピックを指していることを確認するためです。 デザイナーには、フォーム上のボタンなどのデザイナーで選択した項目のコンテキストが用意されています。 エディターやデザイナー必要がありますもサービスへの接続の言語」の説明に従って[レガシ言語サービス Essentials](../extensibility/internals/legacy-language-service-essentials.md)します。
