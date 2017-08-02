---
title: "方法: 標準のテキストのマーカーを追加 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] 従来の標準的なテキスト マーカー"
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 方法: 標準のテキストのマーカーを追加
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコア エディターで提供される既定のテキスト マーカーの種類の 1 種類を作成するには次の手順を使用します。  
  
### テキスト マーカーを作成するには  
  
1.  で 1 ページまたは次元の座標系を使用するか新しいテキスト マーカーを作成するに <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> の <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> のメソッドまたはメソッドを呼び出します。  
  
     このメソッド呼び出しではマーカーを作成するテキスト マーカーの種類およびスコープ <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイスを指定します。  このメソッドは新しく作成されたテキスト マーカーへのポインターを返します。  マーカーの型は <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> の列挙体から取得されます。  マーカー イベントの通知を受け取るには<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイスを指定します。  
  
    > [!NOTE]
    >  メイン UI スレッドだけがテキスト マーカーを作成します。  コア エディターはテキスト バッファーのコンテンツにテキスト マーカーを作成するために使用するテキスト バッファーはスレッド セーフではありません。  
  
## カスタム コマンドの追加  
 `IVsTextMarkerClient` のインターフェイスを実装しマーカーの参照へのポインターを指定すると複数の方法でマーカーの動作を拡張します。  まずこれはマーカーのヒントを提供しコマンドを実行できるようにします。  また個々のマーカーのイベント通知の受け取りマーカーに対してカスタム コンテキスト メニューを作成します。  マーカーのカスタム コンテキスト メニューにコマンドを追加するには次の手順を使用します。  
  
#### カスタム コンテキスト メニューにコマンドを追加するには  
  
1.  コンテキスト メニューが表示される前に環境は <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> のメソッドを呼び出して影響を受けるテキスト マーカーおよびコンテキスト メニューの項目の数へのポインターを渡します。  
  
     たとえばコンテキスト メニューのブレークポイント固有のコマンドは次のスクリーン ショットに表示されるように  **ブレークポイントの作成**  によって **\*\*\* Remove Breakpoint \*\*\*** が含まれます。  
  
     ![マーカー コンテキスト メニュー](~/docs/extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  パス カスタム コマンドの名前を指定するテキスト。  たとえば**\*\*\* Remove Breakpoint \*\*\*** は環境が既に項目を指定しないカスタム コマンドである場合があります。  コマンドを使用できるようにするまたはオンとオフを切り替えますサポートされているかどうかを渡します。  環境が正しい方法のカスタム コンテキスト メニューのコマンドを表示するためにこの情報を使用します。  
  
3.  環境ではコマンドを実行するコンテキスト メニューから選択されたコマンドのテキスト マーカーと数へのポインターを渡す <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> のメソッド。  
  
     テキスト マーカーのアクションを決定するカスタム コマンドを実行するにはこの呼び出しからこの情報を使用します。  
  
## 参照  
 [レガシ API でテキストのマーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: エラー マーカーを実装します。](../extensibility/how-to-implement-error-markers.md)   
 [方法: カスタム テキスト マーカーを作成](../extensibility/how-to-create-custom-text-markers.md)   
 [方法: テキストのマーカーを使用します。](../extensibility/how-to-use-text-markers.md)