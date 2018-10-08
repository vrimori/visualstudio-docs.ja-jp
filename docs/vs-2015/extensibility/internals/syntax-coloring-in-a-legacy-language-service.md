---
title: 構文の色分け、従来の言語サービス |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8f8838752d619bb87a65c929300de1f03d322c9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540090"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>従来の言語サービスでの構文の色分け表示
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[従来の言語サービスでの構文の色分け表示](https://docs.microsoft.com/visualstudio/extensibility/internals/syntax-coloring-in-a-legacy-language-service)します。  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 言語の要素を特定し、エディターで指定した色で表示するには、色分け表示サービスを使用します。  
  
## <a name="colorizer-model"></a>Colorizer モデル  
 言語サービスの実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>インターフェイスで、エディターで使用します。 この実装は、次の図に示すように、言語サービスから独立したオブジェクトです。  
  
 ![SVC Colorizer グラフィック](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
単純な colorizer モデル  
  
> [!NOTE]
>  構文のサービスを色分け表示は、[全般] から別[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]のテキストを色分けするメカニズムです。 詳細については、一般的な[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]色分けをサポートしているメカニズムを参照してください[を使用してフォントおよび色](../../extensibility/using-fonts-and-colors.md)。  
  
 言語サービスは、colorizer だけでなく、advertising カスタムの配色可能な項目を提供することによって、エディターで使用されるカスタムの配色可能な項目を指定できます。 実装することでこれを行う、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>インターフェイスを実装するオブジェクトと同じで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>インターフェイス。 エディターを呼び出すときにカスタムの配色可能な項目の数を返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>メソッド、およびそのエディターを呼び出すと、個々 のカスタム装飾が可能な項目を返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>メソッド。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>メソッドを実装するオブジェクトを返します、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>インターフェイス。 これを実装する必要があります、言語サービスでは、24 ビットまたは高の色の値をサポートする場合、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>インターフェイスと同じオブジェクトを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>インターフェイス。  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage が言語サービスの Colorizer を使用する方法  
  
1.  VSPackage では、言語サービスには、次の VSPackage を必要とする適切な言語サービスを取得する必要があります。  
  
    1.  実装するオブジェクトを使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>を色分け表示するテキストを取得するインターフェイス。  
  
         テキストが実装するオブジェクトを使用して表示される通常の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>インターフェイス。  
  
    2.  言語サービスの GUID の VSPackage のサービス プロバイダーのクエリを実行して、言語サービスを取得します。 言語サービスは、レジストリでファイル拡張子によって識別されます。  
  
    3.  使用して、言語サービスに関連付ける、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>を呼び出してその<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>メソッド。  
  
2.  VSPackage は、今すぐ入手し、colorizer オブジェクトを使用して、次のようにできます。  
  
    > [!NOTE]
    >  コア エディターを使用して、Vspackage は、言語サービスの colorizer オブジェクトを明示的に取得する必要はありません。 コア エディターのインスタンスは、適切な言語サービスを取得するとすぐには、ここで示すようにすべての色づけのタスクを実行します。  
  
    1.  実装する、言語サービスの colorizer オブジェクトを取得、 `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`、および<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>インターフェイスを呼び出すことによって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>メソッドを言語サービスの<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>オブジェクト。  
  
    2.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>テキストの特定の範囲の colorizer 情報を取得します。  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 色分けされて表示されるテキスト範囲内の各文字のいずれかの値の配列を返します。 値は、コア エディターによって管理される既定の配色可能な項目リストまたは言語サービス自体によって管理されるカスタムの装飾が可能な項目リストのいずれかである装飾が可能な項目のリストへのインデックスです。  
  
    3.  によって返される色づけの情報を使用して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドを選択したテキストを表示します。  
  
> [!NOTE]
>  使用だけでなく、言語サービス colorizer、VSPackage は、汎用的な[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]テキストを色分け表示メカニズム。 このメカニズムの詳細については、次を参照してください。[を使用してフォントおよび色](../../extensibility/using-fonts-and-colors.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [構文の色分け表示の実装](../../extensibility/internals/implementing-syntax-coloring.md)  
 言語サービスの構文の色分け表示と構文をサポートするために実装の色分けする必要があります、言語サービスはどのようなエディターにアクセスする方法について説明します。  
  
 [方法: ビルトインの配色可能な項目の使用](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 言語サービスからの組み込みの配色可能な項目を使用する方法を示します。  
  
 [カスタムの配色可能な項目](../../extensibility/internals/custom-colorable-items.md)  
 カスタムの配色可能な項目を実装する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [フォントと色の使用](../../extensibility/using-fonts-and-colors.md)

