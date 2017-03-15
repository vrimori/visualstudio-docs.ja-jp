---
title: "レガシ API を使用してテキスト バッファーにアクセスします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシー - テキスト バッファー"
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# レガシ API を使用してテキスト バッファーにアクセスします。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキストはテキスト ストリームやファイルに永続化を管理する必要があります。  バッファーが他の形式を読み書きできますがバッファーを含むすべての通常の通信は Unicode を使用して行われます。  レガシ API ではテキスト バッファーはバッファーの文字の位置を指定するには座標系 1 次元またはいずれかを使用できます。  
  
## 1 および 2 次元の座標系  
 1 次元座標の位置に 147 などのバッファーの最初の文字から文字の位置に基づいています。  バッファーの 1 次元場所にアクセスするために <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> のインターフェイスを使用します。  次元の座標系は行インデックスとの組み合わせに基づいています。  たとえば435 の文字は43 行目の行の最初の文字の右側にある 5 文字です。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> のインターフェイスを使用してバッファーの次元の場所にアクセスする。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> のインターフェイスはテキスト バッファーの <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> オブジェクト \(\) によって実装され相互に `QueryInterface` を使用してアクセスできます。  次の図はこれらのキーとそのほかのインターフェイスを <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 示します。  
  
 ![テキスト バッファー オブジェクト](../extensibility/media/vstextbuffer.png "vsTextBuffer")  
テキスト バッファーのオブジェクト  
  
 どちらの座標系はテキスト バッファーで動作が次元の座標を使用することを最適化します。  1 次元座標系パフォーマンスのオーバーヘッドを作成できます。  したがって次元の座標系を使用します。  
  
 テキスト バッファー 2 番目の責任はファイルに永続化されます。  これを行うにはテキスト バッファーのオブジェクトの実装 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> は永続化に関連するプロジェクト項目およびそのほかのコンポーネントのドキュメント データ オブジェクトのコンポーネント機能します。  詳細については、「[開く、プロジェクト項目を保存します。](../extensibility/internals/opening-and-saving-project-items.md)」を参照してください。  
  
## このセクションの内容  
 [レガシ API を使用してビューの設定を変更します。](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 レガシ API を使用してビューの設定を変更する方法について説明します。  
  
 [グローバル設定を監視するためのテキスト マネージャーの使用](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 テキスト マネージャーがグローバル設定を監視する方法について説明します。  
  
## 参照  
 [コア エディターの内部](../extensibility/inside-the-core-editor.md)