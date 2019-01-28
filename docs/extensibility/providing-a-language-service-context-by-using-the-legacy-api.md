---
title: 言語サービスのコンテキストを提供するレガシ API を使用して |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8406d0ca1615ef1f784312827e3a21d0a96b04a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016565"
---
# <a name="provide-a-language-service-context-by-using-the-legacy-api"></a>従来の API を使用して、言語サービスのコンテキストを提供します。
2 つのオプションを使用してユーザー コンテキストを提供する言語サービスがある、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のコア エディター: テキスト マーカーのコンテキストを指定するか、すべてのユーザー コンテキストを提供します。 それぞれの違いが記載されています。  
  
 独自のエディターに接続されている言語サービスにコンテキストを提供する詳細については、次を参照してください。[方法。エディターのコンテキストを提供](../extensibility/how-to-provide-context-for-editors.md)します。  
  
## <a name="provide-text-marker-context-to-the-editor"></a>エディターにテキスト マーカー コンテキストを提供します。  
 テキスト マーカーで示されるコンパイラ エラーのコンテキストを提供する、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターには、実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>インターフェイス。 このシナリオでは、言語サービスは、カーソルがテキスト マーカーに場合にのみにコンテキストを提供します。 これにより、エディターでカーソルをキーワードを提供する、**ダイナミック ヘルプ**属性を持たないウィンドウ。  
  
## <a name="provide-all-user-context-to-the-editor"></a>エディターにすべてのユーザー コンテキストを提供します。  
 言語サービスを作成しを使用しているかどうか、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターを実装することができますし、コア、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>言語サービスのコンテキストを提供するインターフェイス。  
  
 実装の`IVsLanguageContextProvider`、コンテキスト バッグ (コレクション) がコンテキスト バッグを更新するには、エディターにアタッチされています。 ときに、**ダイナミック ヘルプ**ウィンドウの呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>コンテキスト バッグ、アイドル状態時に、このコンテキスト バッグのインターフェイスは、更新プログラム用のエディターをクエリします。 エディターは、エディターを更新する必要があり、コンテキスト バッグへのポインターを渡しますが、言語サービスを通知します。 これは、呼び出すことで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>言語サービスに、エディターからのメソッド。 コンテキスト バッグにポインターを使用して、言語サービスできるようになりました追加および削除の属性とキーワード。 詳細については、「 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 」を参照してください。  
  
 実装する 2 つの方法がある`IVsLanguageContextProvider`:  
  
- コンテキスト バッグにするキーワードします。  
  
   コンテキスト バッグを更新する、エディターが呼び出されると、適切なキーワードと属性を渡すし、戻ります`S_OK`します。 この戻り値には、エディター コンテキスト バッグにカーソルをキーワードを指定するのではなく、キーワードと属性のコンテキストを保持するように指示します。  
  
- カーソル位置にキーワードからキーワードを取得します。  
  
   コンテキスト バッグを更新する、エディターが呼び出されると、適切な属性を渡すし、戻ります`E_FAIL`します。 この戻り値には、エディター、コンテキスト バッグに、属性を保持がカーソル位置にキーワードを使用して、コンテキスト バッグを更新するように指示します。  
  
  次の図は、実装する言語サービスのコンテキストを提供する方法を示します`IVsLanguageContextProvider`します。  
  
  ![LangServiceImplementation2 グラフィック](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  言語サービスのコンテキスト  
  
  図では、ご覧のとおり、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]テキストのコア エディターがコンテキスト バッグがアタッチされています。 このコンテキスト バッグが 3 つの個別のサブコンテキスト バッグを指す: 言語サービスの既定のエディターやテキスト マーカー。 言語サービスとテキスト マーカーのサブコンテキスト バッグを含む属性とキーワード、言語サービスの場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>インターフェイスを実装すると、およびテキスト マーカー場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>インターフェイスを実装します。 これらのインターフェイスのいずれかを実装しない場合、エディターは、キーワードの既定のエディターのサブコンテキスト バッグ内のカーソル位置のコンテキストを提供します。  
  
## <a name="context-guidelines-for-editors-and-designers"></a>エディターとデザイナーのコンテキストのガイドライン  
 デザイナーおよびエディターには、エディターまたはデザイナー ウィンドウの一般的なキーワードを指定する必要があります。 これは、ユーザーが押したときに、デザイナーまたはエディターのジェネリックでは、適切なヘルプ トピックが表示されますのでする**F1**します。 エディター、する必要があります。 さらに、カーソル位置の現在のキーワードを指定または現在の選択に基づく、重要な用語を指定します。 これは、ユーザーが押したときに表示を選択したテキストまたは UI 要素のヘルプ トピックを指していることを確認するため**F1**します。 デザイナーでは、フォーム上のボタンなどのデザイナーで選択した項目のコンテキストを提供します。 エディターとデザイナーする必要がありますもサービスに接続する言語」の説明に従って[レガシ言語サービスの基本情報](../extensibility/internals/legacy-language-service-essentials.md)します。