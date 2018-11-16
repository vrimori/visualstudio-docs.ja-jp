---
title: レガシ API を使用してテキスト レイヤーへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5eb9d92e3604224f3806cf64f2dd8d4529e8d01
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729082"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>レガシ API を使用してテキスト レイヤーへのアクセス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

通常、テキスト レイヤーには、テキストのレイアウトの一部の側面がカプセル化します。 「関数で-、-タイム」レイヤーでは、キャレット (挿入ポイントのテキスト) を含む関数の前後に、テキストを非表示にします。  
  
 バッファーと、ビューのテキスト レイヤーが存在して、ビュー バッファーの内容を表示する方法を変更します。  
  
## <a name="text-layer-information"></a>テキスト レイヤー情報  
 次の一覧のテキスト レイヤーの機能について説明します[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
-   テキスト レイヤー内のテキストは、構文の色分け、およびマーカーで修飾できます。  
  
-   現在、独自のレイヤーを実装することはできません。  
  
-   レイヤーを公開<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>から派生<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>します。 テキスト バッファー自体は、これにより、ビューを基になるレイヤーをポリモーフィック扱うレイヤーとしても実装されます。  
  
-   レイヤーの任意の数は、バッファーとビューの間に可能性があります。 各レイヤーが、その下のレイヤーのみを処理し、ビューが最上位のレイヤーを大きく処理します。 (ビューがいくつかについては、バッファー。)  
  
-   レイヤーは、その下のレイヤーだけに影響を与えます。 超える標準的なイベントが発生した上位層に影響を与えることはできません。  
  
-   エディターで、非表示のテキスト、合成のテキストおよびワード ラップがレイヤーとして実装されます。 レイヤーと直接対話することがなく、非表示と代理のテキストを実装できます。 詳細については、次を参照してください。[従来の言語サービスでのアウトライン](../extensibility/internals/outlining-in-a-legacy-language-service.md)と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>します。  
  
-   各テキスト レイヤーを介して公開される、独自のローカルの座標システムが、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>インターフェイス。 行の折り返しのレイヤーなどが含まれの 2 行、基になるテキスト バッファーに 1 行のみを含めることができます。  
  
-   ビューと通信層を<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>インターフェイス。 このインターフェイスを使用して、バッファーの座標を使用してビューの座標を調整します。  
  
-   レイヤーのいずれかなど、テキストから発信された代理テキスト レイヤーは、ローカルの実装を提供する必要があります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>します。  
  
-   それに<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>、テキスト レイヤーを実装する必要があります<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>でイベントを発生させると、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>インターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [構文のカスタム エディターで色分け表示](../extensibility/syntax-coloring-in-custom-editors.md)   
 [レガシ API を使用したテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [レガシ API を使用するエディター コントロールおよびメニューのカスタマイズ](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)

