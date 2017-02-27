---
title: "レガシ API を使用してテキスト レイヤーにアクセスします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシー - テキスト レイヤー"
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# レガシ API を使用してテキスト レイヤーにアクセスします。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキスト レイヤーは通常テキスト レイアウト機能をカプセル化します。  たとえば「一」のレイヤーの表示はキャレット \(テキスト挿入ポイント\) を含む関数の前後に短いメッセージを送信します。  
  
 テキスト レイヤーはバッファーとビューの間に存在しビューがバッファーのコンテンツの外観を変更します。  
  
## レイヤーの情報をショートサーキット メッセージを送信します。  
 次の一覧はテキスト レイヤーが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でどのように動作するかを示しています :  
  
-   テキスト レイヤーのテキストは構文の色指定とマーカーで装飾することができます。  
  
-   現在独自のレイヤーを実行できません。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> から派生したレイヤーは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> を公開します。  テキスト バッファー自体は基になるレイヤーを polymorphically 処理を可能にするビューがレイヤーとして実装されます。  
  
-   レイヤーをいくつでもビューとバッファーになる場合があります。  各レイヤーはでレイヤーを取扱いのみビューの最上位の層を主として処理されます。  \(ビューにバッファーに関する情報があります\)。  
  
-   レイヤーはの下にあるレイヤーだけ影響を及ぼすことがあります。  これは標準イベントの発生を越えてその上のレイヤーには影響しません。  
  
-   エディターで非表示のテキスト全体的なテキストとワード ラップがレイヤーとして実装されます。  レイヤーと直接対話に非表示にし全体的なテキストを実行できます。  詳細については、「[従来の言語サービスでのアウトライン](../extensibility/internals/outlining-in-a-legacy-language-service.md)」および「<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>」を参照してください。  
  
-   各テキスト レイヤーは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> のインターフェイスを通じて公開される独自のローカル座標系があります。  行の折り返しのレイヤーは基になるテキスト バッファーが 1 行だけが含まれることもありますが2 行が含まれることがあります。  
  
-   ビューは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> のインターフェイスを通じて層と通信します。  バッファーの座標のビューの座標を解決するにはこのインターフェイスを使用します。  
  
-   テキストが生じる全体的なテキスト レイヤーなどすべてのレイヤーが <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> のローカル実装を提供する必要があります。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> でなくテキスト レイヤーは <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> を実行し<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> のイベントを発生させるインターフェイス。  
  
## 参照  
 [構文のカスタム エディターの色指定](../extensibility/syntax-coloring-in-custom-editors.md)   
 [レガシ API でテキストのマーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [レガシ API を使用して、エディター コントロールとメニューをカスタマイズします。](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)