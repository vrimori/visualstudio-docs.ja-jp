---
title: "レガシ API を使用してテキストのレイヤーにアクセスする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a5f7a80e8d594f3c9e62ecd2047cc1116948d2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>レガシ API を使用してテキストのレイヤーにアクセスします。
通常、テキストのレイヤーには、テキスト レイアウトの一部の側面がカプセル化します。 「関数での a のタイム」レイヤーでは、キャレット (テキスト挿入ポイント) を含む関数の前後に、テキストを非表示にします。  
  
 バッファーと、ビューのテキストのレイヤーが存在して、ビュー バッファーの内容を表示する方法を変更します。  
  
## <a name="text-layer-information"></a>レイヤーのテキスト情報  
 次の一覧のテキストのレイヤーの動作について説明します[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   レイヤーのテキスト内のテキストは、構文の色分けやマーカーを装飾できます。  
  
-   現在、独自のレイヤーを実装できません。  
  
-   レイヤーを公開<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>から派生した<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>です。 文字列バッファー自体は、基になるレイヤーをポリモーフィックに対処するためのビューを使用する、レイヤーとしても実装されます。  
  
-   複数のレイヤーは、ビューと、バッファー間に可能性があります。 各レイヤーが、下の層のみを処理し、ビューが最上位のレイヤーをほとんど処理します。 (ビューには、バッファーに関する情報。)  
  
-   レイヤーより下にレイヤーだけに影響を与えることができます。 元の標準的なイベントを超える上にあるレイヤーに影響ことはできません。  
  
-   エディターで、非表示テキスト、代理テキスト、およびワード ラップがレイヤーとして実装されます。 レイヤーと直接対話することがなく、統合表示と非テキストを実装できます。 詳細については、次を参照してください。[レガシ言語サービスでのアウトライン](../extensibility/internals/outlining-in-a-legacy-language-service.md)と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>です。  
  
-   各テキスト レイヤーが独自ローカル座標系によって公開される、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>インターフェイスです。 行の折り返しレイヤーなどがあります 2 本の線基になるテキスト バッファーが 1 行のみを含めること。  
  
-   によるレイヤーと通信する、ビュー、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>インターフェイスです。 このインターフェイスを使用して、バッファーの座標を使用してビューの座標を調整します。  
  
-   いずれかのレイヤーのテキストの発生元代理テキスト レイヤーは、ローカルの実装を提供する必要がありますなど<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>です。  
  
-   それに<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>、レイヤーのテキストを実装する必要があります<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>でイベントを発生させると、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>インターフェイスです。  
  
## <a name="see-also"></a>参照  
 [カスタム エディターの構文の色分け](../extensibility/syntax-coloring-in-custom-editors.md)   
 [レガシ API でテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [レガシ API を使用して、エディター コントロールやメニューをカスタマイズします。](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)