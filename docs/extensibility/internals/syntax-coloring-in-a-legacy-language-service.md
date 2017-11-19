---
title: "従来の言語サービスの構文の色分け |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88af397feba9b06eabd73ec23dcf1204ebe755e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>従来の言語サービスの構文の色分け
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]色分けサービスを使用して、言語の要素を識別し、エディターで、指定した色を表示します。  
  
## <a name="colorizer-model"></a>Colorizer モデル  
 言語サービスを実装して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>がエディターを使用しているインターフェイス。 この実装では、次の図に示すように、言語サービスから別のオブジェクトです。  
  
 ![SVC Colorizer グラフィック](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
単純な colorizer モデル  
  
> [!NOTE]
>  構文の色分けをサービスとは別の一般的な[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]メカニズムのテキストが色分けされます。 [全般] の詳細については[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]色分けをサポートするメカニズムを参照してください[を使用するフォントおよび色](../../extensibility/using-fonts-and-colors.md)です。  
  
 言語サービスは、colorizer だけでなく、エディターでカスタムの装飾が可能な項目が用意されている広告によって使用されているカスタムの装飾が可能な項目を指定できます。 実装することによってこれを行う、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>インターフェイスを実装する、同じオブジェクトに対して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイスです。 エディターを呼び出すときは、カスタムの装飾が可能な項目の数を返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>メソッド、およびそのエディターを呼び出すと、個々 のカスタムの装飾が可能な項目を返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>メソッドです。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>メソッドを実装するオブジェクトを返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>インターフェイスです。 これを実装する必要があります、言語サービスは、24 ビット、または高の色の値をサポートする場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスと同じオブジェクトを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>インターフェイスです。  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage が言語サービス Colorizer を使用する方法  
  
1.  VSPackage では、言語サービスには、次の VSPackage を必要とする、適切な言語サービスを取得する必要があります。  
  
    1.  実装するオブジェクトを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>色で表示するテキストを取得するインターフェイスです。  
  
         テキストが通常表示されるを実装するオブジェクトを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>インターフェイスです。  
  
    2.  言語サービス GUID の VSPackage のサービス プロバイダーのクエリを実行して、言語サービスを取得します。 言語サービスは、レジストリでファイル拡張子によって識別されます。  
  
    3.  使用して、言語サービスに関連付ける、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>を呼び出してその<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>メソッドです。  
  
2.  VSPackage は、今すぐ入手し、colorizer オブジェクトは次のように使用できます。  
  
    > [!NOTE]
    >  コア エディターを使用して Vspackage は、言語サービスの colorizer オブジェクトを明示的に取得する必要はありません。 コア エディターのインスタンスは、適切な言語サービスを取得するとすぐには、次に示すすべての色づけタスクを実行します。  
  
    1.  実装する言語サービスの colorizer オブジェクトを取得、 `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>インターフェイスを呼び出すことによって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>メソッドを言語サービスの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>オブジェクト。  
  
    2.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>テキストの特定の範囲の colorizer 情報を取得します。  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>色分け表示されているテキストの範囲内の各文字のいずれかの値の配列を返します。 値は、コア エディターで管理されている既定の装飾が可能な項目リストまたは言語サービス自体によって管理されるカスタムの装飾が可能な項目リストのいずれかである装飾が可能な項目のリストにインデックスです。  
  
    3.  によって返される色付け情報を使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドを選択したテキストを表示します。  
  
> [!NOTE]
>  言語サービス colorizer を使用するだけでなく、VSPackage も使用できます、汎用的な[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]テキストが色分け表示メカニズムです。 このメカニズムの詳細については、次を参照してください。[を使用するフォントおよび色](../../extensibility/using-fonts-and-colors.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [構文の色分け表示の実装](../../extensibility/internals/implementing-syntax-coloring.md)  
 エディターが言語サービスの構文の色分けや構文をサポートするために実装の色分け必要があります言語サービスにアクセスする方法について説明します。  
  
 [方法: ビルトインの配色可能な項目の使用](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 言語サービスからの組み込みの装飾が可能な項目を使用する方法を示します。  
  
 [カスタムの配色可能な項目](../../extensibility/internals/custom-colorable-items.md)  
 カスタムの装飾が可能な項目を実装する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [フォントおよび色を使用します。](../../extensibility/using-fonts-and-colors.md)